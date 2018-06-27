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
&emsp;&emsp;公司项目中有用到Redis，由于地区停电，机房的服务器就关闭了，通电重启后，开启redis服务，结果发现redis之前存储的数据出现丢失的情况，好多key丢失了；然后通过查找资料，发现解决方法，故记录下来以备后查。  
解决方案如下：


①vim /etc/sysctl.config 编辑sysctl.config



②独占一行，添加一行  vm.overcommit_memory = 1



③wq保存修改的配置，然后sysctl -p 使配置生效



这样linux服务器即使重启了，之前的数据依然存在！

