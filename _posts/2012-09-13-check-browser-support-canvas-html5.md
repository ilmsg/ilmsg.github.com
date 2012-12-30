---
layout: post
title: "เช็ค browser ว่าใช้ canvas html5 ได้หรือไม่"
description: "เช็ค browser ว่าใช้ canvas html5 ได้หรือไม่"
category: howto
tags: [html5]
---
{% include JB/setup %}

ฟังก์ชั่นใช้สำหรับ เช็คว่าบราว์เซอร์ของผู้ใช้ สนับสนุน canvas  รึเปล่า

	function supports_canvas() { 
		return !!document.createElement('canvas').getContext; 
	}  

ใช้ร่วมกับ jQuery ได้

	$(document).ready( function(){ 
		if(!supports_canvas()){ 
			//Doesn't support canvas; 
			$('#p1').text("Sorry! But your browser doesn't support everything we need to play."); 
			$('#p2').html("Click <a href='http://www.browserupgrade.info/how-to-upgrade/'>here</a> to learn about upgrading your browser!"); 
		} 
	});