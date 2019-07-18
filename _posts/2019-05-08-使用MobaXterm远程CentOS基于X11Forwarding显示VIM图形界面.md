---
title: 使用MobaXterm远程CentOS基于X11-Forwarding显示VIM图形界面
description: 使用MobaXterm远程CentOS基于X11Forwarding显示VIM图形界面
date: 2019-05-08 23:28:23
categories:
 - CentOS
tags:
 - CentOS
 - X11Forwarding  
---
#### 安装 X11 Forwarding 相关软件    

```linux  
[root@lykjcloud-002 ~]# yum install xorg-x11-xauth xorg-x11-fonts-* xorg-x11-font-utils xorg-x11-fonts-Type1 xclock
```

#### 启用 X11 Forwarding  

```linux  
[root@lykjcloud-002 ~]# vim /etc/ssh/sshd_config
```

将 X11Forwarding 和 X11UseLocalhost 前面的 # 去掉，并将 X11Forwarding 设置为 yes，X11UseLocalhost 设置为 no。  

```linux  
#AllowAgentForwarding yes
#AllowTcpForwarding yes
#GatewayPorts no
X11Forwarding yes
#X11DisplayOffset 10
#X11UseLocalhost yes
X11UseLocalhost no
#PermitTTY yes
```

#### 重启 sshd 服务  

```linux  
[root@lykjcloud-002 ~]# systemctl restart sshd
```

#### MobaXterm远程连接服务器  

连接服务器后，出现如下 X11-forwarding 和 DISPLAY 这两项都打上了绿色的勾，代表设置成功了。  

```linux  
     ┌────────────────────────────────────────────────────────────────────┐
     │                        • MobaXterm 11.0 •                          │
     │            (SSH client, X-server and networking tools)             │
     │                                                                    │
     │ ➤ SSH session to                                │
     │   • SSH compression : ✔                                            │
     │   • SSH-browser     : ✔                                            │
     │   • X11-forwarding  : ✔  (remote display is forwarded through SSH) │
     │   • DISPLAY         : ✔  (automatically set on remote server)      │
     │                                                                    │
     │ ➤ For more info, ctrl+click on help or visit our website           │
     └────────────────────────────────────────────────────────────────────┘

```

#### 验证  

```linux  
[root@lykjcloud-002 ~]# xclock
```

![xclock](https://liyufeng.angton.com/xclock.png)

#### 安装gui-vim编辑器  

```linux  
[root@lykjcloud-002 ~]# yum install gvim
```

#### 验证  

```linux  
[root@lykjcloud-002 ~]# gvim baidu_jsonp_test.html
```

![x11](https://liyufeng.angton.com/x11.png)

![x11](https://dihuaiying.oss-cn-shanghai.aliyuncs.com/x11.png)

   

