---
layout: post
title: "php download file"
description: ""
category: 
tags: [php]
---
{% include JB/setup %}

res_file.txt

	http://www.mysite.com/file1.txt
	http://www.mysite.com/file2.txt
	http://www.mysite.com/file3.txt


download.php

	$url_file = "res_file.txt"; 
	$objFopen = fopen( $url_file, 'r'); 
	while (!feof($objFopen)) { 
		$file = fgets($objFopen, 4096); 
		$target_file = trim($file);  
		$ch = curl_init($target_file); 
		$fp = fopen('download_file/'.$n, 'wb'); 
		curl_setopt($ch, CURLOPT_FILE, $fp); 
		curl_setopt($ch, CURLOPT_HEADER, 0); 
		curl_exec($ch); 
		curl_close($ch); 
		fclose($fp); 
		sleep(3);
	}
	fclose($objFopen); 
	

