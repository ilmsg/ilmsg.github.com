---
layout: post
title: "save image from url"
description: ""
category: 
tags: [php, curl]
---
{% include JB/setup %}


### set allow_url_fopen to true:

	$url = 'http://example.com/image.php';
	$img = '/my/folder/flower.gif';
	file_put_contents($img, file_get_contents($url));


### Else use cURL:

	$ch = curl_init('http://example.com/image.php');
	$fp = fopen('/my/folder/flower.gif', 'wb');
	curl_setopt($ch, CURLOPT_FILE, $fp);
	curl_setopt($ch, CURLOPT_HEADER, 0);
	curl_exec($ch);
	curl_close($ch);
	fclose($fp);

### grab_image function

	function grab_image($url,$saveto){
		$ch = curl_init ($url);
		curl_setopt($ch, CURLOPT_HEADER, 0);
		curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
		curl_setopt($ch, CURLOPT_BINARYTRANSFER,1);
		$raw=curl_exec($ch);
		curl_close ($ch);
		if(file_exists($saveto)){
			unlink($saveto);
		}
		$fp = fopen($saveto,'x');
		fwrite($fp, $raw);
		fclose($fp);
	}
