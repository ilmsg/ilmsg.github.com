---
layout: post
title: "add_filter for language_attributes"
description: ""
category: 
tags: []
---
{% include JB/setup %}

#### source code plugin

	function tlab_add_ns( $output ) {
	  $output .= ' xmlns:tl="' . esc_attr(TLAB_NS_URI) . '"';
	  return $output;
	}
	add_filter('language_attributes', 'tlab_add_ns');


#### html before

	<html dir="ltr" lang="th"
	 xmlns:og="http://opengraphprotocol.org/schema/"
	 xmlns:fb="http://www.facebook.com/2008/fbml">


#### html after

	<html dir="ltr" lang="th"
	 xmlns:og="http://opengraphprotocol.org/schema/"
	 xmlns:fb="http://www.facebook.com/2008/fbml" 
	 xmlns:og="http://opengraphprotocol.org/schema/">
	<head>
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	<title></title>
	</head>	
	<body>	
	</body></html>
