---
title: CentOS下Subversion配置文件详析
description: CentOS下Subversion配置文件详析
categories:
 - Linux
tags:
 - Linux
 - Subversion
---  
&emsp;&emsp;Svnserve是SVN自带的一个轻型服务器，客户端通过使用以```svn://```或```svn+ssh://```为前缀的URL来访问svnserve服务器，实现远程访问SVN版本库。
svnserve可以通过配置文件来设置用户和口令，以及按路径控制版本库访问权限。  
&emsp;&emsp;本文详细分析了svnserve配置文件格式，并说明如何使用配置文件控制版本库访问权限。
本文介绍SVN的版本为1.6.11。  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_c_1.png)  


