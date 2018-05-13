---
title: Linux下禁Ping的方法
description: Linux下禁Ping的方法
categories:
 - Linux
tags:
 - Linux
 - Ping
---

##Linux禁Ping的方法
```shell
[root@ebandao root]# echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
```
如果要恢复，只要：
```shell
[root@ebandao root]# echo 0 > /proc/sys/net/ipv4/icmp_echo_ignore_all
```
即可，挺方便，不要去专门使用ipchains或者iptables了。
    以root进入Linux系统，然后编辑文件icmp_echo_ignore_all
```shell
vi /proc/sys/net/ipv4/icmp_echo_ignore_all
```
将其值改为1后为禁止PING
将其值改为0后为解除禁止PING