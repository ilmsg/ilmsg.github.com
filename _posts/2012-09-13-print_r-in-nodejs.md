---
layout: post
title: "print array, object in node.js"
description: ""
category: 
tags: []
---
{% include JB/setup %}

ใน php จะใช้คำสั่ง 
	
	print_r($object);
	
ใน javascript จะใช้
	
	console.log(object);
	
ข้อมูลที่เป็น object หรือว่า json มันไม่ยอมออก มันบอกแค่ว่า `[object Object]`

	console.log("%j", object);

มีคนแนะนำมาว่า ให้ %j แสดงข้อมูลแบบ json ไปเลย

ไปเจออันนี้ OK กว่ากันเยอะ

	var util = require('util');
	console.log( util.inspect(object) );

รายละเอียดการใช้ util.inspect แบบเต็มๆ
	
[http://docs.nodejitsu.com/articles/getting-started/how-to-use-util-inspect](http://docs.nodejitsu.com/articles/getting-started/how-to-use-util-inspect)
	
	