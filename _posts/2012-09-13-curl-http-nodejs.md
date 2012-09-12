---
layout: post
title: "curl http node.js"
description: ""
category: 
tags: []
---
{% include JB/setup %}

var args = 'grant_type=client_credentials&client_id=XXXXXXXXXXXXXXX&client_secret=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'; 
var options = { host: 'graph.facebook.com', port: 443, path: '/oauth/access_token?' + args, method: 'POST' };  
var http = require('https'); 
http.request(options, function(res) { 
	console.log('\nSTATUS: ' + res.statusCode); 
	console.log('\nHEADERS: ' + JSON.stringify(res.headers)); 
	res.setEncoding('utf8'); 
	res.on('data', function (chunk) { 
		console.log('\nBODY: ' + chunk); 
	}); 
}).end();

