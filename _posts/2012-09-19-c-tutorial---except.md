---
layout: post
title: "C# Tutorial การใช้งาน Except"
description: ""
category: 
tags: [C#, ]
---
{% include JB/setup %}

ตัวอย่างการใช้งาน Except 

เป็นการสร้าง array ใหม่โดยที่ เป็นข้อมูลจาก numberA ทั้งหมด แล้วข้อมูลต้องไม่มีใน numberB ด้วย

#### source code

	public void Linq52(){
		int[] numbersA = { 0, 2, 4, 5, 6, 8, 9 };
		int[] numbersB = { 1, 3, 5, 7, 8 };
	
		IEnumerable aOnlyNumbers = numbersA.Except(numbersB);
	
		Console.WriteLine("Numbers in first array but not second array:");
		foreach (var n in aOnlyNumbers){
			Console.WriteLine(n);
		}
	}

#### Result

	Numbers in first array but not second array:
	0
	2
	4
	6
	9