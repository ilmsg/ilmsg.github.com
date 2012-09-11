---
layout: page
title: ยองหละปูน
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
    
## Sample Posts

This blog contains sample posts which help stage pages and blog data.
When you don't need the samples anymore just delete the `_posts/core-samples` folder.

    $ rm -rf _posts/core-samples

Here's a sample "posts list".
-->

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## หมายเหตุ

ที่ย้าย blog มาที่ github เพราะกลัวว่า host ที่ใช้อยู่จะไม่มีเงินจ่ายเค้า (ตอนนี้เงินซื้อข้าวกินแทบจะไม่มีอยู่แล้ว)
หรือเผื่อผมตายไปหลายๆอย่างที่เคยทำเอาไว้จะได้ไม่สูญเปล่าให้คนข้างหลังได้ใช้ประโยชน์บ้าง github ฟรี 
ผมทำโปรเจ็ค เขียนโค้ด ยังไงก็ต้องใช้ github, gist 

<!--
This theme is still unfinished. If you'd like to be added as a contributor, [please fork](http://github.com/plusjade/jekyll-bootstrap)!
We need to clean up the themes, make theme usage guides with theme-specific markup examples.
-->

