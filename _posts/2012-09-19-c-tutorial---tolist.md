---
layout: post
title: "C# Tutorial - ToList"
description: ""
category: 
tags: []
---
{% include JB/setup %}

ToList

ตัวอย่างการใช้ ToList เป็นการแปลงข้อมูลที่อยู่ในรูปแบบแถวลำดับอยู่แล้ว เช่น array ให้อยู่ในรูปแบบ `List<T>`

#### source code

	public void Linq55(){
		string[] words = { "cherry", "apple", "blueberry" };
	 
		var sortedWords =
			from w in words
			orderby w
			select w;
		var wordList = sortedWords.ToList();
	 
		Console.WriteLine("The sorted word list:");
		foreach (var w in wordList)
		{
			Console.WriteLine(w);
		}
	}

#### Result

	The sorted word list:
	apple
	blueberry
	cherry
