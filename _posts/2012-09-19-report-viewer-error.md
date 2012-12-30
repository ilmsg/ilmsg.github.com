---
layout: post
title: "report viewer error"
description: ""
category: 
tags: [report viewer]
---
{% include JB/setup %}

วันนี้ไปตะลุย report viewer ตอนเช้าดูลาดราวไว้ล่ะ มีแต่เค้าใชักับ 2008 แต่เรา 2010 - -" ( กลับไปใช้ 2008 ท่าจะดี เอาไว้ทำ report โดยเฉพาะเลยนะ เอิ๊ก ๆๆ ) จาทำ report viewer ที่มันเป็น mvc อ่ะ แต่หาตัวอย่างไม่ได้เลย 5555+ (ไม่มีใครอาจหาญที่จะทำ) แน่นอนว่า mvc มันต้อง work กว่า webform สิ.... เอ๋...หรือว่าเราคิดผิด หึหึ (โรคบ้า pattern design กำเริบล่ะ )

 เรามันขั้นเมพ ตกลงใจไปลุย report viewer ใน vs2010+mvc3 razor 555+ ผลลัพธ์ไม่ต้องพูดถึง มึนสิคับพี่น้อง 5555+ ได้ Error กลับมา 1 ตัว

[caption id="attachment_104" align="aligncenter" width="996" caption="The Report Viewer Web Control requires a System.Web.UI.ScriptManager on the web form"]<a rel="attachment wp-att-104" href="http://ilmsg.com/?attachment_id=104"><img class="size-full wp-image-104" title="The Report Viewer Web Control requires a System.Web.UI.ScriptManager on the web form" src="http://ilmsg.com/wp-content/uploads/2011/03/ddd1.png" alt="The Report Viewer Web Control requires a System.Web.UI.ScriptManager on the web form" width="996" height="293" /></a>[/caption]

พอเลย ไปทำ report viewer ใน win app ให้รอดก่อนดีกว่า เด๋วค่อยกลับมาทำ web app นั่งนึกตั้งนาน จะทำ report แล้วมันจะ report ของอะไรดีฟ่ะ มันต้องมี database ก่อนจิ จะได้เข้าท่าเข้าทางหน่อย ไปได้ database ในตำนานของ MS ที่มันชื่อว่า Northwind.mdf  ลงมือ datasource , dataset อะไรของมันไม่รุ้ มีอื้อเลย ทำได้แบบว่าแสดงข้อมูลตาราง Customer ออกมาได้แบบ งง ๆๆ เหอ ๆๆ 

ไปเข้าคอร์ทอบรม Report Viewer  "เมพ Report Viewer ให้ได้ภายใน 15 นาที"  หลักสูตรเร่งรัด 