---
title: Sublime Text3在线Install Package失败解决方法
description: 之前Sublime Text3在线Install Package出现失败，采用的手动本地安装插件，今天查看分析了问题，并参考了资料，得到了一个解决方法。
date: 2017-12-23 20:38:16
categories:
 - Sublime
tags:
 - Sublime
---

### Sublime Text 在线安装插件失败   

点击```首选项 >> 插件控制```或按```ctrl+shift+p```，随后输入选择```InstallPackage```  ，出现如下错误；  

![](https://liyufeng.angton.com/sublime000.png)

按``` ctrl+` ```调出Sublime Text控制台，查看有如下错误，提示无法下载channel的json文件。    

```
Package Control: Error downloading channel. Connection refused (errno 12029) during HTTP write phase of downloading https://sublime.wbond.net/channel.json.
Package Control: Error downloading channel. Connection refused (errno 12029) during HTTP write phase of downloading https://packagecontrol.io/channel_v3.json.
error: Package Control

There are no packages available for installation

```

于是网上下载```channel_v3.json```文件于本地，点击```首选项 >> 插件设置 >> Package Control >> 设置-默认```；  

![](https://liyufeng.angton.com/sublime001.png)

将配置中```channels```链接替换成```channels_v3.json```的本地地址；  
```json
"channels": [
    // "https://sublime.wbond.net/channel.json"
    // "https://packagecontrol.io/channel_v3.json",
    "E:/Software/Sublime Text 3x64/Data/channel_v3.json"
],
```
再进行Install Package操作，又报如下错误，按``` ctrl+` ```调出Sublime Text控制台进行查看，提示```schema_version```版本不对。  

```
Package Control: Channel https://packagecontrol.io/channel_v3.json does not appear to be a valid channel file because  the "schema_version" is not a valid number.
error: Package Control

There are no packages available for installation
```

随后修改```channel_v3.json```文件，将```schema_version```修改为2.0 ；    

```json
"schema_version": "2.0",
```

就可以了。  

![](https://liyufeng.angton.com/sublime002.png)  

  

