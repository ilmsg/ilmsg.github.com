---
layout: post
title: "TLab Simple Widget"
description: ""
category: howto
tags: [wordpress plugin]
---
{% include JB/setup %}

### TLab Simple Widget

	<?php
	/*
	Plugin Name: TLab Simple Widget
	Plugin URI: http://wp-plugin.ilmsg.com/tlab_simple_widget
	Description: Simple extends Widget class
	Author: Eak Netpanya
	Version: 0.1
	Author URI: http://ilmsg.com
	*/
	
	class TlabWidget extends WP_Widget{
		
		// @constructor
		function TlabWidget(){
			$widgetOptions = array(
				'classname' => 'widget_tlab',
				'description' => 'TLab Widget Simple '
			);
			
			$controlOptions = array(
				'width' => '250',
				'height' => '250',
				'id_base' => 'tlabwidget-simple'
			);
			
			$this->WP_Widget('tlabwidget-simple','Tlab Widget', $widgetOptions, $controlOptions);
		}
		
		// handler for widget display
		function widget($args, $widgetInstance){
			extract($args);
			
			$title = apply_filters('widget_title',$widgetInstance['title']);
			
			echo $before_widget;
			if($title) echo $before_title.$title.$after_title;
			
			echo 'my form';
			
			echo $after_widget;
		}
		
		// form containing configuration
		function form($widgetInstance){
			$defaultConfigs = array('title' => 'This is My Title');
			$widgetInstance = wp_parse_args((array) $widgetInstance, $defaultConfigs);
	?>
	
			<p>
				<label for="<?php echo $this->get_field_id('title'); ?>">Title:</label>
				<input id="<?php echo $this->get_field_id('title'); ?>" name="<?php echo $this->get_field_name('title'); ?>" value="<?php echo $widgetInstance['title']; ?>" style="width:200px;" />
			</p>
	<?php
		}
		
		// handler for widget configuration update
		function update( $newInstance, $oldInstance){
			$instance = $old_instance;
			
			$instance['title'] = strip_tags(stripslashes($newInstance['title']));
			
			return $instance;
		}
		
	}
	
	function TlabWidget_Init(){
		register_widget('TlabWidget');
	}
	
	add_action('widgets_init', 'TlabWidget_Init');
	
	?>
