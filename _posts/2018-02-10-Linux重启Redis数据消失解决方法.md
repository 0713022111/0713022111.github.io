---
title: Linux重启Redis数据消失解决方法
description: Linux重启Redis数据消失解决方法
categories:
 - Linux
 - Redis
tags:
 - Linux
 - Redis
---  
&emsp;&emsp;公司项目中有用到Redis，由于地区停电，机房的服务器就关闭了，通电重启后，开启redis服务，结果发现redis之前存储的数据出现key丢失的情况；然后通过查找资料，发现如下解决方法，故记录下来以备后查。  
需要修改Linux内核参数，找到```sysctl.config```文件，进行编辑；  
```shell  
[root@dsdrrreqghhuiio ~]# vi /etc/sysctl.config  
```  
添加一行```vm.overcommit_memory = 1```；  
然后```sysctl -p``` 使配置生效；  
```shell  
[root@dsdrrreqghhuiio ~]# sysctl -p  
```  


