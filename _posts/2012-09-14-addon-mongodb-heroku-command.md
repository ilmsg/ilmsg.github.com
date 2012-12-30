---
layout: post
title: "addon ฐานข้อมูล MongoDB โดยใช้ Heroku Command"
description: ""
category: howto
tags: [mongodb, heroku]
---
{% include JB/setup %}

ลองเช็ค Config ดูก่อนว่าได้ addon mongodb มารึยัง

	$ heroku config
	FACEBOOK_APP_ID => xxxxxxxxxxxxxxx
	FACEBOOK_SECRET => xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

ถ้ายังก็จัดการ คำสั่ง addon mongodb แบบฟรี 5 MB

	$ heroku addons:add mongohq:free
	-----> Adding mongohq:free to [App Name]... done, v6 (free)

เช็ค Config ดูอีกที จะเห็นว่า มี MONGOHQ_URL โผล่ขึ้นมาให้ใช้ได้

	$ heroku config
	FACEBOOK_APP_ID => xxxxxxxxxxxxxxx
	FACEBOOK_SECRET => xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
	MONGOHQ_URL     => mongodb://[user]:[password]@flame.mongohq.com:27108/appXXXXXXX



