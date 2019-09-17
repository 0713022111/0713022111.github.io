---
title: CentOS7安装docker
description: CentOS7安装docker
date: 2019-03-08 23:28:23
categories:
 - docker
 - CentOS
tags:
 - docker
 - CentOS
---
### 前提条件  
目前，CentOS 仅发行版本中的内核支持 Docker。  
Docker 运行在 CentOS 7 上，要求系统为64位、系统内核版本为 3.10 以上。  
Docker 运行在 CentOS-6.5 或更高的版本的 CentOS 上，要求系统为64位、系统内核版本为 2.6.32-431 或者更高版本。  

------

### 使用 yum 安装（CentOS 7下）  
Docker 要求 CentOS 系统的内核版本高于 3.10 ，通过 **uname -r**进行查看。   

```shell
[root@lykjcloud-001 ~]# uname -r
3.10.0-693.11.6.el7.x86_64
```

#### 安装 Docker  

docker分为两个分支版本: Docker CE 和 Docker EE。  
Docker CE 即社区免费版，Docker EE 即企业版，强调安全，但需付费使用。  
本次进行Docker CE 的安装使用。  
移除旧的版本：  
```shell
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-selinux \
                  docker-engine-selinux \
                  docker-engine
```
安装一些必要的系统工具：  
```shell
[root@lykjcloud-001 ~]# sudo yum install -y yum-utils device-mapper-persistent-data lvm2
```
添加软件源信息：  
```shell
[root@lykjcloud-001 ~]# sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```
更新 yum 缓存：  
```shell
[root@lykjcloud-001 ~]# sudo yum makecache fast
```
安装 Docker-ce：  
```shell
[root@lykjcloud-001 ~]# sudo yum -y install docker-ce
```
启动 Docker 后台服务  
```shell
[root@lykjcloud-001 ~]# sudo systemctl start docker
```
查看运行状态  
```shell
[root@lykjcloud-001 ~]# systemctl status docker
● docker.service - Docker Application Container Engine
   Loaded: loaded (/usr/lib/systemd/system/docker.service; disabled; vendor preset: disabled)
   Active: active (running) since Tue 2019-03-08 15:19:23 CST; 28min ago
     Docs: https://docs.docker.com
 Main PID: 9779 (dockerd)
   Memory: 47.3M
   CGroup: /system.slice/docker.service
           └─9779 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock

```

  