---
layout: post
title: "สร้างและใช้งาน module"
description: "การสร้าง module และการเรียกใช้งานในแบบต่างๆ"
category: node.js
tags: [node.js, tutorial]
---
{% include JB/setup %}

### การใช้งาน

ไพล์ `bird.js`

	exports.say = function(word){
		console.log(word);
	};


ไพล์ `use_bird.js`

	var mybird = require('./bird');
	mybird.say('hi ! all');


เรียกใช้แบบคำสั่งเดียว

	require('./bird').say('แมง บ่ะ ดี กิ๋น');
	
