---
layout: post
title: "การเปลี่ยน type ของ field กับฐานข้อมูล MongoDB"
description: ""
category: 
tags: [mongodb]
---
{% include JB/setup %}


เอกสารจาก mongodb.org เรื่อง $type 
[http://www.mongodb.org/display/DOCS/Advanced+Queries#AdvancedQueries-%24type](http://www.mongodb.org/display/DOCS/Advanced+Queries#AdvancedQueries-%24type)



### String to Integer

	db.db-name.find({field-name : {$exists : true}}).forEach( function(obj) { obj.field-name = new NumberInt(obj.field-name); db.db-name.save(obj); } );

### Integer to String

	db.db-name.find({field-name : {$exists : true}}).forEach( function(obj) { obj.field-name = ""+obj.field-name; db.db-name.save(obj); } );



##### รวบรวมข้อมูลจาก

[http://stackoverflow.com/questions/4973095/mongodb-how-to-change-the-type-of-a-field](http://stackoverflow.com/questions/4973095/mongodb-how-to-change-the-type-of-a-field)
