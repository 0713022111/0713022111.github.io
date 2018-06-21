---
title: CentOS搭建DNS服务器
description: CentOS系统下搭建DNS服务器
categories:
 - Linux
tags:
 - Linux
 - DNS
---  
## 搭建DNS服务器
### 安装bind  
用命令```# yum -y install bind```安装bind  
```shell  
[root@centos6 named]# rpm -qa|grep bind
bind-libs-9.7.3-8.P3.el6.x86_64
bind-9.7.3-8.P3.el6.x86_64
ypbind-1.20.4-29.el6.x86_64
rpcbind-0.2.0-8.el6.x86_64
bind-chroot-9.7.3-8.P3.el6.x86_64
bind-utils-9.7.3-8.P3.el6.x86_64       //里面整合有dig工具
```  
### 配置name.conf  
```shell  
[root@centos6 named]#vim /etc/named.conf
//
// named.conf
//
// Provided by Red Hat bind package to configure the ISC BIND named(8) DNS
// server as a caching only nameserver (as a localhost DNS resolver only).
//
// See /usr/share/doc/bind*/sample/ for example named configuration files.
//

options {
        listen-on port 53 { any; };                  //改为any
//      listen-on-v6 port 53 { ::1; };                 //注销这行
        directory       "/var/named";
        dump-file       "/var/named/data/cache_dump.db";
        statistics-file "/var/named/data/named_stats.txt";
        memstatistics-file "/var/named/data/named_mem_stats.txt";
        allow-query     { any; };                //改为 any
        recursion yes;

        dnssec-enable yes;
        dnssec-validation yes;
        dnssec-lookaside auto;

        /* Path to ISC DLV key */
        bindkeys-file "/etc/named.iscdlv.key";
};

logging {
        channel default_debug {
                file "data/named.run";
                severity dynamic;
        };
};

zone "." IN {
        type hint;
        file "named.ca";
};

zone "expint.com" IN {
        type master;
        file "expint.com.zone";            //默认到/var/named目录下寻找
};

zone "1.168.192.in-addr.arpa" IN {
        type master;
        file "1.168.192.in-addr.arpa.zone"; //默认到/var/named目录下寻找
};
//include "/etc/named.rfc1912.zones";
//include "/etc/named.root.key";  
```  
### 添加反向区域  
```shell  
[root@centos6 /]# cd /var/named
[root@centos6 named]# vi 1.168.192.in-addr.arpa.zone
$TTL    86400
@       IN      SOA     1.168.192.in-addr.arpa.  root (  
                        2009092000      ;Serial
                        28800           ;Refresh
                        14400           ;Retry
                        3600000         ;Expire
                        86400 )         ;Minimum
@       IN      NS      dns.expint.com.
66      IN      PTR     dns.expint.com.            //66对应IP中的地址
@       IN      MX      5       mail.expint.com.
66      IN      PTR     mail.expint.com.
66      IN      PTR     www.expint.com.
66      IN      PTR     bbs.expint.com.  
```  
### 添加正向区域  
```shell  
[root@centos_1_8 named]# vi expint.com.zone
$TTL    86400
@       IN      SOA     dns.expint.com.  root (
                        2009092000      ;Serial
                        28800           ;Refresh
                        14400           ;Retry
                        3600000         ;Expire
                        86400 )         ;Minimum
@       IN      NS      dns.expint.com.
localhost  IN  A        127.0.0.1
dns      IN      A       192.168.1.66
@       IN      MX      5       mail.expint.com.
mail     IN      A       192.168.1.66
www    IN      A       192.168.1.66
bbs     IN      A       192.168.1.66  
```  
### 修改hosts文件  
```shell  
[root@centos6 etc]# vi hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
192.168.1.66 dns.expint.com dns  
```  
### 修改resolv.conf文件  
机器设为域名服务器  
```shell  
[root@centos6 etc]# cat resolv.conf
nameserver 192.168.1.66  
```  
### 重启DNS  
```shell  
[root@centos6 named]# service named restart  
[root@centos6 named]# chkconfig named on  
```  
### 测试  
```shell  
[root@centos_1_8 named]# dig mail.expin.com
; <<>> DiG 9.7.3-P3-RedHat-9.7.3-8.P3.el6 <<>> mail.expin.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 17001
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1
;; QUESTION SECTION:
;mail.expin.com.                        IN      A
;; ANSWER SECTION:
mail.expin.com.         86400   IN      A       192.168.1.8
[root@centos_1_8 named]# dig www.expin.com
;; ANSWER SECTION:
www.expin.com.          86400   IN      A       192.168.1.8
[root@centos_1_8 named]# dig dns.expin.com
;; ANSWER SECTION:
dns.expin.com.          86400   IN      A       192.168.1.8
[root@centos_1_8 named]# dig bbs.expin.com
;; ANSWER SECTION:
bbs.expin.com.          86400   IN      A       192.168.1.8  
```  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/DNS1.png)  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/DNS2.png)  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/DNS3.png)  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/DNS4.png)  
DNS搭建结束。

