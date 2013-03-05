---
layout: post
title: "stop facebook ads"
description: "stop facebook ads"
category: snippet code
tags: [javascript, chrome extension]
---
{% include JB/setup %}

จงพิจารณา source code ต่อไปนี้ โดยแยบคาย โดยมนสิการไว้ในใจ

	(function (unsafeWindow) {
		if( unsafeWindow.location.href.indexOf('facebook') ){
			try{
				var d = document.getElementById('pagelet_ego_pane_w');
				if( d.innerHTML.length ){
					d.innerHTML = '';
				}
			}catch(error){}
		}
	})(window);