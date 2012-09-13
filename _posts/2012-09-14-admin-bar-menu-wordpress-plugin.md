---
layout: post
title: "ทำเมนูบาร์ของผู้ดูแลระบบ (admin bar menu)"
description: ""
category: tutorial
tags: [wordpress plugin, php]
---
{% include JB/setup %}

ในส่วนของ admin บนบาร์จะมีเมนูที่เป็นทางลัดอยู่ เราจะทำเมนูของเราใส่เพิ่มเข้าไปในส่วนนี้กัน

ตัวอย่าง 'เมนูของฉัน'


![เมนูบาร์ admin ที่ทำเพิ่งเข้าไป](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/menu-page-wordpress-plugin.png)


	if( is_admin() ){
		add_action( 'admin_bar_menu', 'tlab_toolbar_menu', 999 );
	}


ลำดับการสร้าง


	1. สร้างตัวแม่มันก่อน
	
	2. สร้างกลุ่ม
	
	3. สร้างลูกแล้วบอกว่าใครเป็นแม่มัน


##### Source Code

	function tlab_toolbar_menu( $wp_admin_bar ){
		$wp_plugin_url = WP_PLUGIN_URL . '/' . plugin_basename( dirname( __FILE__ ) );
		 
		// create main menu
		$args = array(
			'id' => 'tlab_adminbar1',
			'title' => '<span class="ab-icon" style="margin-top: 3px;"><img src="' . $wp_plugin_url . '/redneck.png" alt="เมนูของฉัน" /></span><span class="ab-label">เมนูของฉัน</span>',
			'href' => 'admin.php?page=tlab_adminbar_dashboard',
			'parent' => false
		);
		$wp_admin_bar->add_node( $args );
		 
		// create group
		$args = array(
			'id' => 'tlab_adminbar_group',
			'parent' => 'tlab_adminbar1'
		);
		$wp_admin_bar->add_group( $args );
		 
		// create submenu1
		$args = array(
			'id' => 'tlab_adminbar2',
			'title' => '<span class="ab-icon" style="margin-top: 3px;"><img src="' . $wp_plugin_url . '/chiken.png" alt="Tlab Icon" /></span><span class="ab-label">เมนูไก่</span>',
			'href' => 'admin.php?page=tlab_adminbar_chiken',
			'parent' => 'tlab_adminbar_group'
		);
		$wp_admin_bar->add_node( $args );
		 
		// create submenu2
		$args = array(
			'id' => 'tlab_adminbar3',
			'title' => '<span class="ab-icon" style="margin-top: 3px;"><img src="' . $wp_plugin_url . '/eggs.png" alt="Tlab Icon" /></span><span class="ab-label">เมนูไข่</span>',
			'href' => 'admin.php?page=tlab_adminbar_eggs',
			'parent' => 'tlab_adminbar_group'
		);
		$wp_admin_bar->add_node( $args );
		 
		// create submenu3
		$args = array(
			'id' => 'tlab_adminbar4',
			'title' => '<span class="ab-icon" style="margin-top: 3px;"><img src="' . $wp_plugin_url . '/pig.png" alt="Tlab Icon" /></span><span class="ab-label">เมนูหมู</span>',
			'href' => 'admin.php?page=tlab_adminbar_pig',
			'parent' => 'tlab_adminbar_group'
		);
		$wp_admin_bar->add_node( $args );
		 
		// create submenu4
		$args = array(
			'id' => 'tlab_adminbar5',
			'title' => '<span class="ab-icon" style="margin-top: 3px;"><img src="' . $wp_plugin_url . '/cup_of_milk.png" alt="Tlab Icon" /></span><span class="ab-label">เมูนเครื่องดื่ม</span>',
			'href' => 'admin.php?page=tlab_adminbar_drink',
			'parent' => 'tlab_adminbar_group'
		);
		$wp_admin_bar->add_node( $args );
	}


special thank : icon – [http://findicons.com/pack/2036/farm](http://findicons.com/pack/2036/farm)

Reference : [http://codex.wordpress.org/Function_Reference/add_menu](http://codex.wordpress.org/Function_Reference/add_menu)


