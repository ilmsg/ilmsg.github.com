---
layout: post
title: "extension chrome .crx"
description: ""
category: 
tags: []
---
{% include JB/setup %}

ประเภท Extension ไพล์ของ Google Chrome ที่เป็น .CRX  มันอยู่ในรูปแบบของไพล์ที่ Compression แล้ว (พวก zip, rar นั้นแหละ) ฉะนั้นแล้วถ้าเราต้องการที่จะดูว่าอะไรอยู่ข้างใน extension บ้าง ที่เป็นพวก script และ source code ต่างๆ เราต้องเปลี่ยนประเภทของไพล์จาก "CRX" ไปเป็น "ZIP" หรือ "RAR" ก็ได้. หลังจากนั้นก็แกะไพล์ zip หรือ rar แบบปกติที่เคยทำเลย ทีนี้เราก็จะเห็นไพล์ต่างๆที่อยู่ข้างในนั้น วิธีนี้จะทำให้เราเห็นไส้ในของมันว่ามีอะไรบ้าง เรียนรู้วิธีที่จะเขียน extension ด้วยตัวเอง หรือแก้ไข extension นั้นตามที่เราต้องการ แล้วเราก็ยังแพ็คไพล์เก็บสำรองเอาไว้ ที่เป็น ".CRX" แล้วติดตั้งมันใหม่ด้วยไม่กี่คลิก


หลังจากที่ติดตั้ง Chrome extension แล้ว ไดเรกทอรี่จะอยู่มานี้

ให้ก๊อปปี้โฟลเดอร์ extension ที่ต้องการแก้ไข ( ชื่อจะถูกเรียงลำดับตาม extension ID ).

จาก url นี้ chrome://settings/extensionSettings ที่อยู่ในโหมดสำหรับนักพัฒนาซอร์ฟแวร์ ให้เลือก โหลดส่วนขยายที่คลายการแพคแล้ว แล้วเลือกโฟลเดอร์ที่เราก๊อปปี้ extension เตรียมไว้แล้ว

หลังจากที่ทำการเปลี่ยนแล้ว ให้ refresh เพือโหลด extension ที่เพิ่งติดตั้งเข้าไปใหม่

สำหรับ Mac:
/Users/username/Library/Application Support/Google/Chrome/Default/Extensions

สำหรับ Windows 7:
C:\Users\username\AppData\Local\Google\Chrome\User Data\Default\Extensions

สำหรับ Windows XP:
C:\Documents and Settings\YourUserName\Local Settings\Application Data\Google\Chrome\User Data\Default