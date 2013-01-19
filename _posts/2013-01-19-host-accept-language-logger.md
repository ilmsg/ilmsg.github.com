---
layout: post
title: "การใช้ host, accept language, logger ของ play framework"
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

> เอาไว้เช็คดูว่า `strHostNameArge[0]` มันเป็น subdomain หรือว่า domain 

> อีกตัวหนึ่งเป็น accept language ของ browser 

	List<Lang> lang = request().acceptLanguages();

> เอาตัวแรกออกมาดู

	String strCode = lang.get(0).code() 
	String strLanguage = lang.get(0).language();

> เรียกออกมาทั้งหมดเลย

	for(int i = 0; i <= lang.size() - 1; i++){
		Logger.info( "code : " + lang.get(i).code() + " = " + lang.get(i).language() );
	}

> ได้มาเป็น List ของ Lang นะครับ import ตามด้วย

	import play.i18n.Lang;
	import java.util.*;

มีอีกตัวนึง `Logger` เอาไว้แสดงค่าใน console นึกถึง console.log() ของ node.js เลย


[logs](http://www.playframework.org/documentation/1.0/logs)

[api/2.0.4/java/play/i18n](http://www.playframework.org/documentation/api/2.0.4/java/play/i18n/package-summary.html "i18n")

[api/2.0.4/java](http://www.playframework.org/documentation/api/2.0.4/java/index.html)