---
layout: post
title: "model ของ codeigniter สำหรับวัดค่า pagerank จาก google"
description: "model ของ codeigniter สำหรับวัดค่า pagerank จาก google"
category: snippet code
tags: [php, codeigniter, pagerank]
---
{% include JB/setup %}

โหลดโมเดล

	$this->load->model('googlepr_model');
	
การใช้งานโดเมลหลังจากที่โหลดมาแล้ว ตัวอย่างเป็นชื่อเว็บ ilmsg.com นะครับ

	$url = 'ilmsg.com';
	$pagerank = $this->googlepr_model->google_page_rank( $url );
	echo $pagerank;

ซอร์ดโค้ดของโมเดล googlepr_model.php


	<?php if ( ! defined('BASEPATH')) exit('No direct script access allowed');
	
	class Googlepr_model extends CI_Model {
	
		public function __construct(){
			parent::__construct();
		}
		 
		function google_page_rank($url) { // URL or domain name
			if (strlen(trim($url))>0) {                      
				$_url = (strrpos($url, "http://")) ? $url : 'http://'.$url;             
				$pagerank = trim($this->GooglePageRank($_url));
				if (empty($pagerank)) $pagerank = 0;
				return (int)($pagerank);
			}
			return 0;
		}
	 
		function GooglePageRank($url) {
			$fp = fsockopen("toolbarqueries.google.com", 80, $errno, $errstr, 30);
			if (!$fp) {
				echo "$errstr ($errno)<br />\n";
			}else{
				$out = "GET /tbr?client=navclient-auto&hl=en&ch=".$this->CheckHash($this->HashURL($url))."&ie=UTF-8&oe=UTF-8&features=Rank&q=info:".$url." HTTP/1.1\r\n";
				$out .= "Host: toolbarqueries.google.com\r\n";
				$out .= "User-Agent: Mozilla/4.0 (compatible; GoogleToolbar 2.0.114-big; Windows XP 5.1)\r\n";
				$out .= "Connection: Close\r\n\r\n";
				fwrite($fp, $out);
		 
				while (!feof($fp)) {
					$data = fgets($fp, 128);
					$pos = strpos($data, "Rank_");
				if($pos === false){} else{
						$pagerank = substr($data, $pos + 9);                    
					}
				}
				fclose($fp);
				return $pagerank;
			}
		}
	 
		function StrToNum($Str, $Check, $Magic) {
			$Int32Unit = 4294967296; // 2^32
			$length = strlen($Str);
			for ($i = 0; $i < $length; $i++) {
				$Check *= $Magic;
				if ($Check >= $Int32Unit) {
					$Check = ($Check - $Int32Unit * (int) ($Check / $Int32Unit));
					$Check = ($Check < -2147483648)? ($Check + $Int32Unit) : $Check;
				}
				$Check += ord($Str{$i});
			}
			return $Check;
		}
	 
		function HashURL($String) {
			$Check1 = $this->StrToNum($String, 0x1505, 0x21);
			$Check2 = $this->StrToNum($String, 0, 0x1003F);
			$Check1 >>= 2;
			$Check1 = (($Check1 >> 4) & 0x3FFFFC0 ) | ($Check1 & 0x3F);
			$Check1 = (($Check1 >> 4) & 0x3FFC00 ) | ($Check1 & 0x3FF);
			$Check1 = (($Check1 >> 4) & 0x3C000 ) | ($Check1 & 0x3FFF);
			$T1 = (((($Check1 & 0x3C0) << 4) | ($Check1 & 0x3C)) << 2 ) | ($Check2 & 0xF0F );
			$T2 = (((($Check1 & 0xFFFFC000) << 4) | ($Check1 & 0x3C00)) << 0xA) | ($Check2 & 0xF0F0000 );
			return ($T1 | $T2);
		}
	 
		function CheckHash($Hashnum) {
			$CheckByte = 0;
			$Flag = 0;
			$HashStr = sprintf('%u', $Hashnum) ;
			$length = strlen($HashStr);
			for ($i = $length - 1; $i >= 0; $i --) {
				$Re = $HashStr{$i};
				if (1 === ($Flag % 2)) {
					$Re += $Re;
					$Re = (int)($Re / 10) + ($Re % 10);
				}
				$CheckByte += $Re;
				$Flag ++;
			}
			$CheckByte %= 10;
			if (0!== $CheckByte) {
				$CheckByte = 10 - $CheckByte;
				if (1 === ($Flag % 2) ) {
					if (1 === ($CheckByte % 2)) {
						$CheckByte += 9;
					}
					$CheckByte >>= 1;
				}
			}
			return '7'.$CheckByte.$HashStr;
		}
		 
	}
	 
	/* End of file googlepr_model.php */
	/* Location: ./application/models/googlepr_model.php */

