---
layout: post
title: "chrome extension for remove banner"
description: ""
category: 
tags: []
---
{% include JB/setup %}

เปิดเข้าหน้า app นี้ทีไร มี banner ขึ้นมาให้รำคาญมากมาย (จำกัดความ ของความหมาย "มากมาย" หมายถึง banner จำนวนมากมาย หรือ ความรำคาญจำนวนมากมา )

### วิธีแก้ปัญญหาคือ

1. url นี้เท่านั้นที่มี tag ของ div บรรจุ banner เอาไว้
2. ใช้ browser ตัวเดียวคือ chrome

เขียน chrome extension ให้ทำงานเฉพาะ url นี้เท่านั้น ให้ document.getElementById('id_content').removeChild(document.getElementById('id_banner'));

#### source code 

	function removeElement(divNum) {
	  var d = document.getElementById('myDiv');
	  var olddiv = document.getElementById(divNum);
	  d.removeChild(olddiv);
	}
