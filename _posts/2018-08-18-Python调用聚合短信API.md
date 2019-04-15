---
title: Python请求调用聚合短信API
description: Python请求调用聚合短信API,官网的代码示例采用的是Python2,本文示例包括了采用Python3的代码示例。
date: 2018-08-18 22:32:28
categories:
 - Python  
tags:
 - Python
 - urllib  
---
 

**接口地址：**http://v.juhe.cn/sms/send

**返回格式：**json/xml

**请求方式：**http get/post

**请求示例：**http://v.juhe.cn/sms/send?mobile=手机号码&tpl_id=短信模板ID&tpl_value=%23code%23%3D654654&key=

> 请求参数说明：  


| 名称      | 必填 | 类型   | 说明                                                         |
| --------- | ---- | ------ | ------------------------------------------------------------ |
| mobile    | 是   | string | 接收短信的手机号码                                           |
| tpl_id    | 是   | int    | 短信模板ID，请参考个人中心短信模板设置                       |
| tpl_value | 是   | string | 变量名和变量值对，如：#code#=431515，整串值需要urlencode，比如正确结果为：%23code%23%3d431515。如果你的变量名或者变量值中带有#&=中的任意一个特殊符号，请先分别进行utf-8 urlencode编码后再传递，[详细说明>](http://www.juhe.cn/news/index/id/50) |
| key       | 是   | string | 在个人中心->我的数据,接口名称上方查看                        |
| dtype     | 否   | string | 返回数据的格式,xml或json，默认json                           |

> 官网请求代码示例（采用的Python2）：[链接地址](https://www.juhe.cn/docs/api/id/54)

```python 
#!/usr/bin/python
# -*- coding: utf-8 -*-
import json, urllib
from urllib import urlencode

url = "http://v.juhe.cn/sms/send"
params = {
    "mobile": "13429667914",  # 接受短信的用户手机号码
    "tpl_id": "111",  # 您申请的短信模板ID，根据实际情况修改
    "tpl_value": "#code#=1235231&#code#=哈哈",  # 您设置的模板变量，根据实际情况修改，多项采用&拼接
    "key": "您申请的ApiKey",  # 应用APPKEY(应用详细页查询)
}
params = urlencode(params)
f = urllib.urlopen(url, params)
content = f.read()
res = json.loads(content)
if res:
    print(res)
else:
    print("请求异常")
 
```

> 返回参数说明：

| 名称       | 类型   | 说明     |
| ---------- | ------ | -------- |
| error_code | int    | 返回码   |
| reason     | string | 返回说明 |

> JSON返回示例：

```json
/****失败示例**/
{
    "reason": "错误的短信模板ID,请通过后台确认!!!",
    "result": [],
    "error_code": 205402
}

/****成功示例**/
{
    "reason": "短信发送成功",
    "result": {
        "count": 1, /*发送数量*/
        "fee": 1, /*扣除条数*/
        "sid": "23d6bc4913614919a823271d820662af" /*短信ID*/
    },
    "error_code": 0 /*发送成功*/
}
```

> Python3代码：  

```python  
#!/usr/bin/python
# -*- coding: utf-8 -*-
import json
from urllib import request
from urllib.parse import urlencode, quote_plus

url = "http://v.juhe.cn/sms/send"
params = {
    "mobile": "13429667914",  # 接受短信的用户手机号码
    "tpl_id": "111",  # 您申请的短信模板ID，根据实际情况修改
    "tpl_value": "#memberName#=狄怀英&#appointmentTime#=打扫&#consume#=100&#fbalance#=100&#pbalance#=0",  # 您设置的模板变量，根据实际情况修改
    "key": "秘密",  # 应用APPKEY(应用详细页查询)
}

params = urlencode(params, quote_via=quote_plus).encode('utf-8')
with request.urlopen(url, params) as f:
    content = f.read()
res = json.loads(content)
if res:
    print(res)
else:
    print("请求异常")

```

> 返回JSON:  

```json
{'reason': '操作成功', 'result': {'sid': '1720415102011028900', 'fee': 1, 'count': 1}, 'error_code': 0}
```

