---
layout: post
title: "change table name and reset auto id mssql server"
description: ""
category: 
tags: []
---
{% include JB/setup %}

คำสั่ง เปลี่ยนชื่อ ตารางของฐานข้อมูล ms sql server

ตัวอย่าง : ต้องการเปลี่ยนชื่อตาราง test ไปเป็นตาราง employee

	exec sp_rename "test", "employee"


แล้วนี้ก็เป็นคำสั่ง reset auto id ของ table ใน ms sql server 

ตัวอย่าง : ต้องการ reset auto id ของตารางชื่อ test

	dbcc checkident('test',reseed,0);

it work for me.