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
<div style="border-bottom: 100px solid #22222222;
    border-left: 50px solid transparent;
    border-right: 50px solid transparent;
    height: 0;
    width: 100px;margin:auto;"></div>   
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
![CSS画图 <wbr>强悍 <wbr>各种图形 <wbr>果断分享](https://images.cnblogs.com/cnblogs_com/sxwgf/201201/20120117083319815.png)
CSS代码如下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #star-five {
 2     margin: 50px 0;
 3     position: relative;
 4     display: block;
 5     color: #22222222;
 6     width: 0px;
 7     height: 0px;
 8     border-right: 100px solid transparent;
 9     border-bottom: 70px solid #22222222;
10     border-left: 100px solid transparent;
11     -moz-transform: rotate(35deg);
12     -webkit-transform: rotate(35deg);
13     -ms-transform: rotate(35deg);
14     -o-transform: rotate(35deg);
15 }
16 #star-five:before {
17     border-bottom: 80px solid #22222222;
18     border-left: 30px solid transparent;
19     border-right: 30px solid transparent;
20     position: absolute;
21     height: 0;
22     width: 0;
23     top: -45px;
24     left: -65px;
25     display: block;
26     content: '';
27     -webkit-transform: rotate(-35deg);
28     -moz-transform: rotate(-35deg);
29     -ms-transform: rotate(-35deg);
30     -o-transform: rotate(-35deg);
31 
32 }
33 #star-five:after {
34     position: absolute;
35     display: block;
36     color: #22222222;
37     top: 3px;
38     left: -105px;
39     width: 0px;
40     height: 0px;
41     border-right: 100px solid transparent;
42     border-bottom: 70px solid #22222222;
43     border-left: 100px solid transparent;
44     -webkit-transform: rotate(-70deg);
45     -moz-transform: rotate(-70deg);
46     -ms-transform: rotate(-70deg);
47     -o-transform: rotate(-70deg);
48     content: '';
49 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

**17、五角大楼**
最终效果：
![CSS画图 <wbr>强悍 <wbr>各种图形 <wbr>果断分享](https://images.cnblogs.com/cnblogs_com/sxwgf/201201/20120117083320782.png)
CSS代码如下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #pentagon {
 2     position: relative;
 3     width: 54px;
 4     border-width: 50px 18px 0;
 5     border-style: solid;
 6     border-color: #22222222 transparent;
 7 }
 8 #pentagon:before {
 9     content: "";
10     position: absolute;
11     height: 0;
12     width: 0;
13     top: -85px;
14     left: -18px;
15     border-width: 0 45px 35px;
16     border-style: solid;
17     border-color: transparent transparent #22222222;
18 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

**18、六边形**
最终效果：
![CSS画图 <wbr>强悍 <wbr>各种图形 <wbr>果断分享](https://images.cnblogs.com/cnblogs_com/sxwgf/201201/201201170833207161.png)
CSS代码如下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #hexagon {
 2     width: 100px;
 3     height: 55px;
 4     background: #22222222;
 5     position: relative;
 6 }
 7 #hexagon:before {
 8     content: "";
 9     position: absolute;
10     top: -25px;
11     left: 0;
12     width: 0;
13     height: 0;
14     border-left: 50px solid transparent;
15     border-right: 50px solid transparent;
16     border-bottom: 25px solid #22222222;
17 }
18 #hexagon:after {
19     content: "";
20     position: absolute;
21     bottom: -25px;
22     left: 0;
23     width: 0;
24     height: 0;
25     border-left: 50px solid transparent;
26     border-right: 50px solid transparent;
27     border-top: 25px solid #22222222;
28 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

**19、八角形**
最终效果：
![CSS画图 <wbr>强悍 <wbr>各种图形 <wbr>果断分享](https://images.cnblogs.com/cnblogs_com/sxwgf/201201/20120117083320716.png)
CSS代码如下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #octagon {
 2     width: 100px;
 3     height: 100px;
 4     background: #22222222;
 5     position: relative;
 6 }
 7 
 8 #octagon:before {
 9     content: "";
10     position: absolute;
11     top: 0;
12     left: 0;
13     border-bottom: 29px solid #22222222;
14     border-left: 29px solid #eee;
15     border-right: 29px solid #eee;
16     width: 42px;
17     height: 0;
18 }
19 
20 #octagon:after {
21     content: "";
22     position: absolute;
23     bottom: 0;
24     left: 0;
25     border-top: 29px solid #22222222;
26     border-left: 29px solid #eee;
27     border-right: 29px solid #eee;
28     width: 42px;
29     height: 0;
30 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

**20、爱心**

最终效果：
![CSS画图 <wbr>强悍 <wbr>各种图形 <wbr>果断分享](https://images.cnblogs.com/cnblogs_com/sxwgf/201201/201201170833216538.png)
CSS代码如下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #heart {
 2     position: relative;
 3     width: 100px;
 4     height: 90px;
 5 }
 6 #heart:before,
 7 #heart:after {
 8     position: absolute;
 9     content: "";
10     left: 50px;
11     top: 0;
12     width: 50px;
13     height: 80px;
14     background: #22222222;
15     -moz-border-radius: 50px 50px 0 0;
16     border-radius: 50px 50px 0 0;
17     -webkit-transform: rotate(-45deg);
18     -moz-transform: rotate(-45deg);
19     -ms-transform: rotate(-45deg);
20     -o-transform: rotate(-45deg);
21     transform: rotate(-45deg);
22     -webkit-transform-origin: 0 100%;
23     -moz-transform-origin: 0 100%;
24     -ms-transform-origin: 0 100%;
25     -o-transform-origin: 0 100%;
26     transform-origin: 0 100%;
27 }
28 #heart:after {
29     left: 0;
30     -webkit-transform: rotate(45deg);
31     -moz-transform: rotate(45deg);
32     -ms-transform: rotate(45deg);
33     -o-transform: rotate(45deg);
34     transform: rotate(45deg);
35     -webkit-transform-origin: 100% 100%;
36     -moz-transform-origin: 100% 100%;
37     -ms-transform-origin: 100% 100%;
38     -o-transform-origin: 100% 100%;
39     transform-origin :100% 100%;
40 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

**21、无穷大符号**
最终效果：
![CSS画图 <wbr>强悍 <wbr>各种图形 <wbr>果断分享](https://images.cnblogs.com/cnblogs_com/sxwgf/201201/201201170833214520.png)
CSS代码如下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #infinity {
 2     position: relative;
 3     width: 212px;
 4     height: 100px;
 5 }
 6 
 7 #infinity:before,
 8 #infinity:after {
 9     content: "";
10     position: absolute;
11     top: 0;
12     left: 0;
13     width: 60px;
14     height: 60px;
15     border: 20px solid #22222222;
16     -moz-border-radius: 50px 50px 0 50px;
17     border-radius: 50px 50px 0 50px;
18     -webkit-transform: rotate(-45deg);
19     -moz-transform: rotate(-45deg);
20     -ms-transform: rotate(-45deg);
21     -o-transform: rotate(-45deg);
22     transform: rotate(-45deg);
23 }
24 
25 #infinity:after {
26     left: auto;
27     right: 0;
28     -moz-border-radius: 50px 50px 50px 0;
29     border-radius: 50px 50px 50px 0;
30     -webkit-transform: rotate(45deg);
31     -moz-transform: rotate(45deg);
32     -ms-transform: rotate(45deg);
33     -o-transform: rotate(45deg);
34     transform: rotate(45deg);
35 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

**22、鸡蛋**
最终效果
![CSS画图 <wbr>强悍 <wbr>各种图形 <wbr>果断分享](https://images.cnblogs.com/cnblogs_com/sxwgf/201201/201201170833227519.png)
CSS代码如下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
1 #egg {
2     display:block;
3     width: 126px;
4     height: 180px;
5     background-color: #22222222;
6     -webkit-border-radius: 63px 63px 63px 63px / 108px 108px 72px 72px;
7     border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
8 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

**23、食逗人（Pac-Man）**

最终效果：![CSS画图 <wbr>强悍 <wbr>各种图形 <wbr>果断分享](https://images.cnblogs.com/cnblogs_com/sxwgf/201201/201201170833222469.png)
CSS代码如下：

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 #pacman {
 2     width: 0px;
 3     height: 0px;
 4     border-right: 60px solid transparent;
 5     border-top: 60px solid #22222222;
 6     border-left: 60px solid #22222222;
 7     border-bottom: 60px solid #22222222;
 8     border-top-left-radius: 60px;
 9     border-top-right-radius: 60px;
10     border-bottom-left-radius: 60px;
11     border-bottom-right-radius: 60px;
12 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

 

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