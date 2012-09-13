---
layout: post
title: "Menu Page ของ Plugin"
description: ""
category: tutorial
tags: [wordpress plugin]
---
{% include JB/setup %}

ใน plugin ของ wordpress อนุญาติให้เราสร้าง menu ที่จะไปหน้า page ของ plugin เราโดยเฉพาะได้ด้วย

ตัวอย่างใน plugin ที่ผู้ใช้ plugin ติดตั้งเสร็จแล้วก็จะต้องไปตั่งค่าของ plugin ให้ทำงานอย่างเหมาะสมกับ blog ของเรา

![เมนู page ของ plugin](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/menu-page-wordpress-plugin.png)


source code ก็มี
- add_action เข้าไปที่ admin_menu ในชื่อ tlab_mymenu
- tlab_mymenu จะเพิ่มเมนูเข้าไปใหม่ โดยใช้ add_menu_page ในชื่อ tlab_mymenu_settings
- tlab_mymenu_settings ตัวนี้ก็จะสร้าง Page ของเมนูนั้นๆไป


##### Source Code

	add_action('admin_menu', 'tlab_mymenu');
	 
	function tlab_mymenu(){
		$wp_plugin_url = WP_PLUGIN_URL . '/' . plugin_basename( dirname( __FILE__ ) );  
			   add_menu_page("ตัวอย่างเมนู" ,"ตัวอย่างเมนู",1,"tlab-mymenu-option-page",'tlab_mymenu_settings',$wp_plugin_url . '/redneck.png'  );
	}
 
	function tlab_mymenu_settings(){
		echo '<div class="wrap">';
		echo '<div id="icon-options-general" class="icon32"><br /></div>';
			   echo '<h2>ตัวอย่างเมนูของฉัน</h2>';
			   echo '<p>การตั้งค่าของปลั้กอิน ตัวอย่างเมนูของฉัน</p>';
	}


refer:
	
	[http://codex.wordpress.org/Function_Reference/add_menu_page](http://codex.wordpress.org/Function_Reference/add_menu_page)




