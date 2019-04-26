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
    border-left: 30px solid transparent;
    border-right: 30px solid transparent;
    position: absolute;
    height: 0;
    width: 0;
    top: -45px;
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
    border-left: 30px solid transparent;
    border-right: 30px solid transparent;
    position: absolute;
    height: 0;
    width: 0;
    top: -45px;
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
    height: 100px;
    background: #22222222;
    position: relative;
}
#octagon:before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    border-bottom: 29px solid #22222222;
    border-left: 29px solid #eee;
    border-right: 29px solid #eee;
    width: 42px;
    height: 0;
}
#octagon:after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    border-top: 29px solid #22222222;
    border-left: 29px solid #eee;
    border-right: 29px solid #eee;
    width: 42px;
    height: 0;
}
</style>
<div id="octagon" style="margin:auto"></div>  

CSS代码如下：  
```css
 #octagon {
    width: 100px;
    height: 100px;
    background: #22222222;
    position: relative;
}
#octagon:before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    border-bottom: 29px solid #22222222;
    border-left: 29px solid #eee;
    border-right: 29px solid #eee;
    width: 42px;
    height: 0;
}
#octagon:after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    border-top: 29px solid #22222222;
    border-left: 29px solid #eee;
    border-right: 29px solid #eee;
    width: 42px;
    height: 0;
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

最终效果：![CSS画图 <wbr>强悍 <wbr>各种图形 <wbr>果断分享](https://images.cnblogs.com/cnblogs_com/sxwgf/201201/201201170833222469.png)
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
![CSS画图 <wbr>强悍 <wbr>各种图形 <wbr>果断分享](https://images.cnblogs.com/cnblogs_com/sxwgf/201201/201201170833226024.png)
CSS代码如下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #talkbubble {
 2     width: 120px;
 3     height: 80px;
 4     background: #22222222;
 5     position: relative;
 6     -moz-border-radius: 10px;
 7     -webkit-border-radius: 10px;
 8     border-radius: 10px;
 9 }
10 #talkbubble:before {
11     content:"";
12     position: absolute;
13     right: 100%;
14     top: 26px;
15     width: 0;
16     height: 0;
17     border-top: 13px solid transparent;
18     border-right: 26px solid #22222222;
19     border-bottom: 13px solid transparent;
20 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

**25、12角星**

最终效果：
![CSS画图 <wbr>强悍 <wbr>各种图形 <wbr>果断分享](https://images.cnblogs.com/cnblogs_com/sxwgf/201201/201201170833233799.png)
CSS代码如下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #burst-12 {
 2     background: #22222222;
 3     width: 80px;
 4     height: 80px;
 5     position: relative;
 6     text-align: center;
 7 }
 8 #burst-12:before, #burst-12:after {
 9     content: "";
10     position: absolute;
11     top: 0;
12     left: 0;
13     height: 80px;
14     width: 80px;
15     background: #22222222;
16 }
17 #burst-12:before {
18     -webkit-transform: rotate(30deg);
19     -moz-transform: rotate(30deg);
20     -ms-transform: rotate(30deg);
21     -o-transform: rotate(30deg);
22     transform: rotate(30deg);
23 }
24 #burst-12:after {
25     -webkit-transform: rotate(60deg);
26     -moz-transform: rotate(60deg);
27     -ms-transform: rotate(60deg);
28     -o-transform: rotate(60deg);
29     transform: rotate(60deg);
30 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

**26、8角星**
最终效果：
![CSS画图 <wbr>强悍 <wbr>各种图形 <wbr>果断分享](https://images.cnblogs.com/cnblogs_com/sxwgf/201201/20120117083323385.png)
CSS代码如下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #burst-8 {
 2     background: #22222222;
 3     width: 80px;
 4     height: 80px;
 5     position: relative;
 6     text-align: center;
 7     -webkit-transform: rotate(20deg);
 8     -moz-transform: rotate(20deg);
 9     -ms-transform: rotate(20deg);
10     -o-transform: rotate(20eg);
11     transform: rotate(20deg);
12 }
13 #burst-8:before {
14     content: "";
15     position: absolute;
16     top: 0;
17     left: 0;
18     height: 80px;
19     width: 80px;
20     background: #22222222;
21     -webkit-transform: rotate(135deg);
22     -moz-transform: rotate(135deg);
23     -ms-transform: rotate(135deg);
24     -o-transform: rotate(135deg);
25     transform: rotate(135deg);
26 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

**27、钻石**

最终效果：
![CSS画图 <wbr>强悍 <wbr>各种图形 <wbr>果断分享](https://images.cnblogs.com/cnblogs_com/sxwgf/201201/201201170833242304.png)
CSS代码如下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #cut-diamond {
 2     border-style: solid;
 3     border-color: transparent transparent #22222222 transparent;
 4     border-width: 0 25px 25px 25px;
 5     height: 0;
 6     width: 50px;
 7     position: relative;
 8     margin: 20px 0 50px 0;
 9 }
10 #cut-diamond:after {
11     content: "";
12     position: absolute;
13     top: 25px;
14     left: -25px;
15     width: 0;
16     height: 0;
17     border-style: solid;
18     border-color: #22222222 transparent transparent transparent;
19     border-width: 70px 50px 0 50px;
20 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

**28、阴阳八卦（霸气的这个）**

![CSS画图 <wbr>强悍 <wbr>各种图形 <wbr>果断分享](https://images.cnblogs.com/cnblogs_com/sxwgf/201201/201201170833247255.png)
CSS代码如下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #yin-yang {
 2     width: 96px;
 3     height: 48px;
 4     background: #eee;
 5     border-color: #22222222;
 6     border-style: solid;
 7     border-width: 2px 2px 50px 2px;
 8     border-radius: 100%;
 9     position: relative;
10 }
11 
12 #yin-yang:before {
13     content: "";
14     position: absolute;
15     top: 50%;
16     left: 0;
17     background: #eee;
18     border: 18px solid #22222222;
19     border-radius: 100%;
20     width: 12px;
21     height: 12px;
22 }
23 
24 #yin-yang:after {
25     content: "";
26     position: absolute;
27     top: 50%;
28     left: 50%;
29     background: #22222222;
30     border: 18px solid #eee;
31     border-radius:100%;
32     width: 12px;
33     height: 12px;
34 }
```

<div style="position: relative;left: 80px;width: 0;height: 0;border-style: solid;border-width: 0 0 10px 10px;border-color: transparent transparent #00aaff transparent;"></div>