---
layout: post
title: "C# Tutorial Where Simple1"
description: ""
category: 
tags: []
---
{% include JB/setup %}

ตัวอย่างการใช้ where เพื่อหา element ใน array ที่มีค่าน้อยกว่า 5

#### source code

	public void Linq1(){
		int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };
	
		var lowNums =
			from n in numbers
			where n < 5
			select n;
	
		Console.WriteLine("Numbers < 5:");
		foreach (var x in lowNums)
		{
			Console.WriteLine(x);
		}
	}

#### Result

	Numbers < 5: 
	4 
	1 
	3 
	2 
	0