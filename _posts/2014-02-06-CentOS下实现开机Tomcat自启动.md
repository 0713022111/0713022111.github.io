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
        P_ID=`ps -ef | grep -w "$CATALANA_HOME" | grep -v "grep" | awk '{print $2}'`  
        if [ -z $P_ID ]; then           
            echo -e "=== \e[00;32mStarting Tomcat...\e[00m"  
            $CATALANA_HOME/bin/startup.sh  
            sleep 1  
            echo `ps -ef|grep "$CATALANA_HOME"|grep -v "grep"`
        else 
            echo -e "=== \e[00;31m$prog process exists\e[00m"  
        fi
        ;;  
   
    stop)  
        echo -e "\e[00;32mStopping Tomcat...\e[00m"  
        #$CATALANA_HOME/bin/shutdown.sh  
        P_ID=`ps -ef | grep -w "$CATALANA_HOME" | grep -v "grep" | awk '{print $2}'`  
        if [ -z $P_ID ]; then
            echo -e "=== \e[00;31m$prog process not exists or stop success\e[00m"
        else
            echo -e "=== \e[00;32m$prog process pid is:$P_ID\e[00m"
            echo -e "=== \e[00;32mbegin kill $prog process, pid is:$P_ID\e[00m"
            kill -9 $P_ID
        fi
        ;;  
   
    restart)  
        echo -e "\e[00;32mStopping Tomcat...\e[00m"  
        #$CATALANA_HOME/bin/shutdown.sh  
        #sleep 2    
        #echo "Starting Tomcat..."  
        #$CATALANA_HOME/bin/startup.sh  
        #;;  
        $0 stop
        sleep 5
        $0 start
        echo -e "=== \e[00;32mrestart $prog\e[00m"
        ;;
   
    *)  
        echo -e "\e[00;31mUsage: $prog {start|stop|restart}\e[00m"  
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
```  

