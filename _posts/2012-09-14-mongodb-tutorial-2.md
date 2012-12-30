---
layout: post
title: "mongodb tutorial 2"
description: ""
category: tutorial
tags: [mongodb, php]
---
{% include JB/setup %}

### Connection

	$MONGO_URL = 'mongodb://localhost:27017/app_mongo';
	try{
		$mongo = new Mongo( $MONGO_URL );   
	}catch(MongoConnectionException $e){
		die('Failed to connect to database ' . $e->getMessage() );
	}

การดัก Expection ของ Connection ใช้ชื่อ MongoConnectionException


### Cursor

	try{
		$collection = $mongo->app_mongo->e02;
		$cursor = $collection->find();
	}catch (MongoCursorException $e) {
		die('error message: '.$e->getMessage() );
	}

การดัก Expection ของ cursor ใช้ชื่อ MongoCursorException


### List Database ใน MongoDB

	$MONGO_URL = 'mongodb://localhost:27017/app_mongo';
	try{
		$mongo = new Mongo( $MONGO_URL );
		$database = $mongo->listDBs();
			print "<pre>";
		print_r( $database );
		print "</pre>";
	}catch(MongoConnectionException $e){
		die('Failed to connect to database ' . $e->getMessage() );
	}



![List Database ใน MongoDB](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/mongodb-tutorial-2.png)



















