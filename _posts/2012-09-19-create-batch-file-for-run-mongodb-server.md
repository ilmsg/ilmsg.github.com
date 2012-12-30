---
layout: post
title: "create batch file for run mongodb server"
description: ""
category: 
tags: []
---
{% include JB/setup %}

<a href="http://ilmsg.com/wp-content/uploads/2011/07/2011-07-11_234137.jpg"><img class="aligncenter size-medium wp-image-234" title="2011-07-11_234137" src="http://ilmsg.com/wp-content/uploads/2011/07/2011-07-11_234137-300x278.jpg" alt="" width="300" height="278" /></a>

ตามรูปเลยนะ ผมเปิด notepad ออกมาแล้วสร้างไพล์ ชื่อ start_mongodb.bat แล้วข้างในไพล์ ก็จะมีคำสั่งนี้อยู่ข้างใน

### batch file 

	@ECHO OFF
	TITLE MongoDB Server
	mongod.exe --dbpath d:\data\db

@ECHO OFF เป็นคำสั่งปิดการแสดงการใช้คำสั่ง ไม่ต้องสนใจ ไม่มีอะไรมาก

TITLE MongoDB Server อันนี้เป็นคำสั่งใส่ Title ของ window command ให้มันว่าชื่ออะไร เอาไว้ใช้ได้ดีในการเปิดหลาย ๆ หน้าต่าง จะได้ดูง่าย ๆ ว่าอะไรเป็นอะไร

mongodb.exe --dbpath d:\data\db   อันนี้เป็นคำสั่งที่เราพิมพ์แบบ command line นั้นแหละ เอามาใส่ตรงนี้ เปลี่ยนตามชื่อ folder ที่เก็บ database ได้ตามสดวกเลย

<a href="http://ilmsg.com/wp-content/uploads/2011/07/2011-07-11_234250.jpg">
<img class="aligncenter size-medium wp-image-235" title="2011-07-11_234250" src="http://ilmsg.com/wp-content/uploads/2011/07/2011-07-11_234250-300x151.jpg" alt="" width="300" height="151" /></a>ทีนี้เราก็จะ start database server ได้แบบง่าย ๆ คลิกเมาส์กันอย่างเดียว ไม่ต้องเปิด command line เข้าไปพิมพ์คำสั่ง ลองเอาไปใช้กันดูนะ

อ้ออีกอย่าง สร้าง shoutcut ตัว start_mongodb.bat ไว้ที่หน้า desktop ก็ได้นะ คลิกเอาที่หน้า desktop ง่ายๆเลย ไม่ต้องเข้าหลาย folder

เพิ่มเติมนะ

สร้าง shoutcut ด้วยคำสั่ง start ตัวของ mongodb ได้เลยนะ ไม่ต้องสร้าง batch file แล้วสร้าง shoutcut ของ batch file แล้วก็เรียกใช้ shoutcut ของ batch file อีกทีนึง เรียกใช้หลายต่อเกิน

shoutcat to start mongodb ไปเลย ม้วนเดียวจบ