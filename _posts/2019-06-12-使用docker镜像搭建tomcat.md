---
title: 使用docker镜像搭建tomcat
description: 使用docker镜像搭建tomcat
date: 2019-06-12 23:28:23
categories:
 - docker
 - tomcat
tags:
 - docker
 - tomcat
---
#### 选择安装并启动容器    

我们选择星数第一的镜像**tomcat**  

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/docker_tomcat01.png)

  安装并启动容器代码如下：

```shell
docker run \
    --restart always \
    --name tomcat_laiyang \
    -p 9999:8080 \
    -v /mnt/tomcat_laiyang/webapps/:/usr/local/tomcat/webapps/ \
    -v /mnt/tomcat_laiyang/files/:/files/ \
    -d tomcat
```

- `/mnt/tomcat_laiyang/webapps/`为宿主机的文件目录，`/usr/local/tomcat/webapps/`为容器内的文件目录 ，用来存放运行工程项目  
- `/mnt/tomcat_laiyang/files/`为宿主机的文件目录，`/files/`为容器内的文件目录，此处用于存放项目中上传的文件  
- `--restart always`命令可以实现容器在宿主机开机时自启动  
- `-p 9999:8080`表示将宿主机的9999端口映射到容器的8080端口，此端口为tomcat服务的默认端口，可以根据需要自行修改  

#### 查看安装情况  

```shell
[root@lykjcloud-002 ~]# docker images
REPOSITORY                 TAG         IMAGE ID            CREATED             SIZE
nginx                      latest      f68d6e55e065        4 weeks ago         109MB
elleflorio/svn-server      latest      6891c2e152f3        4 weeks ago         48.1MB
tomcat                     latest      5377fd8533c3        6 weeks ago         506MB
mysql                      5.7         a1aa4f76fab9        7 weeks ago         373MB
garethflowers/svn-server   latest      a38966c9817a        2 months ago        13.7MB
garethflowers/svn-server   1.1.0       0dab185635e1        13 months ago       15MB

```

查看运行情况  

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/docker_tomcat02.png)

#### 将项目war包拷贝到webapps目录下

```shell
[root@lykjcloud-002 webapps]# pwd
/mnt/tomcat_laiyang/webapps
[root@lykjcloud-002 webapps]# ll
total 67284
drwxr-x--- 5 root root     4096 Jul 30 11:35 ROOT
-rw-r--r-- 1 root root 68890470 Jul 30 11:34 ROOT.war

```

#### 浏览器访问项目   

项目地址：http://IP地址:9999/   

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/docker_tomcat03.png)