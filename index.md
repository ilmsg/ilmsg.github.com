---
layout: page
title: �����͹�ͧ��лٹ
tagline: ���㴷���ͧ������շͧ��ͧ��� ��͹�鹤��ͧ�����˭���蹴Թ �֧�֧
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

## �觷��»���ҵ�͹�Ѻ������

�չ����Ҩе�ͧ��� node.js ��� run ��ҹ��ԧ��騧�� �������������Թ���·ͧ�ѹ�ա����....

��¡�ú�����������

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## �����˵�

������� blog �ҷ�� github ��������ѹ��� ��Ǽ����� host �����������������仨����Թ������ 
��������ҧ����·��������������٭������餹��ҧ��ѧ�������ª���ҧ
domain ����� 2 ��ǹ����� [ilmsg.com](http://ilmsg.com) ==> [ilmsg.github.com](http://ilmsg.github.com)

