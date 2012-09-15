---
layout: post
title: "app 4shared getAllFolder"
description: ""
category: tutorial
tags: [app 4Shared, php]
---
{% include JB/setup %}

แสดงข้อมูลโพลเดอร์ทั้งหมดของบัญชีเรา

[http://www.4shared.com/developer/docs/folder/#getAllFolders](http://www.4shared.com/developer/docs/folder/#getAllFolders)


#### getAllFolders

	public com.pmstation.shared.soap.api.AccountItem[] getAllFolders(java.lang.String login,
	 java.lang.String password)
	
Returns all of the folders in user's root directory.


#### Parameters:

	login - user login
	password - user password
	
#### Returns:

	Array of info records about user's root folder subfolders


####Source Code 

	$user_login = "eak.netpanya@ilmsg.com"; 
	$user_password = "XXXXXXXXXXXXXXX";  
	$client = new SoapClient("https://api.4shared.com/jax3/DesktopApp?wsdl", array( 
		"cache_wsdl" => WSDL_CACHE_DISK, 
		"trace" => 1, 
		"exceptions" => 0 ) );  
	print_r( $client->getAllFolders($user_login, $user_password) );


![app-4shared-getallfolder](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/app-4shared-getallfolder.png)

