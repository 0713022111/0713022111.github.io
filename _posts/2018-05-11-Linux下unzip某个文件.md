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
e.g.
```shell
    [root@iZb download]# unzip -l angton-v2.2.9.zip |grep "zip"
```

    Archive:  angton-v2.2.9.zip
        868  05-10-2018 20:00   angton-v2.2.9/sql/上线sql.zip

## unzip解压指定文件到指定目录
```shell
    unzip <Your zip file> "*mobile/要解压的文件" -d <要解压的目录> 
```
e.g.
```shell 
    [root@iZb download]# unzip angton-v2.2.9.zip "*/sql/上线sql.zip" -d ../download/
```

    Archive:  angton-v2.2.9.zip
    angton-v2.2.9/sql/上线sql.zip:  mismatching "local" filename (angton-v2.2.9/sql/上线sql.zip),
         continuing with "central" filename version
    extracting: ../download/angton-v2.2.9/sql/上线sql.zip  

-l : 小写的l;

-d :  -d 参数后面跟上你要解压文件到哪个目录;
