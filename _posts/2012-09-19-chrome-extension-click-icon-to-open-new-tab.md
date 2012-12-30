---
layout: post
title: "Google Chrome Extensions - คลิก icon บน toolbar แล้วเปิด tab ใหม่"
description: ""
category: 
tags: []
---
{% include JB/setup %}

Google Chrome Extensions - เมื่อคลิก icon บน toolbar แล้วให้มันเปิด tab ใหม่
ใน manifest ไพล์ เราจะต้องกำหนด permission ให้กับ tabs ด้วย
Manifest File:

{
"name": "My Extension",
"version": "1.0",
"description": "Opens up a local webpage",
"icons": { "128": "icon128.png" },
"background_page": "bg.html",
"browser_action": {
"default_title": "",
"default_icon": "icon22.png"
},
"permissions": [
"tabs"
],
}

ในไพล์ background (bg.html), เราต้องเขียนโค้ดดัก event click mouse ของเจ้าตัว browser อีกทีนึง

chrome.browserAction.onClicked.addListener(function(tab) {
chrome.tabs.create({'url': chrome.extension.getURL('f.html')}, function(tab) {
// Tab opened.
});
});

ตามตัวอย่างข้างบนเลย มันจะเปิดไพล์ f.html ที่เราทำไว้ใน extension ของเราด้วย
ถ้าไม่อยากให้มันเปิดไพล์ใน extension ของเรา เราสามารถใส่เป็น url เข้าไปได้เลย เช่น

chrome.browserAction.onClicked.addListener(function(tab) {
chrome.tabs.create({'url': 'http://www.ilmsg.com/'}, function(tab) {
// Tab opened.
});
});

แบบนี้ได้เช่นกัน