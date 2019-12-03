---
title: 双RouterOS搭建OpenVPN
description: 为了解决公司分部访问总部内部网络的问题（比如访问总部192.168.188.0段），于是采用两台HEX RB750Gr3 RouterOS v6.42.6搭建OpenVPN，一个作为服务端，一个作为客户端。
date: 2019-11-28 22:55:22
categories:
 - RouterOS
 - OpenVPN  
tags:
 - RouterOS
 - OpenVPN  
---
### 简介  

为了解决公司分部访问总部内部网络的问题（比如访问总部192.168.188.0段），于是采用两台HEX RB750Gr3 RouterOS v6.42.6搭建OpenVPN，一个作为服务端，一个作为客户端。

| 角色   | 系统             | IP池                                 | Profile               |
| ------ | ---------------- | ------------------------------------ | --------------------- |
| 服务端 | RouterOS v6.42.6 | Open_vpn (172.10.10.2-172.10.10.254) | ovpn-server           |
| 客户端 | RouterOS v6.42.6 | -                                    | default（服务端分配） |

### 证书  

#### 创建证书  

```shell
[admin@MikroTik] > certificate            
[admin@MikroTik] /certificate> add name=ca-template common-name=ros-vpn-dtops.cc days-valid=3650 key-size=2048 key-usage=crl-sign,key-cert-sign 
[admin@MikroTik] /certificate> add name=server-template common-name=*.ros-vpn-dtops.cc days-valid=3650 key-size=2048 key-usage=digital-signature,key-encipherment,tls-server
[admin@MikroTik] /certificate> add name=client-template common-name=client.ros-vpn-dtops.cc days-valid=3650 key-size=2048 key-usage=tls-client 
[admin@MikroTik] /certificate> 
```

#### 证书签名  

```shell
[admin@MikroTik] /certificate> sign ca-template name=ca-certificate
  progress: done
[admin@MikroTik] /certificate> sign server-template name=server-certificate ca=ca-certificate                                                                               
  progress: done
[admin@MikroTik] /certificate> sign client-template name=client-certificate ca=ca-certificate                                                                               
  progress: done
```

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_01.png)

#### 证书导出到文件  

```shell
[admin@MikroTik] /certificate> export-certificate ca-certificate export-passphrase=""
[admin@MikroTik] /certificate> export-certificate client-certificate export-passphrase=12345678      
[admin@MikroTik] /certificate> export-certificate server-certificate export-passphrase=12345678 
```

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_02.png)

#### 下载证书文件   

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_03.png)

因为我是在作为客户端的RouterOS中创建的证书，所以要将所有的证书下载下来，再上传到作为服务端的RouterOS中；（如果是在服务端创建，则只需将ca和client的证书和私钥共三个文件下载上传到客户端。）  

### RouterOS服务端设置  

#### 上传并导入证书  

将ca、server及client相关证书密钥共5个文件上传到服务端文件中。

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_upload_09.png)

在```Certificate```中通过点击```Import```导入证书及密钥，server和client需Passphrase输入12345678。```（先上传证书再上传密钥，直见K标记）```

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_import_10.png)

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_certificate_11.png)  

或通过如下命令导入：  

```shell
[admin@MikroTik] > /certificate import file-name=cert_export_ca-certificate.crt
[admin@MikroTik] > /certificate import file-name=cert_export_server-certificate.crt
[admin@MikroTik] > /certificate import file-name=cert_export_server-certificate.key
[admin@MikroTik] > /certificate import file-name=cert_export_client-certificate.crt
[admin@MikroTik] > /certificate import file-name=cert_export_client-certificate.key
```

#### 创建OpenVPN专用的IP池    

```shell
[admin@MikroTik] /certificate> /ip pool add name="Open_vpn" ranges=172.10.10.2-172.10.10.254
```

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_pool_04.png)

####  添加用于OpenVPN拨号用的账号     

```shell
[admin@MikroTik] /ip> /ppp profile add name="ovpn-server" local-address=Open_vpn remote-address=Open_vpn use-mpls=default use-compression=default use-encryption=default only-one=default change-tcp-mss=default use-upnp=default address-list="" on-up="" on-down="" 
[admin@MikroTik] /ip> /ppp secret add name=yufeng.li password=xxxxxx profile=ovpn-server service=any
```

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_ppp_profile_05.png)

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_ppp_secret_06.png)

####  启用OpenVPN服务   

```shell
[admin@MikroTik] /ip> /interface ovpn-server server set default-profile=ovpn-server certificate=cert_export_server-sertificate.crt_0 require-client-certificate=yes auth=sha1 cipher=aes128,aes192,aes256 enabled=yes port=1194 mode=iplianjie
```

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_03.png)

#### 添加防火墙允许放行VPN服务   

```shell  
[admin@MikroTik] /ip> /ip firewall filter add chain=input protocol=tcp dst-port=1194 action=accept place-before=0 comment="Allow OpenVPN"
```

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_firewall_08.png)

### RouterOS客户端设置  

#### 证书  

证书开头已创建签名，如果是在服务端创建，此时只需将ca证书、client证书及密钥3个文件上传到客户端。值得注意的仍然是先上传证书再上传key密钥，看到K标志显示。  

#### OpenVPN Client设置    

在```Interface```中添加```OPENVPN Client```，名称ovpn-out1。

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_client_14.png)

几点说明：

1. `Mode` ，这个有两个选项：`IP` 和 `Ethernet`，这表示数据是走layer 3还是layer 2，反映到VPN创建出来的本地虚拟网卡，就是tun还是tap，一般来说OpenVPN都是tun，所以这里是选择 `IP`。如果你使用PPTP，就可以看到虚拟网卡是tap。
2. `User`，这个其实不需要，因为OpenVPN是使用证书来识别client的，每个client都会有一个证书。但是这里ROS需要填一个用户名，所以随便填一个即可。
3. `Profile`，因为在下面会选择加密方式等，所以profile就选default就好，default意思就是按照server的默认设置来。
4. `Certificate`，这里要选择你upload到ROS上的，client的私钥，这个私钥是用来解密数据的。
5. `Auth` / `Cipher`，这个就选成跟server端的配置一致即可。    

#### VPN连接结果  

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_result_16.png)

#### 网络设置  

本次将剩余端口进行桥接。

##### 桥接  

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_ppp_bridge_17.png)

##### DHCP  

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_dhcp_18.png)

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_dhcp_19.png)

##### Address List  

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_address_20.png)

##### Route List  

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_route_21.png)

### 测试  

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_result_22.png)

### 番外  

#### Windows客户端采用OpenVPN GUI    

找到OpenVPN下conf文件夹，下面有```auth.cfg```和```client.ovpn```两个文件

![](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/ros_ovpn/ros_ovpn_window_15.png)

client.ovpn配置如下：

```shell
client
dev tun
proto tcp
remote X.X.X.X 1194      //服务端地址
resolv-retry infinite
nobind
persist-key
persist-tun
#ca ca.crt
#cert client.crt
#key client.key
cipher AES-128-CBC
auth SHA1
auth-user-pass auth.cfg
redirect-gateway def1
verb 4
tls-client
mute 10
remote-cert-tls server
mute-replay-warnings

<ca>
-----BEGIN CERTIFICATE-----
此处粘贴ca证书内容
-----END CERTIFICATE-----
</ca>
<cert>
-----BEGIN CERTIFICATE-----
此处粘贴client证书内容
-----END CERTIFICATE-----
</cert>
<key>
-----BEGIN ENCRYPTED PRIVATE KEY-----
此处粘贴client key内容
-----END ENCRYPTED PRIVATE KEY-----
</key>

```

auth.cfg里面配置服务端secret中配置的用户名密码，第一行写用户名，第二行写密码。