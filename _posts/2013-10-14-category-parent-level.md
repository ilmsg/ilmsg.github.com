---
layout: post
title: "การสร้างหมวดหมู่ย่อยซ้อนกันได้ไม่จำกัด"
description: "การสร้างหมวดหมู่ย่อยซ้อนกันได้ไม่จำกัด"
category: howto
tags: [database design]
---
{% include JB/setup %}

model ชื่อ getCategoryDropDown

  public function getCategoryDropDown( $parent = 0, $cate = array(), $level = 0){
		$categories = $this->db->get_where('category', array('category_parent' => $parent ) )->result();
		foreach( $categories as $key => $category ):
			$cate[ $category->category_id ] = repeater( "&nbsp;&nbsp;", $level ) . $category->category_title;
			if( $this->hasCategoryParent( $category->category_id ) ){				
				$cate = array_merge( $cate, $this->getCategoryDropDown( $category->category_id, $cate, ($level + 1) ) );
			}
		endforeach;
		return $cate;
	}

model ชื่อ hasCategoryParent
	
	public function hasCategoryParent( $parent = 0 ){
		if( $parent ){
			return $this->db->get_where('category', array( 'category_parent' => $parent ))->num_rows();
		}else{
			return false;
		}
	}

![Pic1](https://raw.github.com/ilmsg/ilmsg.github.com/master/_upload/category-parent-level1.png)


  $cat = $this->main_model->getCategoryDropDown();
  
	print "<pre>";
	print_r( $cat );
	print "</pre>";
	
  echo form_dropdown('cat', $cat, '' );
  
