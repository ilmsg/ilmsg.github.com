---
layout: post
title: "Real Mission tlab_auto_login.js"
description: ""
category: 
tags: [javascript, chrome extension]
---
{% include JB/setup %}

ทำในไว้ใน chrome extension

	var d = document;
	var url = d.URL;
	var isTargetUrl = url.indexOf('192.168.1.1:8000');
	
	if(isTargetUrl > 0){
	
		setTimeout(function(){
			var r = d.getElementsByTagName('input')[2].value;
			if(r == "/"){
				d.getElementsByTagName('input')[2].value = 'http://www.google.co.th';
			}
			d.getElementsByTagName('input')[0].value = '';
			d.getElementsByTagName('input')[1].value = '';
			d.getElementsByTagName('input')[3].type = "hidden";
			d.getElementsByTagName('form')[0].action = "http://192.168.1.1:8000/index.php";
			d.forms[0].submit();
		},500);
	}