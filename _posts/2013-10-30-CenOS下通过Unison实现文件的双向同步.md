---
title: CentOS下通过Unison实现文件的双向同步
description: CentOS下通过Unison实现文件的双向同步
categories:
 - Linux
tags:
 - Linux
 - Unison
---  
环境如下:  
 服务器 | IP  
 - | :-:  
 IPCC | 192.168.1.16  
 cc |  192.168.1.17  
## 编译安装Unison  
Linux下通过源码包编译安装```Unison```时，需要用到Objective Caml compiler。  
### 编译安装ocaml  
```shell  
[root@IPCC ~]# cd /home/expint/  
[root@IPCC expint]# tar -zxvf ocaml-4.01.0.tar.gz  
[root@IPCC expint]# cd ocaml-4.01.0  
[root@IPCC ocaml-4.01.0]# ./configure  
[root@IPCC ocaml-4.01.0]# make world opt  
[root@IPCC ocaml-4.01.0]# make install  
```  
### 编译安装Unison  
```shell  
[root@IPCC expint]# tar -zxvf unison-2.40.102.tar.gz  
[root@IPCC expint]# cd unison-2.40.102  
[root@IPCC unison-2.40. 102]# make UISTYLE=text  
[root@IPCC unison-2.40. 102]# make install  
```  
在执行```make install```的过程中，出现以下错误提示：  
```shell  
make[1]: Leaving directory /usr/local/src/unison-2.40.102  
mv /root/bin//unison /tmp/unison-10558  
mv: 无法 stat “/root/bin//unison”: 没有那个文件或目录  
make: [doinstall] 错误 1 (忽略)  
cp unison /root/bin/  
cp: 无法创建一般文件“/root/bin/”: 是一个目录  
make: *** [doinstall] 错误 1  
```  
解决办法：  
尝试创建/root/bin文件夹  
```shell  
[root@www unison-2.40.102]# mkdir /root/bin  
```  
再次执行```make install```，还是报如下错误：  
```shell  
[root@www unison-2.40.102]# make install  
mv /root/bin//unison /tmp/unison-12868  
mv: 无法 stat “/root/bin//unison”: 没有那个文件或目录  
make: [doinstall] 错误 1 (忽略)  
cp unison /root/bin/  
cp unison /root/bin/unison-2.40  
```  
尝试再次执行```make install```，解决了问题：  
```shell  
[root@www unison-2.40.102]# make install  
mv /root/bin//unison /tmp/unison-12899  
cp unison /root/bin/  
cp unison /root/bin/unison-2.40  
```  
安装好的Unison的默认配置文件为```/root/.unison/default.prf```  
## 配置ssh key信任  
建议通过普通用户进行操作，理由是通过root操作本身就危险，免密码登陆的root就更危险了。  
### 分别在两台服务器上创建用户：expint  
```shell  
[root@IPCC ~]# useradd -m expint  
[root@IPCC ~]# passwd expint  
[root@cc ~]# useradd -m expint  
[root@cc ~]# passwd expint  
```  
### 在IPCC上创建key并配置cc的信任  
```shell  
[root@IPCC ~]# su - expint  
[expint@IPCC ~]$ ssh-keygen -t rsa  
Generating public/private rsa key pair.  
Enter file in which to save the key (/home/expint/.ssh/id_rsa):  
Created directory '/home/expint/.ssh'.   
Enter passphrase (empty for no passphrase):   
Enter same passphrase again:   
Your identification has been saved in /home/expint/.ssh/id_rsa.  
Your public key has been saved in /home/expint/.ssh/id_rsa.pub.  
The key fingerprint is: 
74:b9:99:6a:24:a1:e8:d7:64:46:65:ad:86:60:0e:ad expint@IPCC  
```  
在提示保存私钥（key）和公钥（public key）的位置时，使用默认值；  
在提示是否需要私钥密码（passphrase）时，直接敲回车，即不使用私钥密码。  
之后，将生成一对密钥，id_rsa（私钥文件）和id_rsa.pub（公钥文件），保存在/home/expint/.ssh/目录下。  
### 将公钥添加到cc的 ```authorized_keys``` 文件中  
#### 将文件上传到cc主机  
```shell  
[expint@IPCC ~]$ scp ~/.ssh/id_rsa.pub expint@192.168.1.17:/home/expint/  
The authenticity of host ‘192.168.1.17 (192.168.1.17)’ can‘t be established. 
RSA key fingerprint is 57:7a:b5:4d:fa:6d:37:db:70:12:c6:54:87:6b:7b:f8. 
Are you sure you want to continue connecting (yes/no)? yes 
Warning: Permanently added ’192.168.1.17‘ (RSA) to the list of known hosts. 
expint@192.168.1.17’s password: 
id_rsa.pub 100% 394 0.4KB/s  
```  
#### 通过SSH到登陆到cc主机，并将公钥添加到 ```authorized_keys``` 文件中  
```shell  
[expint@IPCC ~]$ ssh expint@192.168.1.17  
expint@192.168.1.17‘s password:  
[expint@cc ~]$ mkdir .ssh  
[expint@cc ~]$ chmod 700 .ssh  
[expint@cc ~]$ mv ~/id_rsa.pub ~/.ssh/authorized_keys  
[expint@cc ~]$ chmod 600 ~/.ssh/authorized_keys  
```  
#### 同理，执行以下步骤在cc主机上创建key并配置IPCC主机的信任  
```shell  
[root@cc ~]# su - expint  
[expint@cc ~]$ ssh-keygen -t rsa  
Generating public/private rsa key pair. 
Enter file in which to save the key (/home/expint/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/expint/.ssh/id_rsa. 
Your public key has been saved in /home/expint/.ssh/id_rsa.pub. 
The key fingerprint is: 
50:71:69:00:20:49:a7:18:7f:10:79:b4:31:04:95:62 expint@cc 
[expint@cc ~]$ scp ~/.ssh/id_rsa.pub expint@192.168.1.16:/home/expint/ 
The authenticity of host ’192.168.1.16 (192.168.1.16)‘ can’t be established. 
RSA key fingerprint is 57:7a:b5:4d:fa:6d:37:db:70:12:c6:54:87:6b:7b:f8. 
Are you sure you want to continue connecting (yes/no)? yes 
Warning: Permanently added ‘192.168.1.16’ (RSA) to the list of known hosts. 
expint@192.168.1.16’s password: 
id_rsa.pub 100% 393 0.4KB/s  
```  
通过SSH到登陆到IPCC主机，并将公钥添加到 authorized_keys 文件中  
```shell  
[expint@cc ~]$ ssh expint@192.168.1.16 
expint@192.168.1.16’s password: 
[expint@IPCC ~]$ mv ~/id_rsa.pub ~/.ssh/authorized_keys  
```  
#### 重启两台服务器的SSH服务  
```shell  
[root@IPCC ~]# /etc/init.d/sshd restart  
[root@cc ~]# /etc/init.d/sshd restart  
```  
## Unison的配置与使用  
在两台服务器上创建test目录，用于测试  
```shell  
[root@IPCC ~]# su - expint  
[expint@IPCC ~]$ mkdir test  
[root@cc ~]# su - expint  
[expint@cc ~]$ mkdir test  
```  
在两台服务器上分别执行一次unison，出现提示确认，则直接敲回车选择默认值  
```shell  
[expint@IPCC ~]$ unison /home/expint/test/ ssh://expint@192.168.1.17//home/expint/test/  
[expint@cc ~]$ unison /home/expint/test/ ssh://expint@192.168.1.16//home/expint/test/  
```shell  
修改两台服务器的unison配置文件，输入以下内容  
```shell  
[expint@IPCC ~]$ vim /home/expint/.unison/default.prf 
#Unison preferences file 
root = /home/expint/test 
root = ssh://expint@192.168.1.17//home/expint/test/ 
#force = 
#ignore = 
batch = true 
#repeat = 1 
#retry = 3 
owner = true 
group = true 
perms = -1 
fastcheck = false 
rsync = false 
sshargs = -C 
xferbycopying = true 
log = true 
logfile = /home/expint/.unison/unison.log 

[expint@cc ~]$ vim /home/expint/.unison/default.prf 
#Unison preferences file 
root = /home/expint/test 
root = ssh://expint@192.168.1.16//home/expint/test/ 
#force = 
#ignore = 
batch = true 
#repeat = 1 
#retry = 3 
owner = true 
group = true 
perms = -1 
fastcheck = false 
rsync = false 
sshargs = -C 
xferbycopying = true 
log = true 
logfile = /home/expint/.unison/unison.log  
```  
相关注解如下：  
```force```表示会以本地所指定文件夹为标准，将该目录同步到远端。这里需要注意，如果指定了force参数，那么Unison就变成了单项同步了，也就是说会以force指定的文件夹为准进行同步，类似于rsync。  
```ignore = Path```表示忽略指定目录，即同步时不同步它。  
```batch = true```，表示全自动模式，接受缺省动作，并执行。  
```fastcheck = true``` 表示同步时仅通过文件的创建时间来比较，如果选项为false，Unison则将比较两地文件的内容。  
```log = true``` 表示在终端输出运行信息。  
```logfile``` 指定输出的log文件。  
## Unison双向同步测试  
首先分别在IPCC与cc的/home/expint/test目录下创建文件或目录，然后在IPCC上执行```unison```，接着如果在IPCC与cc上都能看到各自创建的文件，就说明同步成功。  
分别在IPCC与cc上创建文件  
```shell  
[expint@IPCC ~]$ cd test  
[expint@IPCC test]$ touch 111  
[expint@IPCC test]$ touch 222  
[expint@IPCC test]$ ls  
111 222  
[expint@cc ~]$ cd test  
[expint@cc test]$ touch aaa  
[expint@cc test]$ touch bbb  
[expint@cc test]$ ls  
333 444  
```  
在IPCC上执行unison  
```shell  
[expint@IPCC test]$ unison  
Contacting server...
Connected [//IPCC//home/expint/test -> //cc//home/expint/test]
Looking for changes
Fatal error: Warning: inconsistent state.  
The archive file is missing on some hosts.
For safety, the remaining copies should be deleted.
  Archive ar79e4f9339cfcf577e106e0a06c02e772 on host IPCC is MISSING
  Archive ar004a996be9643b183dd4b5cd32b7a8a2 on host cc should be DELETED
Please delete archive files as appropriate and try again
or invoke Unison with -ignorearchives flag.  
```  
报错,解决方法：  
```shell  
[expint@cc /]$ cd ./home/expint/.unison/  
[expint@cc .unison]$ ll  
total 12  
-rw------- 1 expint expint  829 Oct 30 14:23 ar004a996be9643b183dd4b5cd32b7a8a2
-rw------- 1 expint expint  314 Oct 30 13:42 default.prf
-rw------- 1 expint expint 2298 Oct 30 14:34 unison.log
[expint@cc .unison]$ rm -rf ar004a996be9643b183dd4b5cd32b7a8a2  
```  
同步一下，成功。  
```shell  
[expint@cc test]$ unison  
Contacting server...
Connected [//IPCC//home/expint/test -> //cc//home/expint/test]
Looking for changes
  Waiting for changes from server
Reconciling changes
         <---- new file   aaa  
local        : absent
IPCC         : new file           modified on 2013-10-30 at 15:17:56  size 0         --rw-rw-r-- user=expint group=expint
         <---- new file   bbb  
local        : absent
IPCC         : new file           modified on 2013-10-30 at 15:18:01  size 0         --rw-rw-r-- user=expint group=expint
Propagating updates
UNISON 2.40.102 started propagating changes at 15:19:29.70 on 30 Oct 2013
[BGN] Copying aaa from //IPCC//home/expint/test to /home/expint/test
[BGN] Copying bbb from //IPCC//home/expint/test to /home/expint/test
Shortcut: copied /home/expint/test/aaa from local file /home/expint/test/444
Shortcut: copied /home/expint/test/bbb from local file /home/expint/test/.unison.aaa.004a996be9643b183dd4b5cd32b7a8a2.unison.tmp
[END] Copying aaa
[END] Copying bbb
UNISON 2.40.102 finished propagating changes at 15:19:29.70 on 30 Oct 2013
Saving synchronizer state
Synchronization complete at 15:19:29  (2 items transferred, 0 skipped, 0 failed)
[expint@cc test]$ ll
total 0
-rw-rw-r-- 1 expint expint 0 Oct 30 13:53 111
-rw-rw-r-- 1 expint expint 0 Oct 30 13:49 222
-rw-rw-r-- 1 expint expint 0 Oct 30 13:59 333
-rw-rw-r-- 1 expint expint 0 Oct 30 14:23 444
[expint@cc test]$  
```  
## 设置定期执行同步  
通过crontab计划任务来定期执行同步，以下方式设置每5分钟执行一次  
```shell  
[expint@IPCC ~]$ crontab -e */5 * * * * /usr/local/bin/unison  
crontab: usage error: no arguments permitted after this option
usage:  crontab [-u user] file
        crontab [-u user] [ -e | -l | -r ]
                (default operation is replace, per 1003.2)
        -e      (edit user’s crontab)
        -l      (list user’s crontab)
        -r      (delete user’s crontab)
        -i      (prompt before deleting user’s crontab)
        -s      (selinux context)
[expint@cc ~]$ crontab -e */5 * * * * /usr/local/bin/unison
expint用户无权限  
```  
另类解决方法：  
书写一个脚本probe.sh  
```shell  
#!/bin/bash  
while (true)  
do
    /usr/local/bin/unison
    sleep 30s 
done  
```  

