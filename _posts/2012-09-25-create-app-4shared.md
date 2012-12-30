---
layout: post
title: "การสร้าง App 4Shared"
description: ""
category: 
tags: [php, app 4Shared]
---
{% include JB/setup %}

ตัวอย่างการ Authorize ของ App 4Shared เพื่อเข้าถึงข้อมูลของผู้ใช้ ทำผ่านทาง REST โดย OAuth 1.0

เริ่มกันตรงนี้เลย <http://www.4shared.com/developer>

นี้จะทำให้เห็นว่า การเข้าถึงข้อมูลของผู้ใช้ /user, /users, /folders, /files การสร้าง folder, การลบ folder, การ upload ไพล์, การลบไพล์

มีแนวคิดการจัดการไพล์พวกนี้ให้เป็นประโยชนได้อย่างไร พื้นที่ฟรี 15 GB น่าจะมี App 4Shared ที่สร้างโดยคนไทย ที่ดังๆสัก App นึงนะ

ในหน้าเต็มของการ Authorize จะเห็นว่า ผู้ใชัยังไม่ได้ เข้าระบบ ด้วยบัญชีของตัวเอง

![create-app-4shared](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/create-app-4shared-1.png)

การ Authorize ของ App 4Shared ต้องแสดงตัวตนของผู้ใช้ก่อน ต้อง Login เข้าระบบก่อน ถ้าหากยังไม่มีบัญชีก็สมัครได้เลย

![create-app-4shared](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/create-app-4shared-2.png)

ก่อนการ authorize ของ App 4Shared ต้อง Login เข้าระบบก่อน ยังไม่มีบัญชีก็สมัครได้เลย

ตัวอย่างข้อมูลผู้ใช้ของ 4shared ที่ได้ Authorize จากตัว App 4shared (เหมือนใน app facebook ที่ใช้ /me นั้นแหละ)

![create-app-4shared](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/create-app-4shared-3.png)

ข้อมูลผู้ใช้ของ 4shared

![create-app-4shared](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/create-app-4shared-4.png)

มี Folder อยู่ 2 อันใน Root Directory

![create-app-4shared](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/create-app-4shared-5.png)

มีไพล์รูปอยู่อันเดียว อันใน Root Directory

![create-app-4shared](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/create-app-4shared-6.png)