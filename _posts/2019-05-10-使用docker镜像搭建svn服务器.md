---
title: 使用docker镜像garethflowers/svn-server搭建svn服务器
description: 使用docker镜像garethflowers/svn-server搭建svn服务器
date: 2019-05-10 23:28:23
categories:
 - docker
 - Subversion
tags:
 - docker
 - Subversion
---
#### 选择安装并启动容器    

我们选择星数第一的镜像**garethflowers/svn-server**  

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/docker-svn1.png)

  安装并启动容器代码如下：

```shell
docker run \
    --restart always \
    --name svn \
    -d \
    -v /root/dockers/svn:/var/opt/svn \
    -p 3690:3690 \
    garethflowers/svn-server
```

- `/root/dockers/svn`为宿主机的文件目录，`/var/opt/svn`为容器内的文件目录
- `--restart always`命令可以实现容器在宿主机开机时自启动
- `-p 3690:3690`表示将宿主机的3690端口映射到容器的3690端口，此端口为svn服务的默认端口，可以根据需要自行修改

#### 创建svn仓库和账户

- 进入容器中进行配置

```shell
[root@lykjcloud-002 ~]# docker exec -it svn /bin/sh
/var/opt/svn #
```

- 创建名称为svn的资源仓库

```shell
/var/opt/svn # svnadmin create svn
```

创建成功后svn目录内应该包含以下文件  

```shell
/var/opt/svn # ls svn/
README.txt  conf        db          format      hooks       locks
/var/opt/svn #
/var/opt/svn # ls svn/conf/
authz           hooks-env.tmpl  passwd          svnserve.conf
/var/opt/svn #
```

- 资源仓库配置，修改```svnserve.conf ```   

```shell
[general]
anon-access = none             # 匿名用户不可读写，也可设置为只读 read
auth-access = write            # 授权用户可写
password-db = passwd           # 密码文件路径，相对于当前目录
authz-db = authz               # 访问控制文件
realm = /var/opt/svn/svn       # 认证命名空间，会在认证提示界面显示，并作为凭证缓存的关键字，可以写仓库名称比如svn
```

- 配置账号与密码，修改 ```passwd```文件，格式为“账号 = 密码”    

```shell
/var/opt/svn/svn/conf # cat passwd
### This file is an example password file for svnserve.
### Its format is similar to that of svnserve.conf. As shown in the
### example below it contains one section labelled [users].
### The name and password for each user follow, one account per line.

[users]
# harry = harryssecret
# sally = sallyssecret
lyf = 123456
  
```

- 配置账户权限，修改 ```authz```文件    

```shell
/var/opt/svn/svn/conf # cat authz
### This file is an example authorization file for svnserve.
### Its format is identical to that of mod_authz_svn authorization
### files.
### As shown below each section defines authorizations for the path and
### (optional) repository specified by the section name.
### The authorizations follow. An authorization line can refer to:
###  - a single user,
###  - a group of users defined in a special [groups] section,
###  - an alias defined in a special [aliases] section,
###  - all authenticated users, using the '$authenticated' token,
###  - only anonymous users, using the '$anonymous' token,
###  - anyone, using the '*' wildcard.
###
### A match can be inverted by prefixing the rule with '~'. Rules can
### grant read ('r') access, read-write ('rw') access, or no access
### ('').

[aliases]
# joe = /C=XZ/ST=Dessert/L=Snake City/O=Snake Oil, Ltd./OU=Research Institute/CN=Joe Average

[groups]
# harry_and_sally = harry,sally
# harry_sally_and_joe = harry,sally,&joe
owner = admin,lyf

# [/foo/bar]
# harry = rw
# &joe = r
# * =

# [repository:/baz/fuz]
# @harry_and_sally = rw
# * = r

[/]                            # / 表示所有仓库
admin = rw                     # 用户 admin 在所有仓库拥有读写权限

[svn:/]                        # 表示以下用户在仓库 svn 的所有目录有相应权限
@owner = rw                    # 表示 owner 组下的用户拥有读写权限

```

#### 使用tortoiseSVN与svn进行连接  

使用```svn://ip/svn```地址进行连接  
![svn](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/subversion01.png)  