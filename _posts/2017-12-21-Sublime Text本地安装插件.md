---
title: Sublime Text本地安装插件
description: 最近需要编辑Asterisk的格式为*.conf的配置文件，但是Sublime Text不支持高亮，于是需要安装插件SublimeAsteriskConfig
date: 2017-12-21 20:38:16
categories:
 - Sublime
 - Asterisk
tags:
 - Sublime
 - Asterisk
---

### Sublime Text 本地安装插件的方法 ###   

Sublime Text的插件绝大多数都托管在Github上，我们使用Package Control搜索、安装插件，实际上就是自动将Github上的插件下载下来，然后放到Sublime Text指定的存放插件的文件夹中；我们也可以手动进行安装，本次所讲的就是手动安装。  

### SublimeAsteriskConfig插件 ###    

#### 第一步 ####    

在github上搜索SublimeAsteriskConfig，也可以通过``` channel_v3.json``` [SublimeAsteriskConfig插件地址](https://github.com/pnlarsson/SublimeAsteriskConfig)，将其下载下来。  

```json
{
    "name": "Asterisk Config",
    "description": "Asterisk *.conf syntax highlight and snippets for SublimeText",
    "authors": [
        "pnlarsson"
    ],
    "homepage": "https://github.com/pnlarsson/SublimeAsteriskConfig",
    "previous_names": [

    ],
    "labels": [
        "language syntax"
    ],
    "readme": "https://raw.githubusercontent.com/pnlarsson/SublimeAsteriskConfig/master/README.md",
    "issues": "https://github.com/pnlarsson/SublimeAsteriskConfig/issues",
    "donate": null,
    "buy": null,
    "releases": [
        {
            "platforms": [
                "*"
            ],
            "sublime_text": "*",
            "version": "0.9.3",
            "url": "https://codeload.github.com/pnlarsson/SublimeAsteriskConfig/zip/v0.9.3",
            "date": "2017-11-01 16:05:02"
        }
    ]
},
```

注意这个文件夹的名字就是将来在Sublime Text插件包中要显示的名字（也可以重命名，但不影响使用）。  

#### 第二步 ####  

然后打开Sublime Text，点击工具栏中的Preferences -> Browse Packages（中文：首选项-> 浏览插件），即可打开Packages文件夹。将刚刚的SublimeAsteriskConfig文件夹复制到Packages文件夹内，重启Sublime Text后，插件就已经装好了。  

#### 结果   ####    

![.conf文件高亮](https://liyufeng.angton.com/sublime_asterisk.png)

#### 附件 ####    

[channel_v3.json](https://liyufeng.angton.com/channel_v3.json)  