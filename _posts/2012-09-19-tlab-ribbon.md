---
layout: post
title: "tlab ribbon"
description: ""
category: 
tags: []
---
{% include JB/setup %}

#### source code

	<?php
		/*
		Plugin Name: TLab Ribbon
		Plugin URI: http://wp-plugin.ilmsg.com/tlab_ribbon
		Author: Eak Netpanya
		Author URI: http://www.ilmsg.com/about
		Description: ribbon to top right on website
		Version: 0.1
		Text Domain: ilmsg
		*/
		
		function tlab_ilmsg_ribbon(){	
			$img = plugins_url( 'ilmsg.com_ribbon_left.png', __FILE__ );
			echo '<img src="'.$img.'" style="position:fixed; top:0; left:0; z-index:100000; cursor:pointer;" />';
		}
		add_action('wp_footer', 'tlab_ilmsg_ribbon');	
	?>

<a href="http://ilmsg.com/wp-content/uploads/2012/03/ilmsg.com_ribbon_left.png"><img src="http://ilmsg.com/wp-content/uploads/2012/03/ilmsg.com_ribbon_left.png" alt="" title="ilmsg.com_ribbon_left" width="99" height="99" class="aligncenter size-full wp-image-713" /></a>
