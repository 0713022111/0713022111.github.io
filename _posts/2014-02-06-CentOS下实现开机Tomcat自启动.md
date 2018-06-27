---
title: CentOS下实现开机Tomcat自启动
description: CentOS下实现开机Tomcat自启动
categories:
 - Linux
 - Tomcat
tags:
 - Linux
 - Tomcat
---  
## 脚本文件  
在```/etc/init.d```下创建脚本文件tomcat。  
```shell  
[root@ppp-2-85-227-23 ~]# vi tomcat  
```  
脚本如下：
```shell  
#!/bin/bash  
#  
# tomcat startup script for the Tomcat server  
#  
# chkconfig: 345 80 20  
# description: start the tomcat deamon  
#  
# Source function library  
. /etc/rc.d/init.d/functions  
   
prog=tomcat8  

JAVA_HOME=/usr/java/jdk1.7.0_79/  
export JAVA_HOME
CATALANA_HOME=/home/tomcat8  
export CATALINA_HOME  
   
case "$1" in  
    start)  
        echo "Starting Tomcat..."  
        $CATALANA_HOME/bin/startup.sh  
        sleep 1  
        echo `ps -ef|grep "$CATALANA_HOME"|grep -v "grep"`
        ;;  
   
    stop)  
        echo "Stopping Tomcat..."  
        #$CATALANA_HOME/bin/shutdown.sh  
        P_ID=`ps -ef | grep -w "$CATALANA_HOME" | grep -v "grep" | awk '{print $2}'`  
        if [ -z $P_ID ]; then
            echo "=== $prog process not exists or stop success"
        else
            echo "=== $prog process pid is:$P_ID"
            echo "=== begin kill $prog process, pid is:$P_ID"
            kill -9 $P_ID
        fi
        ;;  
   
    restart)  
        echo "Stopping Tomcat..."  
        #$CATALANA_HOME/bin/shutdown.sh  
        #sleep 2    
        #echo "Starting Tomcat..."  
        #$CATALANA_HOME/bin/startup.sh  
        #;;  
        $0 stop
        sleep 5
        $0 start
        echo "=== restart $prog"
        ;;
   
    *)  
        echo "Usage: $prog {start|stop|restart}"  
        ;;  
esac  
exit 0  
```  
## 配置  
```shell  
[root@ppp-2-85-227-23 ~]# chmod +x /etc/init.d/tomcat   
[root@ppp-2-85-227-23 ~]# chkconfig tomcat on  
[root@ppp-2-85-227-23 ~]# chkconfig --list|grep tomcat
tomcat           0:off   1:off   2:on    3:on    4:on    5:on    6:off
[root@ppp-2-85-227-23 ~]# service tomcat start  
