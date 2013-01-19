---
layout: post
title: "mysql session store node.js"
description: "express กับการใช้งาน session กับ mysql"
category: howto
tags: [node.js, session, mysql]
---
{% include JB/setup %}

0. ติดตั้ง connect-mysql-session เข้ามาใช้กันก่อน

	npm install connect-mysql-session 

1. require ตัว connect-mysql-session เข้ามาใช้กับ express ก่อน

	var express = require('express');
	var MySQLSessionStore = require('connect-mysql-session')(express);

2. เพิ่มใน app.configure ในส่วนของ middlewear 
	app.configure(function(){
	  ....
	  app.use(express.session({
	    store: new MySQLSessionStore("database_name", "database_user", "database_password", {
	        // options...
	    }),
	    secret: "keyboard cat"
	  }));
	  app.use(express.session());
	  ....
	});

3. ในส่วนของการใช้งาน session 

	app.get('/', function(req, res){
		req.session.username = 'user';
		res.render('index', { title: 'Express' });
	};

4. ลองไปเปิดเช็คในฐานข้อมูลดู จะเห็นว่ามีข้อมูล username เก็บใน mysql databse ของเราแล้ว
