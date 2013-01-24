---
layout: post
title: "การ render view ใน folder ย่อย"
description: "การแยก view ใน folder ย่อยๆ แล้วเรียกไปแสดงผลใน controller"
category: howto
tags: [play framework, controller, view]
---
{% include JB/setup %}

ปกติใน controller ที่ไม่มี folder ย่อยใน views การ import ก็แบบนี `/views/index.scala.html`
	
	import views.html.*;

การแสดงผลก็จะใช้ประมาณนี้

	return ok( "ข้อความตรงนี้" );
	return ok( views.html.index.render("ข้อความตรงนี้") );

`views.html` อันนี้เป็นค่าปกติ เรา `import views.html.*` อยู่แล้ว ก็ใช้ `index.render("ข้อความ");`

การทำ folder ย่อยภายใน views ประโยชน์คือ แยกตาม controller เวลาอ่านโค้ด แก้ไข จะทำให้ดูง่ายขึ้น
ตัวอย่าง folder

	/views/products/index.scala.html


ก่อนใช้คำสั่งใน controller ต้อง import เข้ามาก่อน

	import views.html.products.*;


คำสั่งใน controller
		
	return ok(index.render(products));
