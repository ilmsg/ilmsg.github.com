---
layout: post
title: "get all file in folder app 4shared"
description: ""
category: 
tags: []
---
{% include JB/setup %}

แสดงข้อมูลไพล์ในโพลเดอร์ที่เราต้องการ หมายถึงว่าเราจะมี FolderId ของเราเตรียมไว้แล้ว

<http://www.4shared.com/developer/docs/items/#getAllItems>

getItemsPartial

	AccountItem[] getItemsPartial(java.lang.String login,
	 java.lang.String password,
	 long dirId,
	 int startIndex,
	 int count)
	
Get specified count folders' items ordered by name, folders first starting from startIndex.

#### Source Code

	$user_login = "eak.netpanya@ilmsg.com";
	$user_password = "XXXXXXXXXXXXXXX";
	$folder_id = 273227370;
	$start = 0;
	$end = 20;
	 
	$client = new SoapClient("https://api.4shared.com/jax3/DesktopApp?wsdl", array(
		"cache_wsdl" => WSDL_CACHE_DISK,
		"trace" => 1,
		"exceptions" => 0
		)
	);
	 
	print_r( $client->getItemsPartial($user_login, $user_password, $folder_id, $start, $end) );


ตรง $start เป็นตัวเริ่มต้น ก็เริ่มจาก 0 กันเลย และ $end เราอาจจะต้องการจำนวนของไพล์ทั้งหมดของโฟลเดอร์นั้นๆ ก็ใช้แบบนี้


	$client->getItemsCount($user_login, $user_password, $folder_id) );

![get-all-file-in-folder](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/get-all-file-in-folder.png)