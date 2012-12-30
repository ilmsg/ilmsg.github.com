---
layout: post
title: "เขียน node.js ให้ run ไพล์ .php"
description: "เขียน node.js ให้ run ไพล์ .php"
category: tutorial
tags: [node.js, php]
---
{% include JB/setup %}

![รายชื่อไพล์](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/run-php-with-node-js-server.png)

ใช้ run ไพล์ php อย่างเดียวเลยนะคับ ไม่ได้มีตัว `php.ini` โหลด extension อะไรขึ้นมาเลย ไปจิ้กไพล์ `php.exe` กับ `php5ts.dll` แถวๆ XAMPP 

ไพล์ `app.js`

	var exec = require("child_process").exec;
	var http = require('http');
	
	exec("php info.php", function (error, stdout, stderr) {
		console.log(stdout);
	});
	
ไพล์ `info.php`

	<?php phpinfo(); ?>


