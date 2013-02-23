---
layout: post
title: "เขียน plugin wordpress ทำปุ่ม share ของ facebook, digg โดยใช้ add_filter"
description: "เขียน plugin wordpress ทำปุ่ม share ของ facebook, digg โดยใช้ add_filter"
category: tutorial
tags: [wordpress, php]
---
{% include JB/setup %}

ก่อนหน้านี้จะทำปุ่ม share เราต้องไปแก้ไขไพล์ theme ด้วย ซึ่งซับซ้อนและยุ่งกับส่วนอื่นๆด้วยที่ไม่ใช่แค่ plugin อย่างเดียว ทีนี้การใช้ add_filter จะทำให้เราไม่ต้องไปแก้ไขไพล์ theme อีกแล้ว

digg

	function WPDiggThis_ContentFilter($content){ 
		return $content.WPFacebookThis_Link(); 
	}
	add_filter('the_content', 'WPDiggThis_ContentFilter');

facebook

	function WPFacebookThis_ContentFilter($content){ 
		return $content.WPDiggThis_Link(); 
	}
	add_filter('the_content', 'WPFacebookThis_ContentFilter');