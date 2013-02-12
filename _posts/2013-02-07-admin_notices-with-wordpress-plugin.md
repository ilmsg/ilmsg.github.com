---
layout: post
title: "สร้างข้อความแจ้งเตือนกับปลั้กอิน wordpress"
description: "การใช้คำสั่ง admin_notices สร้างข้อความแจ้งเตือนกับปลั้กอิน wordpress"
category: tutoiral
tags: [wordpress, plugin]
---
{% include JB/setup %}

![Notices ของ WordPress Plugin](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/2013-02-07_224818.png)


	add_action( 'admin_menu', 'tlabwarnning_menu' );
	add_action( 'admin_notices', 'tlabwarnning');

	function tlabwarnning_menu(){
		$wp_plugin_url = WP_PLUGIN_URL . '/' . plugin_basename( dirname( __FILE__ ) );
		add_menu_page( __('ตั้งค่าปลั้กอิน TLab'), __('ตั้งค่าปลั้กอิน TLab') ,1,"tlabwarnning-option", "tlabwarnning_config", '', 99);
	}

	function tlabwarnning_config(){
		echo '<div class="wrap">';
		echo '<div id="icon-options-general" class="icon32"><br /></div>';
		echo '<h2>ตั้งค่าปลั้กอิน TLab</h2>';
		echo '<form method="post" action="admin.php?page=tlabwarnning-option">';  
		echo '<p><strong>Email:</strong><br />';
		echo '<input type="text" name="tlab_email" size="50" value="'. get_option('tlab_email') .'" /></p>';
		echo '<p class="submit"><input type="submit" name="submit" id="submit" class="button button-primary" value="บันทึกการเปลี่ยนแปลง"></p>';
		echo '<input type="hidden" name="action" value="update" />';
		echo '</form>';
		echo '</div>';	
	}

	function tlabwarnning(){
		if ( !get_option('tlab_email') ) {
			echo '<div id="tlab-warning" class="updated fade">';
			echo '<p><strong>ปลั้กอิน TLabWarnning ยังไม่ได้ตั้งค่าเริ่มต้น</strong>';
			echo ' คุณจะต้อง <a href="admin.php?page=tlabwarnning-option">คลิกที่นี้</a> เพื่อตั้งค่าการใช้งานให้เหมาะสม.</p>';
			echo '</div>';
		}
	}