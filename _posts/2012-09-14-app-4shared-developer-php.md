---
layout: post
title: "พัฒนา App 4Shared ด้วยภาษา PHP"
description: ""
category: tutorial
tags: [app 4Shared, php]
---
{% include JB/setup %}

Sourc Code ตัวอย่างที่เขียนด้วย PHP ทำงานผ่านตัว SoapClient
[http://www.4shared.com/developer/docs/samples/#PHP](http://www.4shared.com/developer/docs/samples/#PHP)

การ Upload ไพล์

	<!DOCTYPE html>
	<html xmlns="http://www.w3.org/1999/xhtml">
	 
	<head>
	<meta content="text/html; charset=utf-8" http-equiv="Content-Type" />
	<title>Upload</title>
	</head>
	 
	<body>
	 
	 <form action="<?echo $PHP_SELF;?>" method="post" enctype="multipart/form-data">
	 <input name="myfile" type="file" /><br />
	 <input name="submit" type="submit" value="Upload to 4shared" />
	 </form>
	 
	 <?
	 //User credentials on 4shared
	 $user_login = "a5642551@nepwk.com";
	 $user_password = "123123";
	 
	 if (isset ($_POST['submit'])) {
	 
	 $fileLocal = $_FILES['myfile']['tmp_name']; // This is the entire file that was uploaded to a temp location.
	 $fileName = $_FILES['myfile']['name'];
	 $fileSize = $_FILES['myfile']['size'];
	 
	 $client = new SoapClient("https://api.4shared.com/jax3/DesktopApp?wsdl", array(
	  "cache_wsdl" => WSDL_CACHE_DISK,
	  "trace" => 1,
	  "exceptions" => 0
	  )
	  );
	 
	 $client->yourFunction();
	 
	 //Let's look if we have enough free space in user's account
	 $freeSpace = $client->getFreeSpace($user_login, $user_password);
	 
	 //Check upload limit for user
	 $maxSize = $client->getMaxFileSize($user_login, $user_password);
	 
	 if ($fileSize > $maxSize) die("<b>Error: Your file is too big</b>");
	 else if ($fileSize > $freeSpace) die("<b>Error: Not enough space in account</b>");
	 
	 //Get Session Key for file upload. -1 means uploading file into root folder
	 $session = $client->createUploadSessionKey($user_login, $user_password, -1);
	 
	 //Get datacenter
	 $datacenter = $client->getNewFileDataCenter($user_login, $user_password, -1);
	 if ($datacenter <= 0) die("<b>Error: Something went wrong</b>");
	 
	 //Get Upload Url
	 $uploadUrl = $client->getUploadFormUrl($datacenter, $session);
	 
	 //Reserve fileId for our upload
	 $fileId = $client->uploadStartFile($user_login, $user_password, -1, $fileName, $fileSize);
	 
	 //Send file and params via post request
	 
	  $post_params = array(
	  'resumableFileId' => $fileId,
	  'resumableFirstByte' => 0,
	  'FilePart' => '@'.$fileLocal
	  );
	 
	  $ch = curl_init();
	  curl_setopt($ch, CURLOPT_URL, $uploadUrl);
	  curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
	  curl_setopt($ch, CURLOPT_POST, true);
	  curl_setopt($ch, CURLOPT_POSTFIELDS, $post_params);
	  $req = curl_exec($ch);
	  curl_close($ch);
	 
	 $finish = $client->uploadFinishFile($user_login, $user_password, $fileId, md5_file($fileLocal));
	 
	 if($finish == "") {echo "File uploaded";}
	 
	 }
	 ?>
	 
	</body>
	</html>



