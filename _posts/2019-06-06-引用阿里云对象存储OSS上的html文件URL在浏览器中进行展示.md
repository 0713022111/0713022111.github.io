---
title: 引用阿里云对象存储OSS上的html文件URL在浏览器中进行展示
description: 引用阿里云对象存储OSS上的html文件URL在浏览器中进行展示，而非进行下载
date: 2019-06-06 23:28:23
categories:
 - 阿里云OSS
tags:
 - 阿里云OSS  
---
#### 问题  

最近将图床转移到阿里云OSS，引用图片没有什么问题，但是当上传一个纯html文件boy.html后进行引用，再浏览器中打开链接，提示直接下载此html文件。  

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/OSS2.png)

#### 解决  

通过修改html文件的HTTP头，将**Content-Encoding**修改为**utf-8**，**Content-Disposition**修改为**attachment inline**  

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/OSS1.png)

#### 结果  

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/OSS3.png)