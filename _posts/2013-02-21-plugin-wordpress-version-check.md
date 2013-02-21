---
layout: post
title: "เขียน plugin wordpress เช็ค version ของ wordpress ก่อนติดตั้งปลั้กอิน"
description: "เขียน plugin wordpress เช็ค version ของ wordpress ก่อนติดตั้งปลั้กอิน"
category: tutorial
tags: [wordpress, php]
---
{% include JB/setup %}

การเขียนปลั้กอินใช้งานกับ wordpress เนื่องด้วย wordpress มีการพัฒนาเวอร์ชั่นอย่างต่อเนื่อง และก็จะมี function บางตัวที่ถูกยกเลิกไป 
นี้แหละที่ทำให้ plugin ที่เราสร้างขึ้นมา อาจจะใช้งานไม่ได้กับ wordpress เวอร์ชั่นใหม่ ๆ  

ฉะนั้น plugin ที่เราเขียนขึ้นมาต้องเช็คเวอร์ชั่นของ wordpress ก่อนติดตั้ง

	if( version_compare($wp_version, "3.5.1", "<") ){
		// ทำอะไรบางอย่าง เมื่อผู้ใช้นำปลั้กอินนี้ไปติดตั้งกับ wordpress ที่มีเวอร์ชั่นต่ำกว่า 3.5.1
	}

ลองดูอีกแบบที่เป็นการใช้งานจริงๆ

![](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/2013-02-21_214337.png)

source code

	function tlab_check_version(){
		echo '
		<div id="tlab-version-error" class="updated fade">
			<p>ปลั้กอินนี้ต้องติดตั้งกับ WordPress เวอร์ชั่น 3.5.1 หรือ เวอร์ชั่นที่ใหม่กว่า. <a href="http://codex.wordpress.org/Upgrading_WordPress">โปรดอัพเดต Wordpress !</a></p>
		</div>';
	}
	
	if( version_compare($wp_version, "3.5.1", "<") ){
		add_action( 'admin_notices', 'tlab_check_version');
	}

