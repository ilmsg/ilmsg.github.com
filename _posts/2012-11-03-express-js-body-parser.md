---
layout: post
title: "การใช้ Express กับ bodyParser"
description: ""
category: node.js
tags: []
---
{% include JB/setup %}

ต้องใช้ `app.use(app.router);` ไว้บน `app.use(express.bodyParser());` นะ

	app.use(app.router); // Contains your /test/ route
	app.use(express.bodyParser());
	app.use(express.cookieParser());
	app.use('/min',express.static('../min'));
	app.use('/js',express.static('../js'));
	app.use('/css',express.static('../css'));
	app.use('/img',express.static('../img'));
	
อ้างอิง : <http://stackoverflow.com/questions/7451966/express-js-body-parser-not-working>