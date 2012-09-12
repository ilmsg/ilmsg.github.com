---
layout: post
title: "socket.io with express 3.x"
description: ""
category: 
tags: []
---
{% include JB/setup %}

ตัวอย่างโค้ดอย่างง่าย

	var app = express();
	var server = app.listen(3000);
	var io = require('socket.io').listen(server);

ตอนเอาไปใช้จริงก็แบบนี้เลย  แบบเดิมเป็นแบบนี้

	http.createServer(app).listen(app.get('port'), function(){
		console.log("Express server listening on port " + app.get('port')); 
	});

แก้ไขใหม่เป็นแบบนี้

	var server = http.createServer(app).listen(app.get('port'), function(){ 
		console.log("Express server listening on port " + app.get('port'));
	});
	var io = require('socket.io').listen(server);




