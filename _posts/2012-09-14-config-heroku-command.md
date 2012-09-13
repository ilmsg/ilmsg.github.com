---
layout: post
title: "คำสั่ง Heroku Command กับการเพิ่ม,ลบ key ของ config"
description: ""
category: howto
tags: [heroku]
---
{% include JB/setup %}

### คำสั่ง Heroku Command กับการเพิ่ม,ลบ key ของ config

##### คำสั่งแสดง key, value ของ config ทั้งหมด

	$ heroku config

##### การเพิ่ม add
	
	$ heroku config:add key1=value1

##### คำสั่งนี้เราเพิ่ม key กับ value เข้าไป 1 ชุด ถ้าต้องการเพิ่มทีละหลายๆชุดก็ใช้แบบนี้

	$ heroku config:add key1=value1 key2=value2 key3=value3 key4=value4

ใช้ง่ายๆเลย คำสั่งเดิมแต่ใช้ [Spacebar] ในการเว้นวรรคแต่ละชุดเอาไว้ 

หลังจากการใช้คำสั่งนี้แล้ว ลองดูผลลัพธ์ด้วยคำสั่ง

	$ heroku config
	
##### การลบ delete

	$ heroku config:remove key1
	
คำสั่งลบก็ใช้เพียงระบุ key ลงไปว่าต้องการจะลบ key ตัวไหน











