---
layout: post
title: "การใช้ request ของ play framework"
description: "การใช้ request สำหรับดึงค่า host, acceptLanguage ของ play framework"
category: howto
tags: [java, play framework]
---
{% include JB/setup %}

> หา hostname ของ เว็บ

	String strHostName = request().host();
	String strHostNameArge[] = strHostName.split("\\.");

> ใน split ของ java เขียนได้อีกแบบ
	
	String strHostNameArge[] = strHostName.split("[.]");

> เอาไว้เช็คดูว่า strHostNameArge[0] มันเป็น sub domain หรือว่า domain 
> อีกตัวหนึ่งเป็น accept language ของ browser 

	List<Lang> lang = request().acceptLanguages();

> ได้มาเป็น List ของ Lang นะครับ import ตามด้วย

	import play.i18n.Lang;
	import java.util.*;


[api/2.0.4/java/play/i18n](http://www.playframework.org/documentation/api/2.0.4/java/play/i18n/package-summary.html "i18n")

[api/2.0.4/java](http://www.playframework.org/documentation/api/2.0.4/java/index.html)