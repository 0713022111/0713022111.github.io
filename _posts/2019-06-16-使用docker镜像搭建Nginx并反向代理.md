---
title: 使用docker镜像搭建Nginx并做反向代理
description: 使用docker镜像搭建Nginx并做反向代理
date: 2019-06-16 23:28:23
categories:
 - docker
 - Nginx
tags:
 - docker
 - Nginx
---
#### 选择安装并启动容器    

1、我们选择星数第一的官方镜像**nginx**  

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/docker_nginx01.png)  

2、下载nginx镜像包；  

```shell
[root@lykjcloud-002 ~]# docker pull nginx
```

3、查看镜像；  

```shell
[root@lykjcloud-002 ~]# docker images | grep nginx
nginx           latest        5a3221f0137b        1 weeks ago         126MB
```

4、以终端的方式打开镜像容器；  

```shell
[root@lykjcloud-002 ~]# docker run -i -t nginx /bin/bash
root@3f188db8190a:/# ls
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
```
查看nginx镜像里面配置文件、日志等文件的具体位置，如下表；  

| 序号 | 宿主机                                  | 容器                  | 注释                   |
| :--: | :-------------------------------------- | --------------------- | ---------------------- |
|  1   | /mnt/nginx_docker/nginx/conf/nginx.conf | /etc/nginx/nginx.conf | 文件，nginx配置文件    |
|  2   | /mnt/nginx_docker/nginx/conf.d          | /etc/nginx/conf.d     | 目录，用于存放配置文件 |
|  3   | /mnt/nginx_docker/nginx/logs            | /var/log/nginx        | 目录，用于存放日志文件 |
|  4   | /mnt/nginx_docker/nginx/html            | /usr/share/nginx/html | 目录，用于存放默认首页 |

5、在宿主机创建挂载源文件目录等用于之后进行挂载；   

```shell
[root@lykjcloud-002 ~]# mkdir -p /mnt/nginx_docker/nginx/conf
[root@lykjcloud-002 ~]# mkdir -p /mnt/nginx_docker/nginx/conf.d
[root@lykjcloud-002 ~]# mkdir -p /mnt/nginx_docker/nginx/logs
[root@lykjcloud-002 ~]# mkdir -p /mnt/nginx_docker/nginx/html
```

6、查看镜像容器NAMES为dazzling_haslett，为拷贝做准备；  

```shell
[root@lykjcloud-002 ~]# docker ps -a
CONTAINER ID   IMAGE    COMMAND     CREATED        STATUS         PORTS       NAMES
3f188db8190a   nginx  "/bin/bash"  4days ago   Exited(0)4days ago        dazzling_haslett
```

7、将容器中的配置文件```nginx.conf```和```default.conf```及默认页面拷贝出来；  

```shell
[root@lykjcloud-002 ~]# docker cp dazzling_haslett:/etc/nginx/nginx.conf /mnt/nginx_docker/nginx/conf/
[root@lykjcloud-002 ~]# docker cp dazzling_haslett:/etc/nginx/conf.d/default.conf /mnt/nginx_docker/nginx/conf.d/
[root@lykjcloud-002 ~]# docker cp dazzling_haslett:/usr/share/nginx/html/50x.html /mnt/nginx_docker/nginx/html/
[root@lykjcloud-002 ~]# docker cp dazzling_haslett:/usr/share/nginx/html/index.html /mnt/nginx_docker/nginx/html/
```

8、修改default.conf配置文件设置反向代理；  


```shell
server {
    ...
    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
        proxy_set_header  Host  $http_host;
        proxy_set_header  X-Real-IP  $remote_addr;
        proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_pass  http://宿主IP地址:8888;
    }
	...
}
```

9、创建并启动容器mynginx；  

```shell
docker run  \
	--restart always \
	--name mynginx \
	-d -p 80:80 \
	-v /mnt/nginx_docker/nginx/html:/usr/share/nginx/html \
	-v /mnt/nginx_docker/nginx/conf/nginx.conf:/etc/nginx/nginx.conf \
	-v /mnt/nginx_docker/nginx/conf.d:/etc/nginx/conf.d  \
	-v /mnt/nginx_docker/nginx/logs:/var/log/nginx nginx
```

10、查看容器启动情况；  

```shell
[root@lykjcloud-002 ~]# docker ps -a
CONTAINER ID  IMAGE        COMMAND              CREATED      STATUS        PORTS         NAMES
c71c58489685  nginx  "nginx -g 'daemon of…"  38 seconds ago  Created  0.0.0.0:80->80/tcp  mynginx
```

11、验证nginx；

```
[root@lykjcloud-002 ~]# curl http://127.0.0.1
<html>
<head><title>403 Forbidden</title></head>
<body>
<center><h1>403 Forbidden</h1></center>
<hr><center>nginx/1.17.3</center>
</body>
</html>

```

12、启动web服务后再次验证；

```shell
[root@lykjcloud-002 ~]# curl http://127.0.0.1

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <title>Home</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="">
    <meta name="author" content="">

    ...
</body>
</html>
```

