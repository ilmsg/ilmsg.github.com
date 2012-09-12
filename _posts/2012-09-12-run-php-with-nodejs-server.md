---
layout: post
title: "run php with node.js server"
description: ""
category: 
tags: []
---
{% include JB/setup %}

![my list file](./_upload/run-php-with-node-js-server.png)


![list file](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/run-php-with-node-js-server.png)

app.js

	var exec = require("child_process").exec;
	var http = require('http');
	
	exec("php info.php", function (error, stdout, stderr) {
		console.log(stdout);
	});
	
info.php

	<?php phpinfo(); ?>


