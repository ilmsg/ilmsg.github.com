---
layout: post
title: "Facebook API อ่านโพสทั้งหมดของ app"
description: ""
category: facebook
tags: [app facebook]
---
{% include JB/setup %}

การใช้ facebook api อ่านโพสของ app (read_stream permission) ทุกอย่างที่ถูกโพสผ่านทาง app ตัวนั้นๆเอาออกมาแสดง

	
	<div id="feeddata"></div>

	function getFeed(){
		FB.api('/me/home?limit=120&filter=app_123456789012345', function(response) {
			if (!response || response.error) {
				 alert('Error occured');
			} else {
				var posts = response.data;
				var textpost='';
				for(post in posts){
					if( posts[post].type == 'link'){
						textpost += '<br><img src="'+posts[post].picture+'">' + '<a href="' + posts[post].link + '">' + posts[post].caption + '</a>';
					}
				}
				document.getElementById('feeddata').innerHTML = textpost;
				console.log(response);
			}
	   });
	}


limit ใส่ไว้ 120 เพราะว่าไม่ทำ paging เอาออกมา 120 พอ (มากกว่านี้สัก 99999 เครื่องอืด ค้าง แรมหมด )

filter จะกรองเอาเฉพาะ feed จาก app หมายเลข ID ของ app ก็แทนที่ด้วยตัว app_XXXXXXXXXXXXXXX


	FB.api('/me/home?limit=120&filter=app_XXXXXXXXXXXXXXX', function(response) { });


โค้ดที่ใช้งานจริง

	<!DOCTYPE html>
	<html xmlns="http://www.w3.org/1999/xhtml" xmlns:fb="http://www.facebook.com/2008/fbml">
	<head>
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
	<title></title>
	</head>
	<body>
	<div id="fb-root"></div>
	<fb:login-button autologoutlink="true" scope="email,publish_stream,read_stream"></fb:login-button>
	<div id="feeddata"></div>
	
	<script type="text/javascript">
		window.fbAsyncInit = function() {
			FB.init({appId: '382109201862946', status: true, cookie: true, xfbml: true});
				
			FB.getLoginStatus(function(response) {
				if (response.status === 'connected') {
					var uid = response.authResponse.userID;
					var accessToken = response.authResponse.accessToken;
					console.log('uid : ' + uid);
					console.log('accessToken : ' + accessToken);
					
					getFeed();
				} else if (response.status === 'not_authorized') {
					console.log('loged facebook but not auth app');	
				} else {	
					console.log('not login facebook');	
				}
			});
	
		};
		
		(function() {
			var e = document.createElement('script');
			e.type = 'text/javascript';
			e.src = document.location.protocol +
			'//connect.facebook.net/th_TH/all.js';
			e.async = true;
			document.getElementById('fb-root').appendChild(e);
		}());
	
		function getFeed(){
			FB.api('/me/home?limit=999&filter=app_180751008671144', function(response) {
				if (!response || response.error) {
					 alert('Error occured');
				} else {
					var posts = response.data;
					var textpost='';
					for(post in posts){
						//if( posts[post].type == 'link'){						
							textpost += '<br><img src="'+posts[post].picture+'">' + '<a href="' + posts[post].link + '">' + posts[post].caption + '</a>';
						//}
					}
					document.getElementById('feeddata').innerHTML = textpost;
					console.log(response);
				}
		   });
		}
	</script>
	</body></html>

