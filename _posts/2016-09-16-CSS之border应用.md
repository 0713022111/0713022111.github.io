---
title: CSS之border应用
description: CSS之border应用
date: 2016-09-16 20:58:21
categories:
 - CSS
tags:
 - CSS
 - border
---
## border-width属性定义及用法

在css中，border-width属性是用来设置元素上下左右边框的宽度，它其实是将上下左右[边框宽度](https://www.ggbiji.com/tag/边框宽度/)的四个属性定义在一个声明中，从而减少代码量。

**border-width属性可以有1-4个属性值**

1. 当有4个属性值时，分别表示：上边框宽度、右边框宽度、下边框宽度、左边框宽度；
2. 有3个属性值时，分别表示：上边框宽度、左右边框宽度、下边框宽度；
3. 有2个属性值时，分别表示：上下边框宽度、左右边框宽度；
4. 有1个属性值时，分别表示：上下左右边框宽度；

**如果要单独为元素的一边设置边框宽度，建议使用以下属性：**

- [border-top-width属性](https://www.ggbiji.com/border-top-width.html)：设置元素上边框宽度；
- [border-right-width属性](https://www.ggbiji.com/border-right-width.html)：设置元素右边框宽度；
- [border-bottom-width属性](https://www.ggbiji.com/border-bottom-width.html)：设置元素下边框宽度；
- [border-left-width属性](https://www.ggbiji.com/border-left-width.html)：设置元素左边框宽度；

## border-width属性语法格式

1. border-widt: 值1 值2 值3 值4;（如：border-widt: 10px 9px 8px 7px;）
2. border-widt: 值1 值2 值3;（如：border-widt: 10px 9px 8px;）
3. border-widt: 值1 值2;（如：border-widt: 10px 9px;）
4. border-widt: 值1;（如：border-widt: 10px;）

## border-width属性值说明

- thin：设置细的边框;
- medium：设置中等的边框;
- thick ：设置粗的边框;
- length：自定义边框的宽度;
- inherit：从父元素继承边框宽度;

### 例子  

**1、正方形**  
最终效果：

<div style="width:100px;height:100px;background:#22222222;margin:auto;"></div>

CSS代码如下：

```css
#square {
    width: 100px;
    height: 100px;
    background: #22222222;
}
```

**2、长方形**  
最终效果：  
<div style="width:200px;height:100px;background:#22222222;margin:auto;"></div>  

CSS代码如下：

```css
#rectangle {
 　width: 200px;
 　height: 100px;
 　background: #22222222;
}
```

**3、圆形**  
最终效果：

<div style="width:100px;height:100px;background:#22222222;-moz-border-radius: 50px;-webkit-border-radius: 50px;border-radius: 50px;margin:auto;"></div>

CSS代码如下：

```css
#circle {
    width: 100px;
    height: 100px;
    background: #22222222;
    -moz-border-radius: 50px;
    -webkit-border-radius: 50px;
    border-radius: 50px;
}
```

**4、椭圆**  
最终效果：  
<div style="width:200px;height:100px;background:#22222222;margin:auto;-moz-border-radius: 100px / 50px;-webkit-border-radius: 100px / 50px;border-radius: 100px / 50px;"></div>  
CSS代码如下：  
```css
#oval {
    width: 200px;
    height: 100px;
    background: #22222222;
    -moz-border-radius: 100px / 50px;
    -webkit-border-radius: 100px / 50px;
    border-radius: 100px / 50px;
}
```
**5、上三角**  
最终效果：  

<div style="width:0;height:0;border-left: 50px solid transparent;border-right: 50px solid transparent;border-bottom: 100px solid #22222222;margin:auto;"></div>   
CSS代码如下：  
```css
#triangle-up {
    width: 0;
    height: 0;
    border-left: 50px solid transparent;
    border-right: 50px solid transparent;
    border-bottom: 100px solid #22222222;
}
```
**6、下三角**  
最终效果：  
<div style="width:0;height:0;border-left: 50px solid transparent;border-right: 50px solid transparent;border-top: 100px solid #22222222;margin:auto;"></div>   
CSS代码如下：  
```css
#triangle-down {
    width: 0;
    height: 0;
    border-left: 50px solid transparent;
    border-right: 50px solid transparent;
    border-top: 100px solid #22222222;
}
```
**7、左三角**  
最终效果：  
<div style="width:0;height:0;border-top: 50px solid transparent;
    border-right: 100px solid #22222222;
    border-bottom: 50px solid transparent;margin:auto;"></div>   
CSS代码如下：  
```css
#triangle-left {
    width: 0;
    height: 0;
    border-top: 50px solid transparent;
    border-right: 100px solid #22222222;
    border-bottom: 50px solid transparent;
}
```
**8、右三角**  
最终效果：  
<div style="width:0;height:0;border-top: 50px solid transparent;
    border-left: 100px solid #22222222;
    border-bottom: 50px solid transparent;margin:auto;"></div>   
CSS代码如下：  
```css
#triangle-right {
    width: 0;
    height: 0;
    border-top: 50px solid transparent;
    border-left: 100px solid #22222222;
    border-bottom: 50px solid transparent;
}
```
**9、左上三角**  
最终效果：  

<div style="width:0;height:0;border-top: 100px solid #22222222;
    border-right: 100px solid transparent;margin:auto;"></div>   
CSS代码如下：  
```css
#triangle-topleft {
    width: 0;
    height: 0;
    border-top: 100px solid #22222222;
    border-right: 100px solid transparent;
}
```
**10、右上三角**  
最终效果：  
<div style="width:0;height:0;border-top: 100px solid #22222222;
    border-left: 100px solid transparent;margin:auto;"></div>   
CSS代码如下：  
```css
#triangle-topright {
    width: 0;
    height: 0;
    border-top: 100px solid #22222222;
    border-left: 100px solid transparent;
}
```
**11、左下三角**  
最终效果：  
<div style="width:0;height:0;border-bottom: 100px solid #22222222;
    border-right: 100px solid transparent;margin:auto;"></div>   
CSS代码如下：  
```css
#triangle-bottomleft {
    width: 0;
    height: 0;
    border-bottom: 100px solid #22222222;
    border-right: 100px solid transparent;
}
```
**12、右下三角**  
最终效果：  
<div style="width:0;height:0;border-bottom: 100px solid #22222222;
    border-left: 100px solid transparent;margin:auto;"></div>   
CSS代码如下：  
```css
#triangle-bottomright {
    width: 0;
    height: 0;
    border-bottom: 100px solid #22222222;
    border-left: 100px solid transparent;
}
```
**13、平行四边形**  
最终效果：  
<div style="width: 150px;
    height: 100px;
    margin-left:20px;
    -webkit-transform: skew(20deg);
    -moz-transform: skew(20deg);
    -o-transform: skew(20deg);
    background: #22222222;margin:auto;"></div>   
CSS代码如下：  
```css
#parallelogram {
    width: 150px;
    height: 100px;
    margin-left:20px;
    -webkit-transform: skew(20deg);
    -moz-transform: skew(20deg);
    -o-transform: skew(20deg);
    background: #22222222;
}
```
**14、梯形**  
最终效果：  

<div style="width: 100px;border-bottom: 100px solid #22222222;border-left: 50px solid transparent;border-right: 50px solid transparent;height: 0;margin:auto;"></div>   

CSS代码如下：  
```css
#trapezoid {
    border-bottom: 100px solid #22222222;
    border-left: 50px solid transparent;
    border-right: 50px solid transparent;
    height: 0;
    width: 100px;
}
```
**15、六角星**  
最终效果：  
<style>
#star-six {
    width: 0;
    height: 0;
    border-left: 50px solid transparent;
    border-right: 50px solid transparent;
    border-bottom: 100px solid #22222222;
    position: relative;
}
#star-six:after {
    width: 0;
    height: 0;
    border-left: 50px solid transparent;
    border-right: 50px solid transparent;
    border-top: 100px solid #22222222;
    position: absolute;
    content: "";
    top: 30px;
    left: -50px;
}
</style>
<div id="star-six" style="margin:auto;"></div>  
CSS代码如下：   
```css
#star-six {
    width: 0;
    height: 0;
    border-left: 50px solid transparent;
    border-right: 50px solid transparent;
    border-bottom: 100px solid #22222222;
    position: relative;
}
#star-six:after {
    width: 0;
    height: 0;
    border-left: 50px solid transparent;
    border-right: 50px solid transparent;
    border-top: 100px solid #22222222;
    position: absolute;
    content: "";
    top: 30px;
    left: -50px;
}
```
**16、五角星**   
最终效果：  
<style>
#star-five {
    margin: 50px 0;
    position: relative;
    display: block;
    color: #22222222;
    width: 0px;
    height: 0px;
    border-right: 100px solid transparent;
    border-bottom: 70px solid #22222222;
    border-left: 100px solid transparent;
    -moz-transform: rotate(35deg);
    -webkit-transform: rotate(35deg);
    -ms-transform: rotate(35deg);
    -o-transform: rotate(35deg);
}
#star-five:before {
    border-bottom: 80px solid #22222222;
    border-left: 23px solid transparent;
    border-right: 23px solid transparent;
    position: absolute;
    height: 0;
    width: 0;
    top: -60px;
    left: -65px;
    display: block;
    content: '';
    -webkit-transform: rotate(-35deg);
    -moz-transform: rotate(-35deg);
    -ms-transform: rotate(-35deg);
    -o-transform: rotate(-35deg);
}
#star-five:after {
    position: absolute;
    display: block;
    color: #22222222;
    top: 3px;
    left: -105px;
    width: 0px;
    height: 0px;
    border-right: 100px solid transparent;
    border-bottom: 70px solid #22222222;
    border-left: 100px solid transparent;
    -webkit-transform: rotate(-70deg);
    -moz-transform: rotate(-70deg);
    -ms-transform: rotate(-70deg);
    -o-transform: rotate(-70deg);
    content: '';
}
</style>
<div id="star-five" style="margin:auto;"></div>  
CSS代码如下：  
```css
#star-five {
    margin: 50px 0;
    position: relative;
    display: block;
    color: #22222222;
    width: 0px;
    height: 0px;
    border-right: 100px solid transparent;
    border-bottom: 70px solid #22222222;
    border-left: 100px solid transparent;
    -moz-transform: rotate(35deg);
    -webkit-transform: rotate(35deg);
    -ms-transform: rotate(35deg);
    -o-transform: rotate(35deg);
}
#star-five:before {
    border-bottom: 80px solid #22222222;
    border-left: 23px solid transparent;
    border-right: 23px solid transparent;
    position: absolute;
    height: 0;
    width: 0;
    top: -60px;
    left: -65px;
    display: block;
    content: '';
    -webkit-transform: rotate(-35deg);
    -moz-transform: rotate(-35deg);
    -ms-transform: rotate(-35deg);
    -o-transform: rotate(-35deg);
}
#star-five:after {
    position: absolute;
    display: block;
    color: #22222222;
    top: 3px;
    left: -105px;
    width: 0px;
    height: 0px;
    border-right: 100px solid transparent;
    border-bottom: 70px solid #22222222;
    border-left: 100px solid transparent;
    -webkit-transform: rotate(-70deg);
    -moz-transform: rotate(-70deg);
    -ms-transform: rotate(-70deg);
    -o-transform: rotate(-70deg);
    content: '';
}
```
**17、五角大楼**  
最终效果：  

<style>
#pentagon {
    position: relative;
    width: 54px;
    border-width: 50px 18px 0;
    border-style: solid;
    border-color: #22222222 transparent;
}
#pentagon:before {
    content: "";
    position: absolute;
    height: 0;
    width: 0;
    top: -85px;
    left: -18px;
    border-width: 0 45px 35px;
    border-style: solid;
    border-color: transparent transparent #22222222;
}
</style>
<div id="pentagon" style="margin:auto;"></div>

CSS代码如下：  
```css
#pentagon {
    position: relative;
    width: 54px;
    border-width: 50px 18px 0;
    border-style: solid;
    border-color: #22222222 transparent;
}
#pentagon:before {
    content: "";
    position: absolute;
    height: 0;
    width: 0;
    top: -85px;
    left: -18px;
    border-width: 0 45px 35px;
    border-style: solid;
    border-color: transparent transparent #22222222;
}
```
**18、六边形**  
最终效果：  
<style>
#hexagon {
    width: 100px;
    height: 55px;
    background: #22222222;
    position: relative;
}
#hexagon:before {
    content: "";
    position: absolute;
    top: -25px;
    left: 0;
    width: 0;
    height: 0;
    border-left: 50px solid transparent;
    border-right: 50px solid transparent;
    border-bottom: 25px solid #22222222;
}
#hexagon:after {
    content: "";
    position: absolute;
    bottom: -25px;
    left: 0;
    width: 0;
    height: 0;
    border-left: 50px solid transparent;
    border-right: 50px solid transparent;
    border-top: 25px solid #22222222;
}
</style>
<div id="hexagon" style="margin:auto;"></div>

CSS代码如下：  
```css
#hexagon {
    width: 100px;
    height: 55px;
    background: #22222222;
    position: relative;
}
#hexagon:before {
    content: "";
    position: absolute;
    top: -25px;
    left: 0;
    width: 0;
    height: 0;
    border-left: 50px solid transparent;
    border-right: 50px solid transparent;
    border-bottom: 25px solid #22222222;
}
#hexagon:after {
    content: "";
    position: absolute;
    bottom: -25px;
    left: 0;
    width: 0;
    height: 0;
    border-left: 50px solid transparent;
    border-right: 50px solid transparent;
    border-top: 25px solid #22222222;
}
```
**19、八角形**  
最终效果：  

<style>
 #octagon {
    width: 100px;
    height: 42px;
    background: #22222222;
    position: relative;
}
#octagon:before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    border-bottom: 29px solid #22222222;
    border-left: 29px solid transparent;
    border-right: 29px solid transparent;
    width: 42px;
    height: 0;
    top: -29px;
}
#octagon:after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    border-top: 29px solid #22222222;
    border-left: 29px solid transparent;
    border-right: 29px solid transparent;
    width: 42px;
    height: 0;
    top:42px;
}
</style>
<div id="octagon" style="margin:auto"></div>  

CSS代码如下：  
```css
 #octagon {
    width: 100px;
    height: 42px;
    background: #22222222;
    position: relative;
}
#octagon:before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    border-bottom: 29px solid #22222222;
    border-left: 29px solid transparent;
    border-right: 29px solid transparent;
    width: 42px;
    height: 0;
    top: -29px;
}
#octagon:after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    border-top: 29px solid #22222222;
    border-left: 29px solid transparent;
    border-right: 29px solid transparent;
    width: 42px;
    height: 0;
    top:42px;
}
```
**20、爱心**  
最终效果：  
<style>
#heart {
    position: relative;
    width: 100px;
    height: 90px;
}
#heart:before,
#heart:after {
    position: absolute;
    content: "";
    left: 50px;
    top: 0;
    width: 50px;
    height: 80px;
    background: #22222222;
    -moz-border-radius: 50px 50px 0 0;
    border-radius: 50px 50px 0 0;
    -webkit-transform: rotate(-45deg);
    -moz-transform: rotate(-45deg);
    -ms-transform: rotate(-45deg);
    -o-transform: rotate(-45deg);
    transform: rotate(-45deg);
    -webkit-transform-origin: 0 100%;
    -moz-transform-origin: 0 100%;
    -ms-transform-origin: 0 100%;
    -o-transform-origin: 0 100%;
    transform-origin: 0 100%;
}
#heart:after {
    left: 0;
    -webkit-transform: rotate(45deg);
    -moz-transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    -o-transform: rotate(45deg);
    transform: rotate(45deg);
    -webkit-transform-origin: 100% 100%;
    -moz-transform-origin: 100% 100%;
    -ms-transform-origin: 100% 100%;
    -o-transform-origin: 100% 100%;
    transform-origin :100% 100%;
}
</style>
<div id="heart" style="margin:auto"></div>  
CSS代码如下：  
```css
#heart {
    position: relative;
    width: 100px;
    height: 90px;
}
#heart:before,
#heart:after {
    position: absolute;
    content: "";
    left: 50px;
    top: 0;
    width: 50px;
    height: 80px;
    background: #22222222;
    -moz-border-radius: 50px 50px 0 0;
    border-radius: 50px 50px 0 0;
    -webkit-transform: rotate(-45deg);
    -moz-transform: rotate(-45deg);
    -ms-transform: rotate(-45deg);
    -o-transform: rotate(-45deg);
    transform: rotate(-45deg);
    -webkit-transform-origin: 0 100%;
    -moz-transform-origin: 0 100%;
    -ms-transform-origin: 0 100%;
    -o-transform-origin: 0 100%;
    transform-origin: 0 100%;
}
#heart:after {
    left: 0;
    -webkit-transform: rotate(45deg);
    -moz-transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    -o-transform: rotate(45deg);
    transform: rotate(45deg);
    -webkit-transform-origin: 100% 100%;
    -moz-transform-origin: 100% 100%;
    -ms-transform-origin: 100% 100%;
    -o-transform-origin: 100% 100%;
    transform-origin :100% 100%;
}
```
**21、无穷大符号**  
最终效果：  
<style>
#infinity {
    position: relative;
    width: 212px;
    height: 100px;
}
#infinity:before,
#infinity:after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 60px;
    height: 60px;
    border: 20px solid #22222222;
    -moz-border-radius: 50px 50px 0 50px;
    border-radius: 50px 50px 0 50px;
    -webkit-transform: rotate(-45deg);
    -moz-transform: rotate(-45deg);
    -ms-transform: rotate(-45deg);
    -o-transform: rotate(-45deg);
    transform: rotate(-45deg);
}
#infinity:after {
    left: auto;
    right: 0;
    -moz-border-radius: 50px 50px 50px 0;
    border-radius: 50px 50px 50px 0;
    -webkit-transform: rotate(45deg);
    -moz-transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    -o-transform: rotate(45deg);
    transform: rotate(45deg);
}
</style>
<div id="infinity" style="margin:auto;"></div>  
CSS代码如下：  
```css
#infinity {
    position: relative;
    width: 212px;
    height: 100px;
}
#infinity:before,
#infinity:after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 60px;
    height: 60px;
    border: 20px solid #22222222;
    -moz-border-radius: 50px 50px 0 50px;
    border-radius: 50px 50px 0 50px;
    -webkit-transform: rotate(-45deg);
    -moz-transform: rotate(-45deg);
    -ms-transform: rotate(-45deg);
    -o-transform: rotate(-45deg);
    transform: rotate(-45deg);
}
#infinity:after {
    left: auto;
    right: 0;
    -moz-border-radius: 50px 50px 50px 0;
    border-radius: 50px 50px 50px 0;
    -webkit-transform: rotate(45deg);
    -moz-transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    -o-transform: rotate(45deg);
    transform: rotate(45deg);
}
```
**22、鸡蛋**  
最终效果  
<style>
#egg {
    display:block;
    width: 126px;
    height: 180px;
    background-color: #22222222;
    -webkit-border-radius: 63px 63px 63px 63px / 108px 108px 72px 72px;
    border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
}
</style>
<div id="egg" style="margin:auto;"></div>  
CSS代码如下：  
```css
#egg {
    display:block;
    width: 126px;
    height: 180px;
    background-color: #22222222;
    -webkit-border-radius: 63px 63px 63px 63px / 108px 108px 72px 72px;
    border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
}
```
**23、食逗人（Pac-Man）**  
最终效果：  
<style>
#pacman {
    width: 0px;
    height: 0px;
    border-right: 60px solid transparent;
    border-top: 60px solid #22222222;
    border-left: 60px solid #22222222;
    border-bottom: 60px solid #22222222;
    border-top-left-radius: 60px;
    border-top-right-radius: 60px;
    border-bottom-left-radius: 60px;
    border-bottom-right-radius: 60px;
</style>
<div id="pacman" style="margin:auto;"></div>  
CSS代码如下：  
```css
#pacman {
    width: 0px;
    height: 0px;
    border-right: 60px solid transparent;
    border-top: 60px solid #22222222;
    border-left: 60px solid #22222222;
    border-bottom: 60px solid #22222222;
    border-top-left-radius: 60px;
    border-top-right-radius: 60px;
    border-bottom-left-radius: 60px;
    border-bottom-right-radius: 60px;
}
```
**24、提示对话框**  
最终效果：  
<style>
#talkbubble {
    width: 120px;
    height: 80px;
    background: #22222222;
    position: relative;
    -moz-border-radius: 10px;
    -webkit-border-radius: 10px;
    border-radius: 10px;
}
#talkbubble:before {
    content:"";
    position: absolute;
    right: 100%;
    top: 26px;
    width: 0;
    height: 0;
    border-top: 13px solid transparent;
    border-right: 26px solid #22222222;
    border-bottom: 13px solid transparent;
}
</style>
<div id="talkbubble" style="margin:auto;"></div>  
CSS代码如下：  
```css
#talkbubble {
    width: 120px;
    height: 80px;
    background: #22222222;
    position: relative;
    -moz-border-radius: 10px;
    -webkit-border-radius: 10px;
    border-radius: 10px;
}
#talkbubble:before {
    content:"";
    position: absolute;
    right: 100%;
    top: 26px;
    width: 0;
    height: 0;
    border-top: 13px solid transparent;
    border-right: 26px solid #22222222;
    border-bottom: 13px solid transparent;
}
```
**25、12角星**  
最终效果：  
<style>
#burst-12 {
    background: #22222222;
    width: 80px;
    height: 80px;
    position: relative;
    text-align: center;
}
#burst-12:before, #burst-12:after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    height: 80px;
    width: 80px;
    background: #22222222;
}
#burst-12:before {
    -webkit-transform: rotate(30deg);
    -moz-transform: rotate(30deg);
    -ms-transform: rotate(30deg);
    -o-transform: rotate(30deg);
    transform: rotate(30deg);
}
#burst-12:after {
    -webkit-transform: rotate(60deg);
    -moz-transform: rotate(60deg);
    -ms-transform: rotate(60deg);
    -o-transform: rotate(60deg);
    transform: rotate(60deg);
}
</style>
<div id="burst-12" style="margin:auto;"></div>  
CSS代码如下：  
```css
#burst-12 {
    background: #22222222;
    width: 80px;
    height: 80px;
    position: relative;
    text-align: center;
}
#burst-12:before, #burst-12:after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    height: 80px;
    width: 80px;
    background: #22222222;
}
#burst-12:before {
    -webkit-transform: rotate(30deg);
    -moz-transform: rotate(30deg);
    -ms-transform: rotate(30deg);
    -o-transform: rotate(30deg);
    transform: rotate(30deg);
}
#burst-12:after {
    -webkit-transform: rotate(60deg);
    -moz-transform: rotate(60deg);
    -ms-transform: rotate(60deg);
    -o-transform: rotate(60deg);
    transform: rotate(60deg);
}
```
**26、8角星**  
最终效果：  
<style>
#burst-8 {
    background: #22222222;
    width: 80px;
    height: 80px;
    position: relative;
    text-align: center;
    -webkit-transform: rotate(20deg);
    -moz-transform: rotate(20deg);
    -ms-transform: rotate(20deg);
    -o-transform: rotate(20eg);
    transform: rotate(20deg);
}
#burst-8:before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    height: 80px;
    width: 80px;
    background: #22222222;
    -webkit-transform: rotate(135deg);
    -moz-transform: rotate(135deg);
    -ms-transform: rotate(135deg);
    -o-transform: rotate(135deg);
    transform: rotate(135deg);
}
</style>
<div id="burst-8" style="margin:auto;"></div>  
CSS代码如下：  
```css
#burst-8 {
    background: #22222222;
    width: 80px;
    height: 80px;
    position: relative;
    text-align: center;
    -webkit-transform: rotate(20deg);
    -moz-transform: rotate(20deg);
    -ms-transform: rotate(20deg);
    -o-transform: rotate(20eg);
    transform: rotate(20deg);
}
#burst-8:before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    height: 80px;
    width: 80px;
    background: #22222222;
    -webkit-transform: rotate(135deg);
    -moz-transform: rotate(135deg);
    -ms-transform: rotate(135deg);
    -o-transform: rotate(135deg);
    transform: rotate(135deg);
}
```
**27、钻石**  
最终效果：  
<style>
#cut-diamond {
    border-style: solid;
    border-color: transparent transparent #22222222 transparent;
    border-width: 0 25px 25px 25px;
    height: 0;
    width: 50px;
    position: relative;
    margin: 20px 0 50px 0;
}
#cut-diamond:after {
    content: "";
    position: absolute;
    top: 25px;
    left: -25px;
    width: 0;
    height: 0;
    border-style: solid;
    border-color: #22222222 transparent transparent transparent;
    border-width: 70px 50px 0 50px;
}
</style>
<div id="cut-diamond" style="margin:auto;"></div>
<div style="margin-bottom: 70px;"></div>  
CSS代码如下：  
```css
#cut-diamond {
    border-style: solid;
    border-color: transparent transparent #22222222 transparent;
    border-width: 0 25px 25px 25px;
    height: 0;
    width: 50px;
    position: relative;
    margin: 20px 0 50px 0;
}
#cut-diamond:after {
    content: "";
    position: absolute;
    top: 25px;
    left: -25px;
    width: 0;
    height: 0;
    border-style: solid;
    border-color: #22222222 transparent transparent transparent;
    border-width: 70px 50px 0 50px;
}
```
**28、阴阳八卦（霸气的这个）**  
<style>
#yin-yang {
    width: 96px;
    height: 48px;
    background: #eee;
    border-color: #22222222;
    border-style: solid;
    border-width: 2px 2px 50px 2px;
    border-radius: 100%;
    position: relative;
} 
#yin-yang:before {
    content: "";
    position: absolute;
    top: 50%;
    left: 0;
    background: #eee;
    border: 18px solid #22222222;
    border-radius: 100%;
    width: 12px;
    height: 12px;
} 
#yin-yang:after {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    background: #22222222;
    border: 18px solid #eee;
    border-radius:100%;
    width: 12px;
    height: 12px;
}
</style>
<div id="yin-yang" style="margin:auto;"></div>  
CSS代码如下：  
```css
#yin-yang {
    width: 96px;
    height: 48px;
    background: #eee;
    border-color: #22222222;
    border-style: solid;
    border-width: 2px 2px 50px 2px;
    border-radius: 100%;
    position: relative;
} 
#yin-yang:before {
    content: "";
    position: absolute;
    top: 50%;
    left: 0;
    background: #eee;
    border: 18px solid #22222222;
    border-radius: 100%;
    width: 12px;
    height: 12px;
} 
#yin-yang:after {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    background: #22222222;
    border: 18px solid #eee;
    border-radius:100%;
    width: 12px;
    height: 12px;
}
```

<div style="position: relative;left: 80px;width: 0;height: 0;border-style: solid;border-width: 0 0 10px 10px;border-color: transparent transparent #00aaff transparent;"></div>