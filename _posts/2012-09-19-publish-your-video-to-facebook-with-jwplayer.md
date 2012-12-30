---
layout: post
title: "publish your video to facebook with jwplayer"
description: ""
category: 
tags: []
---
{% include JB/setup %}


http://www.longtailvideo.com/support/blog/19150/publish-your-videos-to-facebook-with-a-jw-player

### source code

	<script type='text/javascript' src='jwplayer.js'></script>
	
	<div id='mediaspace'>This text will be replaced</div>
	
	<script type='text/javascript'>
	  jwplayer('mediaspace').setup({
		'flashplayer': 'player.swf',
		'file': 'http://www.longtailvideo.com/jw/upload/bunny.mp3',
		'duration': '33',
		'controlbar': 'bottom',
		'width': '470',
		'height': '24'
	  });
	</script>
	
	