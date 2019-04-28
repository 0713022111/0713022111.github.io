---
title: CSS之border演示
description: CSS之border演示
date: 2016-09-17 20:38:16
categories:
 - CSS
tags:
 - CSS
 - border
---

  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
	<head>
		<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
		<title>border-Css3</title>
		<link href="http://liyufeng.angton.com/css3-style2.css" rel="stylesheet" type="text/css" />
		<link href="http://liyufeng.angton.com/slider.css" rel="stylesheet" type="text/css" />
		<link rel="stylesheet" type="text/css" href="http://liyufeng.angton.com/normalize.css" />
		<link rel="stylesheet" type="text/css" href="http://liyufeng.angton.com/jquery.classycolor.css" />
		<script type="text/javascript" src="http://liyufeng.angton.com/slider.min.js"></script>
		<script src="http://liyufeng.angton.com/jquery-2.1.1.min.js"></script>
		<script src="http://liyufeng.angton.com/jquery.classycolor.js"></script>
	</head>
	<body>
	<div class="action-container">
		<form id="form1" name="form1" method="post" action="">
			<h2 class="toptit">效果设置区</h2>
			<div class="action-properties" id="shadow-container1">
				<h3>元素宽高设置</h3>
				<div class="property-container">
					<label cless="label">宽：</label>
					<input name="textfield" type="text" class="fd_slider_cn_halfSize fd_tween fd_tween fd_slider_cb_update_Borders.showBorder fd_range_0_10 fd_slider_cn_theSlider" id="bwidth" value="2" maxlength="3" />
					<select name="" id="width-units" onchange="Borders.showBorder();">
						<option selected="selected">em</option>
						<option>px</option>
					</select>
				</div>
				<div class="property-container">
					<label cless="label">高：</label>
					<input name="textfield" type="text" class="fd_slider_cn_halfSize fd_tween fd_tween fd_slider_cb_update_Borders.showBorder fd_range_0_10 fd_slider_cn_theSlider" id="bheight" value="2" maxlength="3" />
					<select name="" id="height-units" onchange="Borders.showBorder();">
						<option selected="selected">em</option>
						<option>px</option>
					</select>
				</div>
			</div>
			<div class="action-properties" id="shadow-container1">
				<h3>四边框分别设置</h3>
				<div class="property-container">
					<label cless="label">上：</label>
					<div class="color-box">
						<div class="classypicker1" onchange="Borders.showBorder();"></div>
					</div>
					<input name="textfield" type="text" class="fd_slider_cn_halfSize fd_tween fd_tween fd_slider_cb_update_Borders.showBorder fd_range_0_10 fd_slider_cn_theSlider" id="btop" value="2" maxlength="3" onchange="Borders.showBorder();"/>
					<select name="" id="top-units" onchange="Borders.showBorder();">
						<option selected="selected">em</option>
						<option>px</option>
					</select>	
				</div>
				<div class="property-container">
					<label cless="label">右：</label>
					<div class="color-box">
						<div class="classypicker2"></div>
					</div>
					<input name="textfield" type="text" class="fd_slider_cn_halfSize fd_tween fd_tween fd_slider_cb_update_Borders.showBorder fd_range_0_10 fd_slider_cn_theSlider" id="bright" value="2" maxlength="3" />
					<select name=""  id="right-units" onchange="Borders.showBorder();">
						<option selected="selected">em</option>
						<option>px</option>      
					</select>
				</div>
				<div class="property-container">
					<label cless="label">下：</label>
					<div class="color-box">
						<div class="classypicker3"></div>
					</div>
					<input name="textfield" type="text" class="fd_slider_cn_halfSize fd_tween fd_tween fd_slider_cb_update_Borders.showBorder fd_range_0_10 fd_slider_cn_theSlider" id="bbottom" onchange="BoxShadow.showShadow();" value="2" maxlength="3" />
					<select name="" id="bottom-units" onchange="Borders.showBorder();">
						<option selected="selected">em</option>
						<option>px</option>
					</select>
				</div>
				<div class="property-container">
					<label cless="label">左：</label>
					<div class="color-box">
						<div class="classypicker4"></div>
					</div>
					<input name="textfield" type="text" class="fd_slider_cn_halfSize fd_tween fd_tween fd_slider_cb_update_Borders.showBorder fd_range_0_10 fd_slider_cn_theSlider" id="bleft" onchange="BoxShadow.showShadow();" value="2" maxlength="3" />
					<select name="" id="left-units" onchange="Borders.showBorder();">
						<option selected="selected">em</option>
						<option>px</option>
					</select>
				</div>
			</div>		
			<div class="action-properties" id="shadow-container1">
				<h3>四角分别设置</h3>
				<div class="property-container">
					<label cless="label">左上圆角半径：</label>
					<input name="textfield" type="text" class="fd_slider_cn_halfSize fd_tween fd_tween fd_slider_cb_update_Borders.showBorder fd_range_0_10 fd_slider_cn_theSlider" id="top-left" value="2" maxlength="3" />
					<select name="" id="top-left-units" onchange="Borders.showBorder();">
						<option selected="selected">em</option>
						<option>px</option>
					</select>
				</div>
				<div class="property-container">
					<label cless="label">右上圆角半径：</label>
					<input name="textfield" type="text" class="fd_slider_cn_halfSize fd_tween fd_tween fd_slider_cb_update_Borders.showBorder fd_range_0_10 fd_slider_cn_theSlider" id="top-right" value="2" maxlength="3" />
					<select name=""  id="top-right-units" onchange="Borders.showBorder();">
						<option selected="selected">em</option>
						<option>px</option>         
					</select>
				</div>
				<div class="property-container">
					<label cless="label">左下圆角半径：</label>
					<input name="textfield" type="text" class="fd_slider_cn_halfSize fd_tween fd_tween fd_slider_cb_update_Borders.showBorder fd_range_0_10 fd_slider_cn_theSlider" id="bottom-left" onchange="BoxShadow.showShadow();" value="2" maxlength="3" />
					<select name="" id="bottom-left-units" onchange="Borders.showBorder();">
						<option selected="selected">em</option>
						<option>px</option>
					</select>
				</div>
				<div class="property-container">
					<label cless="label">右下圆角半径：</label>
					<input name="textfield" type="text" class="fd_slider_cn_halfSize fd_tween fd_tween fd_slider_cb_update_Borders.showBorder fd_range_0_10 fd_slider_cn_theSlider" id="bottom-right" onchange="BoxShadow.showShadow();" value="2" maxlength="3" />
					<select name="" id="bottom-right-units" onchange="Borders.showBorder();">
						<option selected="selected">em</option>
						<option>px</option>
					</select>
				</div>
			</div>
		</form>
	</div>
	<div class="Preview-container">
		<h2 class="toptit">效果展示区</h2>
		<div style="height: 400px;">
			<div id="demo-border"></div>
		</div>
		<h2 class="toptit">CSS</h2>
		<div id="code2"></div>
	</div>
	<script>
		$(function(){
			$('.classypicker1').ClassyColor({
					color: '#ff5900a8',
					colorSpace: 'rgba',
					labels: true,
					displayColor: 'hex'
			});			
			$('.classypicker2').ClassyColor({
					color: '#bbbf36',
					// colorSpace: 'rgb',
					colorSpace: 'rgba',
					labels: true,
					displayColor: 'hex'
			});
			$('.classypicker3').ClassyColor({
					color: '#365cbf',
					colorSpace: 'rgba',
					// colorSpace: 'hsla',
					labels: true,
					displayColor: 'hex'
					// displayColor: 'css'
			});
			$('.classypicker4').ClassyColor({
					color: '#36bf5e',
					colorSpace: 'rgba',
					// colorSpace: 'hsl',
					labels: true,
					displayColor: 'hex'
			});
			var tcolor = "#ff5900a8";
			var rcolor = "#bbbf36";
			var bcolor = "#365cbf";
			var lcolor = "#36bf5e";
			$(".classypicker1").on('newcolor',function(){			
				var selectColor1 = $(".classypicker1 .output-wrapper").html();
				console.log(selectColor1);
				$("#demo-border").css({'border-top-color':selectColor1});
				var top_html = $("#code2").html();
				top_html = top_html.replace(new RegExp(tcolor,"gm"),selectColor1);
				tcolor = selectColor1;
				$("#code2").html(top_html);
			});
			$(".classypicker2").on('newcolor',function(){
				var selectColor2 = $(".classypicker2 .output-wrapper").html();
				$("#demo-border").css({'border-right-color':selectColor2});
				var right_html = $("#code2").html();
				right_html = right_html.replace(new RegExp(rcolor,"gm"),selectColor2);
				rcolor = selectColor2;
				$("#code2").html(right_html);
			});
			$(".classypicker3").on('newcolor',function(){
				var selectColor3 = $(".classypicker3 .output-wrapper").html();
				$("#demo-border").css({'border-bottom-color':selectColor3});
				var bottom_html = $("#code2").html();
				bottom_html = bottom_html.replace(new RegExp(bcolor,"gm"),selectColor3);
				bcolor = selectColor3;
				$("#code2").html(bottom_html);
			});
			$(".classypicker4").on('newcolor',function(){
				var selectColor4 = $(".classypicker4 .output-wrapper").html();
				$("#demo-border").css({'border-left-color':selectColor4});
				var left_html = $("#code2").html();
				left_html = left_html.replace(new RegExp(lcolor,"gm"),selectColor4);
				lcolor = selectColor4;
				$("#code2").html(left_html);
			});			
		});	
	</script>
	<script type="text/javascript" src="http://liyufeng.angton.com/Border.js"></script>
	</body>
</html>