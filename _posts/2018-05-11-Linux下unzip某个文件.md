---
title: Linux下unzip解压指定文件到指定目录
description: Linux下unzip指定文件到指定目录下，
categories:
 - Linux
tags:
 - Linux
 - unzip
 - zip
---

## unzip查看压缩包中文件
```shell
    unzip -l xxx.zip | grep "aaa"
```
## unzip解压指定文件到指定目录
```shell
    unzip <Your zip file> "*mobile/要解压的文件" -d <要解压的目录> 
```

-l : 小写l;
-d :  -d 参数后面跟上你要解压文件到哪个目录；
