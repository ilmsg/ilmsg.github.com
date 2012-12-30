---
layout: post
title: "LINQ 2 Method"
description: ""
category: 
tags: []
---
{% include JB/setup %}

ดูการใช้ LINQ ระหว่าง 2 Mehod วันหลังเราจะใช้แบบนี้มั้ง

#### วิธีที่ 1

	public ActionResult DoSomething1(int id){
		ViewData.Model = (from m in _db.MovieSet where m.Id == id select m).FirstOrDefault();
		return View();
	}

#### อันนี้เป็นวิธีที่ 2

	public ActionResult DoSomething(int id){
		ViewData.Model = _db.MovieSet.First(m => m.Id == id);
		return View();
	}