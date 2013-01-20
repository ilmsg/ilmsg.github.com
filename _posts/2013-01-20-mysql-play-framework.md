---
layout: post
title: "การใช้ฐานข้อมูล mysql กับ play framework"
description: "การใช้ฐานข้อมูล mysql กับ play framework"
category: howto
tags: [mysql, java, play framework]
---
{% include JB/setup %}


อันดับแรก เพิ่ม database driver  ลงไปก่อน product\Build.scala

	val appDependencies = Seq(
    	// Add your project dependencies here,
		...
    	"mysql" % "mysql-connector-java" % "5.1.18"
		...
	)

ดาวน์โหลดติดตั้งตัว Driver ด้วยคำสั่งนี้

	play dependencies


หลังจากนั้นก็ไปแก้ไขไพล์ conf/application.conf

	db.default.driver=com.mysql.jdbc.Driver
	db.default.url="mysql://root:rootpassword@localhost/mydatabase"

[Database](http://www.playframework.org/documentation/2.0.4/JavaDatabase)
