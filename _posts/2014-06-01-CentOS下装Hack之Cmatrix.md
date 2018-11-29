---
title: CeotOS下Hacker装之Cmatrix
description: Cmatrix实现黑客帝国之矩阵效果
categories:
 - CentOS
tags:
 - CentOS
 - Cmatrix
---  
下载Cmatrix包```cmatrix-1.2a.tar.gz```后安装  
[cmatrix-1.2a.tar.gz包下载地址](https://sourceforge.net/projects/cmatrix/files/latest/download?source=typ_redirect)  
```shell  
[root@localhost ~]# ls
cmatrix-1.2a.tar.gz
[root@localhost ~]# tar xvf cmatrix-1.2a.tar.gz  
[root@localhost ~]# cd cmatrix-1.2a
[root@localhost ~]# yum install ncurses-devel  
已加载插件：fastestmirror
Loading mirror speeds from cached hostfile
 * base: ftp.sjtu.edu.cn
 * extras: mirrors.cn99.com
 * updates: mirrors.cn99.com
正在解决依赖关系
--> 正在检查事务
---> 软件包 ncurses-devel.x86_64.0.5.9-14.20130511.el7_4 将被 安装
--> 解决依赖关系完成

依赖关系解决

===========================================================================================
 Package                架构            版本                           源             大小
===========================================================================================
正在安装:
 ncurses-devel          x86_64          5.9-14.20130511.el7_4          base          712 k

事务概要
===========================================================================================
安装  1 软件包

总下载量：712 k
安装大小：2.1 M
Is this ok [y/d/N]: y
Downloading packages:
ncurses-devel-5.9-14.20130511.el7_4.x86_64.rpm                      | 712 kB  00:00:00     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  正在安装    : ncurses-devel-5.9-14.20130511.el7_4.x86_64                             1/1 
  验证中      : ncurses-devel-5.9-14.20130511.el7_4.x86_64                             1/1 

已安装:
  ncurses-devel.x86_64 0:5.9-14.20130511.el7_4                                             

完毕！
[root@localhost cmatrix-1.2a]# 
[root@localhost cmatrix-1.2a]# ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH
[root@localhost cmatrix-1.2a]# 
```  
编译失败，因为没有安装```gcc```包。  
```shell  
[root@localhost cmatrix-1.2a]# yum install gcc
...
已安装:
  gcc.x86_64 0:4.8.5-28.el7_5.1                                                            

作为依赖被安装:
  cpp.x86_64 0:4.8.5-28.el7_5.1            glibc-devel.x86_64 0:2.17-222.el7              
  glibc-headers.x86_64 0:2.17-222.el7      kernel-headers.x86_64 0:3.10.0-862.9.1.el7     
  libmpc.x86_64 0:1.0.1-3.el7              mpfr.x86_64 0:3.1.1-4.el7                      

作为依赖被升级:
  libgcc.x86_64 0:4.8.5-28.el7_5.1            libgomp.x86_64 0:4.8.5-28.el7_5.1           

完毕！
[root@localhost cmatrix-1.2a]# 
```  
再次编译并安装。  
```shell  
[root@localhost cmatrix-1.2a]# ./configure  
...
[root@localhost cmatrix-1.2a]# make
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -Wall -Wno-comment -c cmatrix.c
gcc  -g -O2 -Wall -Wno-comment  -o cmatrix  cmatrix.o  -lncurses  -lncurses
[root@localhost cmatrix-1.2a]# 
[root@localhost cmatrix-1.2a]# 
[root@localhost cmatrix-1.2a]# make install
make[1]: 进入目录“/root/cmatrix-1.2a”
/bin/sh ./mkinstalldirs /usr/local/bin
  /usr/bin/install -c  cmatrix /usr/local/bin/cmatrix
make  install-man1
make[2]: 进入目录“/root/cmatrix-1.2a”
/bin/sh ./mkinstalldirs /usr/local/man/man1
mkdir /usr/local/man
mkdir /usr/local/man/man1
 /usr/bin/install -c -m 644 ./cmatrix.1 /usr/local/man/man1/cmatrix.1
make[2]: 离开目录“/root/cmatrix-1.2a”
 Installing matrix fonts in /usr/lib/kbd/consolefonts...
make[1]: 离开目录“/root/cmatrix-1.2a”
[root@localhost cmatrix-1.2a]#  
```  
使用说明。
```shell  
[root@localhost cmatrix-1.2a]# cmatrix -h
 Usage: cmatrix -[abBfhlsVx] [-u delay] [-C color]
 -a: Asynchronous scroll
 -b: Bold characters on
 -B: All bold characters (overrides -b)
 -f: Force the linux $TERM type to be on
 -l: Linux mode (uses matrix console font)
 -o: Use old-style scrolling
 -h: Print usage and exit
 -n: No bold characters (overrides -b and -B, default)
 -s: "Screensaver" mode, exits on first keystroke
 -x: X window mode, use if your xterm is using mtx.pcf
 -V: Print version information and exit
 -u delay (0 - 10, default 4): Screen update delay
 -C [color]: Use this color for matrix (default green)
[root@localhost cmatrix-1.2a]# 
```  
执行如下命令，会得到下图的效果，并开全屏。  
```shell  
[root@localhost cmatrix-1.2a]# cmatrix -B
```  
![Alt text](http://liyufeng.angton.com/IMG_3181.GIF "#cmatrix -B效果")  
![Alt text](http://liyufeng.angton.com/IMG_3184.GIF "#cmatrix -B -C red -u 1效果")  
![Alt text](http://liyufeng.angton.com/IMG_3185.GIF "#cmatrix -b -C blue -u 6效果")  

