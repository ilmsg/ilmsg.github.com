---
layout: post
title: "เขียน plugin wordpress ทำปุ่ม share ของ facebook, digg"
description: "เขียน plugin wordpress ทำปุ่ม share ของ facebook, digg"
category: tutorial
tags: [wordpress, php]
---
{% include JB/setup %}

การทำปุ่ม share ของ facebook, digg นั้น เราจะใช้คุณสมบัติของทาง facebook และ digg มาใช้งานกันนะ

การทำปุ่ม share ของ facebook ปกติจะเป็นแบบนี้

	http://www.facebook.com/sharer.php?u=http://wordpress.ilmsg.com/alexa-page-rank/

เราก็จะเปลี่ยนตรงตอนท้ายของ u= เป็น url ที่เราต้องการได้ และการทำปุ่ม share ของ digg ก็จะเป็นแบบนี้

	http://digg.com/submit?url=http://wordpress.ilmsg.com/alexa-page-rank/

ก็จะคล้ายๆกันเราก็จะเปลี่ยนตรง url= ให้เป็น url ตามที่เราต้องการ

มาดูกันว่าเราจะเอามาทำเป็น plugin ได้ยังไง

สร้าง plugin ขึ้นมาแล้วสร้าง function ตัวนี้ลงไป digg และ facebook นะ

	function WPDiggThis_Link(){
		global $post;
		
		// รับ URL จาก post id
		$link = urlencode(get_permalink($post->ID));
		
		// รับ post title
		$title = urlencode($post->post_title);
		
		// รับข้อความ 350 ตัวอักษรแรกจาก post และตัด html tag ออกไปด้วย 
		$text = urlencode(substr(strip_tags($post->post_content), 0, 350));
		
		// สร้าง link ของ Digg และส่งค่ากลับไป
		return '<a href="http://digg.com/submit?url='.$link.'&amp;title='.$title.'&amp;bodytext='.$text.'">Digg This</a>';
	}

อันนี้เป็นของ facebook

	function WPFacebookThis_Link(){
		global $post;
		
		// รับ URL จาก post id
		$link = urlencode(get_permalink($post->ID));
		
		// รับ post title
		$title = urlencode($post->post_title);
		
		// รับข้อความ 350 ตัวอักษรแรกจาก post และตัด html tag ออกไปด้วย 
		$text = urlencode(substr(strip_tags($post->post_content), 0, 350));
		
		// สร้าง link ของ Digg และส่งค่ากลับไป 
		return '<a onclick="window.open(\'http://www.facebook.com/sharer.php?u='. $link .'\',\'wn\',\'width=640,height=320,left=100,top=50,toolbar=0,status=0,resizable=1,scrollbars=1\');" title="Click to view" name="TLab WP Facebook Share" href="javascript:void(0);"><img border="0" src="images/facebook-share.jpg"></a></p>';
	}

ทำส่วนของ plugin กันเรียบร้อยแล้ว แต่ยังใช้งานไม่ได้ เราต้องไปแก้ไข theme ที่เราใช้งานอยู่ด้วย เพื่อเพิ่มส่วนของการเรียกใช้ function ที่ plugin ของเราสร้างมันมา

	<?php if(function_exists(WPFacebookThis_Link)) echo WPFacebookThis_Link(); ?>
	<?php if(function_exists(WPDiggThis_Link)) echo WPDiggThis_Link(); ?>

การนำไปใส่นใน theme ที่เราใช้งานอยู่ ตอนนี้ผมใช้ theme ชื่อว่า Breezing ก็จะเข้าไปแก้ไขไพล์ content-single.php ซึ่งโค้ดที่เราจะเอาไปใส่ก็ใส่หลังจาก content มองหาอย่างง่ายๆก็ หา div ที่มี class เป็น entry และการเรียกใช้ function ชื่อ the_content

![](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/2013-02-23_050909.png)

![](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/2013-02-23_051529.png)

เอารูปภาพปุ่ม facebook share ไปด้วย

![](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/facebook-share.jpg)

![](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/2013-02-23_031530.png)