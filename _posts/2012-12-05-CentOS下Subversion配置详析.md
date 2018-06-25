---
title: CentOS下Subversion配置文件详析
description: CentOS下Subversion配置文件详析
categories:
 - Linux
tags:
 - Linux
 - Subversion
---  
&emsp;&emsp;Svnserve是SVN自带的一个轻型服务器，客户端通过使用以```svn://```或```svn+ssh://```为前缀的URL来访问svnserve服务器，实现远程访问SVN版本库。
svnserve可以通过配置文件来设置用户和口令，以及按路径控制版本库访问权限。  
&emsp;&emsp;本文详细分析了svnserve配置文件格式，并说明如何使用配置文件控制版本库访问权限。
本文介绍SVN的版本为1.6.11。  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_c_1.png)  
## svnserve配置文件概述  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_c_2.png)  
svnserve配置文件通常由以下3个文本文件组成：
svn服务配置文件，该文件版本库目录的conf目录下，文件名为svnserve.conf。  
用户名口令文件，该文件名在文件svnserve.conf中指定，缺省为同目录下的passwd。  
权限配置文件，该文件名也在文件svnserve.conf中指定，缺省为同目录下的authz。  
## svn服务配置文件  
svn服务配置文件为版本库目录中的文件conf/svnserve.conf。该文件仅由一个[general]配置段组成。  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_c_3.png)  
**[general]**配置段中配置行格式如下：  
<配置项> = <值>  
配置项分为以下5项：  
anon-access 控制非鉴权用户访问版本库的权限。取值范围为"write"、"read"和"none"。
即"write"为可读可写，"read"为只读，"none"表示无访问权限。  
缺省值：read  
auth-access 控制鉴权用户访问版本库的权限。取值范围为"write"、"read"和"none"。
即"write"为可读可写，"read"为只读，"none"表示无访问权限。  
缺省值：write  
password-db 指定用户名口令文件名。除非指定绝对路径，否则文件位置为相对conf
目录的相对路径。  
缺省值：passwd  
authz-db 指定权限配置文件名，通过该文件可以实现以路径为基础的访问控制。
除非指定绝对路径，否则文件位置为相对conf目录的相对路径。  
缺省值：authz  
realm 指定版本库的认证域，即在登录时提示的认证域名称。若两个版本库的
认证域相同，建议使用相同的用户名口令数据文件。  
缺省值：一个UUID(Universal Unique IDentifier，全局唯一标示)。  
说明:版本库认证域  
在使用svn客户端访问svnserve服务器时，若需要用户登录，则提示信息如下：  
```shell  
[root@centos_1_8 conf]# svn list svn://192.168.1.8/CallCenter
Authentication realm: 0d545a49-4038-0410-99b4-c66dc73f754e
Password for root:  
```  
在上述第2行"Authentication realm: "之后显示的字符串为认证域名称。如果在配置文件中为设定认证域，就会提示一个UUID，如上述所示。  
如果在配置文件中指定了如下配置项：  
realm = repos  
将在svn客户端提示如下：  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_c_4.png)  
例1：svn服务配置文件conf/svnserve.conf的内容如下：  
```shell  
[general]
anon-access = none
auth-access = write
password-db = passwd
authz-db = authz
realm = repos  
```  
上述配置文件设定非鉴权用户无权限访问该版本库；鉴权用户可对版本库进行读写；用户名口令文件为conf目录的文件"passwd"；权限配置文件为conf目录的文件"authz"；版本库的认证域为"repos"。  
## 用户名口令文件  
用户名口令文件由svnserve.conf的配置项password-db指定，缺省为conf目录中的passwd。该文件仅由一个[users]配置段组成。  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_c_5.png)  
[users]配置段的配置行格式如下：
<用户名> = <口令>
注意：配置行中的口令为未经过任何处理的明文。
例2：用户名口令文件conf/passwd的内容如下：  
```shell  
[users]
dihuaiying = dihuaiying_passwd
gubin = gubin_passwd
……  
```  
该文件中配置了几个用户，其中用户名"dihaiying"和"gubin"。其中" dihuaiying "用户的口令为" dihuaiying_passwd"；" gubin "用户的口令为" gubin_passwd"。
## 权限配置文件  
权限配置文件由svnserve.conf的配置项authz-db指定，缺省为conf目录中的authz。该配置文件由一个[groups]配置段和若干个版本库路径权限段组成。  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_c_6.png)  
[groups]配置段中配置行格式如下：  
<用户组> = <用户列表>  
用户列表由若干个用户组或用户名构成，用户组或用户名之间用逗号","分隔，引用用户组时要使用前缀"@"(如：引用用户组"admin"要使用字符串"@admin")。  
版本库路径权限段的段名格式如下：  
[<版本库名>:<路径>]  
如版本库abc路径/tmp的版本库路径权限段的段名为"[abc:/tmp]"。  
可省略段名中的版本库名。若省略版本库名，则该版本库路径权限段对所有版本库中相同路径的访问控制都有效。如：段名为"[/tmp]"的版本库路径权限段设置了所有引用该权限配置文件的版本库中目录"/tmp"的访问权限。  
版本库路径权限段中配置行格式有如下三种：  
<用户名> = <权限>  
<用户组> = <权限>  
* = <权限>  
其中，"*"表示任何用户；权限的取值范围为''、'r'和'rw'，''表示对该版本库路径无任何权限，'r'表示具有只读权限，'rw'表示有读写权限。  
注意：每行配置只能配置单个用户或用户组。  
例3：权限配置文件conf/authz的内容如下：  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/subverison_c_7.png)    
在上述配置文件中，定义了一个用户组"admin"，该用户组包含用户"gubin"和"lixiaolong"。然后定义了2个版本库路径权限段。其中，版本库"admintools"只有用户组"admin"可读写，其他用户无任何权限；版本库"test"中路径"/home/gubin"只有用户" gubin "有读写权限，其他用户只有可读权限。  
## 总结  
在本文中，详细介绍了svnserve程序的3个配置文件。SVN管理员可以通过这3个配置文件设置svnserve服务的用户名口令，以及对版本库路径的访问权限。这些配置文件保存后就立即生效，不需要重启svnserve服务。  
需要强调的是本文介绍的配置文件只对svnserve服务有效，即客户端通过前缀为svn://或svn+ssh://的URL访问版本库有效，而对通过前缀http://、https://或file:///的URL无效。  
