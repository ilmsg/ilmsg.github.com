---
layout: post
title: "app mediafire getPreviewLink"
description: ""
category: 
tags: []
---
{% include JB/setup %}

การใช้ getPreviewLink นั้น จะทำได้กับไพล์ที่เป็น preview image หรือ flv preview สำหรับไพล์ที่เป็น video เท่านั้น ถ้าเป็นไพล์ประเภท .rar จะไม่มี preview ให้ดู ถ้าใช้คำสั่งนี้กับไพล์ที่ไม่สามารถ preview ได้จะ error ทันที ฉะนั้นก่อนการใช้คำสั่งนี้ ต้องตรวจสอบประเภพทของไพล์นั้นๆก่อน

[http://www.4shared.com/developer/docs/file/#getPreviewLink](http://www.4shared.com/developer/docs/file/#getPreviewLink)

#### getPreviewLink

	java.lang.String getPreviewLink(java.lang.String login,
	 java.lang.String password,
	 long fileId)

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
	 
	print_r( $client->getPreviewLink($user_login, $user_password, $file_id) );


กรณีนี้ไพล์เป็นรูปภาพ ผลลัพธ์ที่ได้ออกมาจะเป็น url ของรูปภาพ

	http://dc604.4shared.com/img/5rRXBOHX/tlab_bot_plugin.png


![tlab_bot_plugin.png](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/tlab_bot_plugin.png)

จะเห็นว่ารูปเล็กมาก เป็นรูปสำหรับ Preview เท่านั้นไม่ใช่รูปขนาดจริงของไพล์

