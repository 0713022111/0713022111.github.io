---
title: CentOS下安装Subversion1.6.11
description: CentOS下安装Subversion1.6.11
categories:
 - Linux
tags:
 - Linux
 - Subversion
---  
## 环境描述  

序号 | 系统 | IP | 备注  
- | :-: | :-: | -:  
1 | Centos6.2 | 192.168.1.245 | 运行环境  
2 | Windows7 | 192.168.1.181 | 测试环境  
  
## Subversion安装  
安装svn需要以下几个安装包，如下图  
注：其中libproxy-0.3.0-3.el6_3.x86_64.rpm  
libproxy-bin-0.3.0-3.el6_3.x86_64.rpm  
libproxy-python-0.3.0-3.el6_3.x86_64.rpm  
通过命令来安装：  
```shell  
[root@localhost liyufeng]# rpm –vih libproxy-*   
```  
