---
layout: post
title: "wordpress get thumbnail url"
description: ""
category: 
tags: []
---
{% include JB/setup %}

WordPress tip: Get thumbnail url
Posted: 15 Mar 2012 11:24 AM PDT
Simply paste the following code on your theme file, within the loop.

#### source code

	<?php
		$image_id = get_post_thumbnail_id();
		$image_url = wp_get_attachment_image_src($image_id);
		$image_url = $image_url[0];
	?>