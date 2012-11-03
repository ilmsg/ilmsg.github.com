---
layout: page
title: หละอ่อนยองหละปูน
tagline: เมอใดที่ท้องฟ้าเป๋นสีทองฝ่องอำไพ เมอนั้นคนยองจะเป๋นใหญ่ในแผ่นดิน กึงนึง
---
{% include JB/setup %}

<!--
Read [Jekyll Quick Start](http://jekyllbootstrap.com/usage/jekyll-quick-start.html)

Complete usage and documentation available at: [Jekyll Bootstrap](http://jekyllbootstrap.com)

## Update Author Attributes

In `_config.yml` remember to specify your own data:
    
    title : My Blog =)
    
    author :
      name : Name Lastname
      email : blah@email.test
      github : username
      twitter : username

The theme should reference these variables whenever needed.
-->   

## เริ่มหนาว

ต้นเดือนพฤษจิกายน ตอนเช้าๆอากาศเย็นๆ ไม่อยากตื่นเลย นอนหลับอุตุอยู่ในผ้าห่ม

ในที่สุดก็ได้ online ไปกับ node.js แบบจริงจัง งานนี้ยากเหมือนอย่างที่คิดไว้เลย เหอๆๆ

รายการบทความทั้งหมด

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

<!--
## หมายเหตุ

ที่ย้าย blog มาที่ github เพราะว่ามันฟรี เด๋วผมตายไป host ที่ใช้อยู่จะไม่มีใครไปจ่ายเงินให้เค้า 
หลายๆอย่างที่เคยทำเอาไว้จะได้ไม่สูญเปล่าให้คนข้างหลังได้ใช้ประโยชน์บ้าง
domain เข้าได้ 2 ตัวนี้เลย [ilmsg.com](http://ilmsg.com) ==> [ilmsg.github.com](http://ilmsg.github.com)

ไม่ได้ทำมีโปรเจ็คใหญ่โตอะไรเลย เขียนโค้ดเล็กๆน้อยๆ บันทึกเอาไว้ตอนลืมก็กลับมาดู ยังไงก็ต้องใช้ github, gist 
--> 

