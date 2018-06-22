---
title: CentOS下使用VSFTP搭建FTP服务
description: CentOS下使用VSFTP搭建FTP服务
categories:
 - Linux
tags:
 - Linux
 - FTP
---  
VSFTP是一个基于GPL发布的类Unix系统上使用的FTP服务器软件，它的全称是Very Secure FTP 从此名称可以看出来，编制者的初衷是代码的安全。  
## 安装   
一般在CentOS上都自动安装了vsftpd，若没有安装则可以使用以下步骤进行安装  
```shell  
yum -y install vsftpd
touch /var/log/vsftpd.log # 创建vsftp的日志文件  
```  
## 基于虚拟用户的FTP架设  
1. 我们在/etc/vsftpd/vsftpd.conf中做如下CentOS FTP服务配置：  
```anonymous_enable=NO```设定不允许匿名访问；  
```local_enable=YES```设定本地用户可以访问；(注：如使用虚拟宿主用户，在该项目设定为NO的情况下所有虚拟用户将无法访问。)  
```chroot_list_enable=YES```使用户不能离开主目录；  
```xferlog_file=/var/log/vsftpd.log```设定vsftpd的服务日志保存路径；（注意，该文件默认不存在。必须要手动touch出来。）  
```ascii_upload_enable=YES```；  
```ascii_download_enable=YES```设定支持ASCII模式的上传和下载功能；  
```pam_service_name=vsftpd```PAM认证文件名。PAM将根据/etc/pam.d/vsftpd进行认证；  
以下这些是关于vsftpd虚拟用户支持的重要CentOS FTP服务配置项目。  
默认vsftpd.conf中不包含这些设定项目，需要自己手动添加CentOS FTP服务配置。  
```guest_enable=YES``` 设定启用虚拟用户功能。  
```guest_username=ftp``` 指定虚拟用户的宿主用户。CentOS中已经有内置的ftp用户了  
```user_config_dir=/etc/vsftpd/vuser_conf``` 设定虚拟用户个人vsftp的CentOS FTP服务文件存放路径。  
存放虚拟用户个性的CentOS FTP服务文件(配置文件名=虚拟用户名)  
其他内容可以参考修改，以下内容为必要的   
```shell  
anonymous_enable=NO 
local_enable=YES 
write_enable=NO 
anon_upload_enable=NO 
anon_mkdir_write_enable=NO 
anon_other_write_enable=NO 
chroot_local_user=YES 限制用户在默认目录
guest_enable=YES 
guest_username=virtual 
listen=YES 
listen_port=21 
pasv_enable=YES 启用FTP被动模式
pasv_min_port=30000 设置被动模式开启的最大、最小端口号
pasv_max_port=30999  
```  
2. 创建chroot list，将用户ftp加入其中：  
```shell  
touch /etc/vsftpd/chroot_list  
echo ftp >> /etc/vsftpd/chroot_list  
```  
3. 进行认证：  
首先，安装Berkeley DB工具，很多人找不到db_load的问题就是没有安装这个包。  
```shell  
yum install db4 db4-utils  
```  
然后，创建用户密码文本/etc/vsftpd/vuser_passwd.txt ，注意奇行是用户名，偶行是密码  
```shell  
ftpuser1
ftppass1
ftpuser2
ftppass2  
```  
接着，生成虚拟用户认证的db文件  
```shell  
db_load -T -t hash -f /etc/vsftpd/vuser_passwd.txt /etc/vsftpd/vuser_passwd.db  
```  
随后，编辑认证文件/etc/pam.d/vsftpd，全部注释掉原来语句，再增加以下两句  
```shell  
auth required pam_userdb.so db=/etc/vsftpd/vuser_passwd  
account required pam_userdb.so db=/etc/vsftpd/vuser_passwd  
```  
最后，创建虚拟用户个性CentOS FTP服务文件  
```shell  
mkdir /etc/vsftpd/vuser_conf/  
vi /etc/vsftpd/vuser_conf/ftpuser1（ftpuser2）  
```  
内容如下：  
```shell  
local_root=/opt/var/ftp/ftpuser1（ftpuser2） 虚拟用户的根目录(根据实际修改)
write_enable=YES 可写
anon_umask=022 掩码
anon_world_readable_only=NO 
anon_upload_enable=YES 
anon_mkdir_write_enable=YES
anon_other_write_enable=YES  
```  
## 启动vsftp服务器  
```shell  
mkdir /opt/var/ftp/ftpuser1（ftpuser2）  
chmod 777 /opt/var/ftp/ftpuser1 （ftpuser2）         
代表user，group ,others ,都有读写和可执行权限  
service vsftpd start  
```  
配置成功！  
