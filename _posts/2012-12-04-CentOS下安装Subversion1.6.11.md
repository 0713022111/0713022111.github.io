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
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_i_1.png )
注：其中libproxy-0.3.0-3.el6_3.x86_64.rpm  
libproxy-bin-0.3.0-3.el6_3.x86_64.rpm  
libproxy-python-0.3.0-3.el6_3.x86_64.rpm  
通过命令来安装：  
```shell  
[root@localhost liyufeng]# rpm –vih libproxy-*   
```  
## 测试SVN是否安装成功  
查看安装目录  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_i_2.png )  
执行:   
```shell  
[root@localhost liyufeng]# svnserve –version  
```  
如果显示版本信息, 则安装成功.如下：  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_i_3.png )  
## 新建版本库  
&emsp;&emsp;本系统采用为每个项目单独建一版本库的策略。配置文件，密码文件，访问控制文件等都放在版本库的conf目录下。所以每次开始一个新项目都必须新建一个版本库，并重新配置各配置文件。  
&emsp;&emsp;还有很重要的一条，要求各组员重新配置客户端，包括服务器版本库路径，本地路径等信息。  
:point_right:建立版本库目录(可建立多个，新建库后以下各项都需重新配置。注意区别安装目录与版本库目录，以下讲的都是版本库目录)  
```shell  
[root@localhost liyufeng]# mkdir –p /opt/svndata/repos  
```  
:point_right:建立svn版本库(与上面目录对应)  
```shell  
[root@localhost liyufeng]# svnadmin create /opt/svndata/repos  
```  
执行此命令后svn自动在repos目录下添加必须的配置文件。 
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_i_4.png )   
需要配置的文件位于conf目录下：```authz```，```passwd```，```svnserve.conf```。  
关于这三个文件的配置可查看文件【Subversion配置文件详析_20121204.docx】。  
注意:版本库不同于一般的文件夹, 直接在操作系统上新建文件无法被SVN识别, 必须使用import等命令将文件导入版库。此为svn内部指令，create用于新建版本库。请使用svn help查看详细说明。  
## 启动服务  
```shell  
[root@localhost liyufeng]#svnserve –d –r /opt/svndata/repos/   
```  
启动服务, 以deamon方式运行。  
本系统采用svnserve方式, 这是小团队项目的推荐方法. 这种方法维护最少, 配置最简单。  
指令简介：此指令用于启动svn服务，```-d```指明以守护模式运行，svn自动在```3690```端口监听。3690是默认端口，可以使用```“--listen-port=”```或者```“--listen-host=”```来指定其它端口。```-r```选项用来指定svn服务的根目录，这样用户就可以使用相对路径访问，而不用提供完整路径。另，关闭svn服务可以通过执行```#kill 3690```来实现。  
## 查看svn端口  
查看svn端口，为3690。并打开防火墙。  
```shell  
[root@localhost liyufeng]# netstat -tnlp|grep svn  
```  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_i_5.png )  
```shell  
[root@localhost sysconfig]# cd /etc/sysconfig  
```  
配置防火墙，是开通端口3690。  
```shell  
[root@localhost sysconfig]# vi iptables  
```  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_i_6.png )  
重启防火墙  
```shell  
[root@localhost conf]# service iptables restart  
```  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_i_7.png )  
## 测试  
通过客户端```TortoiseSVN```来测试。  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_i_8.png )  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_i_9.png )  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_i_10.png )  
