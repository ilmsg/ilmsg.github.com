---
layout: post
title: "เรียนรู้ javascript ตอน #1"
description: ""
category: tutorial
tags: [javascript]
---
{% include JB/setup %}

การใช้ javascript ใน html

	<!DOCTYPE html>
	<html>
	<body>
	<h1>My Javascript Giggog</h1>
	<p id="desc">My First Paragraph</p>
	 
	<script type="text/javascript">
		// javascript code ตรงนี้
		document.getElementById("desc").innerHTML="JavaScript ของฉัน";
	</script>
	 
	</body>
	</html>
	
	
### การสร้าง Object

สร้าง Object ชื่อ ilmsg ( เขียนได้ 2 แบบ )

สร้าง Object แบบที่ 1

	var ilmsg = Object();


สร้าง Object แบบที่ 2

	var ilmsg = {};

ในแบบที่ 2 จะนิยมกันมากกว่า เพราะสือความหมายได้ง่าย ถ้าเป็น object ที่มี attribute หรือ method ก็จะอยู่ในรูปแบบนี้

	var ilmsg = {
		type: 'blog',
		author: 'Eak Netpanya',
		aboutme: function(){
			// about me
		}
	};
	
	
	
	
	
	
	
	
	