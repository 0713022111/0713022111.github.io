---
title: CentOS下实现开机Redis自启动
description: CentOS下实现开机Redis自启动
categories:
 - Linux
 - Redis
tags:
 - Linux
 - Redis
---  
## 前期准备 
![Alt text](http://liyufeng.angton.com/redis_boot.png "Redis Info")  
&emsp;&emsp;为了让redis-server能在系统启动时自动运行，需要将redis服务作为守护进程（daemon）来运行，找到配置文件```redis.conf```的文件，这个文件是redis服务运行时加载的配置，需要修改daemonize的值：  
```shell  
...
################################# GENERAL #####################################
# By default Redis does not run as a daemon. Use 'yes' if you need it.
# Note that Redis will write a pid file in /var/run/redis.pid when daemonized.
daemonize yes
# If you run Redis from upstart or systemd, Redis can interact with your
# supervision tree. Options:  
...
```  
另外需要准备如下参数：  
**REDISPORT=6379**（redis端口）  
**REDISPATH=/home/redis-stable/**（redis路径所在）  
**CONF=/etc/redis.conf**（redis配置文件所在）  
## 脚本  
在```/etc/init.d```下创建脚本文件redis。  
```shell  
[root@iZbp19jppbw8plpr718y1bZ /]# vi redis  
```  
脚本如下：
```shell  
#!/bin/sh    
#chkconfig: 2345 90 10    
# Simple Redis init.d script conceived to work on Linux systems    
# as it does use of the /proc filesystem.    
REDISPORT=6379    
REDISPATH=/home/redis-stable/  
EXEC=${REDISPATH}/src/redis-server    
CLIEXEC=${REDISPATH}/src/redis-cli    
#PIDFILE=/var/run/redis_${REDISPORT}.pid    
CONF="/etc/redis.conf"  
prog=redis
case "$1" in    
    start)  
        PID=`ps -ef|grep redis|grep -v grep|awk '{print $2}'`  
        if [ -n $PID ]    
        then    
            echo -e "\e[00;31mredis_pid:$PID exists, process is already running or crashed\e[00m"    
        else    
            echo -e "\e[00;32mStarting Redis server...\e[00m"    
            $EXEC $CONF    
        fi    
        ;;  

    status)  
        PID=`ps -ef | grep redis | grep -v grep | awk '{print $2}'`  
        if [ -z $P_ID ]; then
            echo -e "\e[00;31m$prog process not running\e[00m"
        else
            echo -e "\e[00;32m$prog process is running with pid:$PID\e[00m"
        fi
        ;; 

    stop)  
        PID=`ps -ef|grep redis|grep -v grep|awk '{print $2}'`  
        if [ -z $PID ]  
        then  
            echo "\e[00;31mredis_pid:$PID does not exist, process is not running\e[00m"    
        else     
            echo "\e[00;32mStopping ...\e[00m"    
            $CLIEXEC -p $REDISPORT shutdown    
            while [ -x /proc/${PID} ]    
            do    
                echo "\e[00;32mWaiting for Redis to shutdown ...\e[00m"    
                sleep 1    
            done    
            echo "\e[00;32mRedis stopped\e[00m"    
        fi    
        ;;    
    *)    
        echo "\e[00;31mPlease use service $prog {start|status|stop}\e[00m"    
        ;;    
esac
exit 0  
```  
## 配置  
```shell  
[root@ppp-2-85-227-23 ~]# chmod +x /etc/init.d/redis  
[root@ppp-2-85-227-23 ~]# chkconfig redis on  
[root@ppp-2-85-227-23 ~]# chkconfig --list|grep redis  
redis           0:off   1:off   2:on    3:on    4:on    5:on    6:off  
[root@ppp-2-85-227-23 ~]# service redis start  
```  

