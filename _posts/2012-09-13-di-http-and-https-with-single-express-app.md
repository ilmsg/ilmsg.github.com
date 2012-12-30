---
layout: post
title: "DI http and https with single express app"
description: ""
category: 
tags: []
---
{% include JB/setup %}

โค้ดต้นแบบ

	var express = require( 'express' ) , 
	https = require("https") , 
	fs = require( 'fs' );  
	
	var app = express.createServer(); // init routes and middlewares 
	app.listen( 80 );  
	var privateKey = fs.readFileSync( 'privatekey.pem' ).toString(); 
	var certificate = fs.readFileSync( 'certificate.pem' ).toString(); 
	var options = {key: privateKey, cert: certificate}; 
	
	https.createServer( options, function(req,res){ 
		app.handle( req, res ); 
	}).listen( 443 );

แนวคิดการทำ DI

	var register = function (app) { // config middleware 
		app.configure({  });  // config routes 
		app.get(...); 
	};  
	
	var http = express.createServer(); 
	register(http); 
	http.listen(80);
	
	var https = express.createServer({ key: /* https properties */ }); 
	register(https);
	https.listen(443);


ตัวอย่างที่ใชงานจริง

	fs = require('fs');
	https = require('https');
	http = require('http');
	express = require('express');
	
	keys_dir = 'keys/';
	server_options = { 
		key : fs.readFileSync(keys_dir + 'privatekey.pem'), 
		ca : fs.readFileSync(keys_dir + 'certrequest.csr'), 
		cert : fs.readFileSync(keys_dir + 'certificate.pem') 
	}

	app = express();
	app.configure -> 
		app.use express.cookieParser() 
		app.use express.bodyParser() 
		app.use express.methodOverride() 
		app.use express.session( { secret: '' } ) 
		app.use app.router

	app.configure 'development', -> 
		app.use express.static(__dirname + '/public') 
		app.use express.errorHandler({dumpExceptions: true, showStack:true}) 
		app.set('view options', { pretty: true })  
		app.get '/', (req, res) -> res.send("Hello World!");
	
	https.createServer(server_options,app).listen(7000);
	http.createServer(app).listen(8000);
	
	
