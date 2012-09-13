---
layout: post
title: "การใช้งาน http (auth app facebook) node.js"
description: ""
category: howto
tags: [app facebook, auth]
---
{% include JB/setup %}

ตัวอย่างการใช้ http ทำ auth app_access_token ของ app facebook

	var args = 'grant_type=client_credentials&client_id=XXXXXXXXXXXXXXX&client_secret=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'; 
	var options = { 
		host: 'graph.facebook.com', 
		port: 443, 
		path: '/oauth/access_token?' + args, 
		method: 'POST' 
	};  
	var http = require('https'); 
	http.request(options, function(res) { 
		console.log('\nSTATUS: ' + res.statusCode); 
		console.log('\nHEADERS: ' + JSON.stringify(res.headers)); 
		res.setEncoding('utf8'); 
		res.on('data', function (chunk) { 
			console.log('\nBODY: ' + chunk); 
		}); 
	}).end();

