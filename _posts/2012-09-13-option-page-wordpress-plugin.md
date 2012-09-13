---
layout: post
title: "สร้าง page สำหรับตั้งค่า ปลั้กอิน wordpress"
description: ""
category: 
tags: [wordpress, plugin]
---
{% include JB/setup %}

สร้าง Option Page ของ WordPress Plugin 

![Option Page ของ WordPress Plugin](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/option-page-wordpress-plugin.jpg)


	add_action('admin_menu', 'tlab_option_page');
	 
	function tlab_option_page() {
		add_options_page('ตั้งค่าปลั้กอินของฉัน', 'ตั้งค่าปลั้กอินของฉัน', 'manage_options', 'tlab_option_page', 'my_plugin_options');
	}
 
	function my_plugin_options(){
		echo '<div class="wrap">';
		echo '<div id="icon-options-general" class="icon32"><br /></div>';
		echo '<h2>ตั้งค่าปลั้กอินของฉัน</h2>';
		echo '<p>การตั้งค่าของปลั้กอินของฉัน</p>';
		echo '<form method="post" action="">';
		echo 'หัวข้อ : <input type="text" size="40"/><br/>';
		echo 'รายละเอียด : <br/><textarea rows="5" cols="80"></textarea><br/>';
		echo '<input type="submit" class="button-primary"  value="บันทึก" />';
		echo '<input type="submit" class="button"  value="รีเซตการตั้งค่า" />';
		echo '</form>';
	}

การตั้งค่าของ plugin ทำแบบฟอร์มไว้เฉยๆนะ ยังไม่ได้ทำส่วนที่ update ข้อมูลการตั้งค่าลง Database กันจริงๆ

รายละเอียดเพิ่มเติม

[http://codex.wordpress.org/Function_Reference/add_options_page](http://codex.wordpress.org/Function_Reference/add_options_page)



