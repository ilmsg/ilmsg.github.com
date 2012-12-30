---
layout: post
title: "C# Tutorial Where Simple2"
description: ""
category: 
tags: []
---
{% include JB/setup %}

ตัวอย่างการใช้ where เพื่อหาสินค้าที่หมดคลังสินค้า

#### source code

	public void Linq2(){
		List products = GetProductList();
	
		var soldOutProducts =
			from p in products
			where p.UnitsInStock == 0
			select p;
	
		Console.WriteLine("Sold out products:");
		foreach (var product in soldOutProducts){
			Console.WriteLine("{0} is sold out!", product.ProductName);
		}
	}

#### Result

	Sold out products: 
	Chef Anton's Gumbo Mix is sold out! 
	Alice Mutton is sold out! 
	ThÃ¼ringer Rostbratwurst is sold out! 
	Gorgonzola Telino is sold out! 
	Perth Pasties is sold out!