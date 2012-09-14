---
layout: post
title: "app 4Shared getFileDownloadLink"
description: ""
category: tutorial
tags: [app 4Shared, php]
---
{% include JB/setup %}



การหา Lik สำหรับ Download File โดยใช้ FileID เป็นตัวหา

[http://www.4shared.com/developer/docs/download/#getFileDownloadLink](http://www.4shared.com/developer/docs/download/#getFileDownloadLink)

getFileDownloadLink

	public java.lang.String getFileDownloadLink(java.lang.String login,
	 java.lang.String password,
	 long fileID)
	
Returns download link for user owned file.


#####Parameters:

- login – user login
- password – user password
- fileID – id of file to be downloaded

Returns:

Download link or empty string if some errors occurs.



##### Source Code

	$user_login = "eak.netpanya@ilmsg.com";
	$user_password = "XXXXXXXXXXXXXXX";
	$file_id = 1437396575;
	 
	$client = new SoapClient("https://api.4shared.com/jax3/DesktopApp?wsdl", array(
		"cache_wsdl" => WSDL_CACHE_DISK,
		"trace" => 1,
		"exceptions" => 0
		)
	);
 
	print_r( $client->getFileDownloadLink($user_login, $user_password, $file_id) );


ผลลัพธ์ที่ได้กลับมาจะเป็น url

	http://www.4shared.com/photo/5rRXBOHX/tlab_bot_plugin.html

เอา url ที่ได้มาเปิดกับ web browser ก็จะออกมาหน้าแบบนี้ ซึ่งเป็นหน้าดาวน์โหลดแบบปกติของ 4Shared เลย

![getFileDownloadLink](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/app-mediafire-getfiledownloadlink.png)

