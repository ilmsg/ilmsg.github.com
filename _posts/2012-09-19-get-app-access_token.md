---
layout: post
title: "get app access_token"
description: ""
category: howto
tags: [app facebook, php, auth]
---
{% include JB/setup %}

#### url สำหรับ auth เพื่อรับค่า app access_token กลับมา

	https://graph.facebook.com/oauth/access_token?client_id=yyyyyyyyyyyyyyy&client_secret=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx&grant_type=client_credentials

#### app access_tokey ที่ได้กลับมา หน้าตาจะประมาณนี้
	
	access_token=yyyyyyyyyyyyyyy|0UH0uTltlfd1Dl-d-kDUutnBEOo

#### source code php 

	$app_id = 'yyyyyyyyyyyyyyy';
	$app_secret = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx';
	$targetUrl = 'https://graph.facebook.com/oauth/access_token?client_id='. $app_id . '&client_secret='. $app_secret .'&grant_type=client_credentials';
	$response = file_get_content($targetUrl);

ทำผ่านทาง fire_get_content 
