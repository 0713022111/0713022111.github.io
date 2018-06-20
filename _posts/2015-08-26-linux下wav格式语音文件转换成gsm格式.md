---
title: Linux下wav格式语音文件转换为gsm格式
description: Linux下wav格式语音文件转换为gsm格式
categories:
 - Linux
 - Asterisk
tags:
 - Linux
 - Asterisk
---

使用linux自带的```sox```工具转换：
```shell
sox inputfile.wav -r 8000 -c 1 outputfile.gsm
```
注释： inputfile.wav 为转换前文件；
        outputfile.gsm为转换后文件；
        -r 8000 为采样率；
        -c 1 为频道单声道；

转换完成既为GSM格式音频文件。
在wav或者gsm格式音频文件放在/var/lib/asterisk/mohmp3/路径下，playback正常播放；

