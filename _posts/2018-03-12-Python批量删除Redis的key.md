---
title: Python批量删除Redis的指定key
description: Python批量删除Redis的指定key
categories:

 - Python
 - Redis
tags:
 - Python
 - Redis
---
连接Redis常用的方式有两种：普通连接和连接池，另外的方式还用管道、订阅发布等，这边不采用。

### 普通连接Redis  

```python
import redis   

# 导入redis模块，通过python操作redis 也可以直接在redis主机的服务端操作缓存数据库
r = redis.Redis(host='localhost', port=6379, decode_responses=True)   
# host是redis主机，需要redis服务端和客户端都启动 redis默认端口是6379
# decode_responses=True，写入的键值对中的value为str类型，不加这个参数写入的则为字节类型。
```

### 连接池  

redis-py使用connection pool来管理对一个redis server的所有连接，避免每次建立、释放连接的开销。  

```python
import redis    
# 导入redis模块，通过python操作redis 也可以直接在redis主机的服务端操作缓存数据库

pool = redis.ConnectionPool(host='localhost', port=6379, decode_responses=True)   
# host是redis主机，需要redis服务端和客户端都起着 redis默认端口是6379
r = redis.Redis(connection_pool=pool)
r.set('gender', 'male')     # key是"gender" value是"male" 将键值对存入redis缓存
print(r.get('gender'))      # gender 取出键male对应的值
```

### 模糊匹配   

采用```keys(pattern='*')    ```，所有的key将存入这个list作为结果返回 。 

```
keys(*)           # 匹配数据库中所有key。 
keys(h?llo)       # 匹配hello，hallo和hxllo等。 
keys(h*llo)       # 匹配hllo和heeeeello等。
keys(h[ae]llo)    # 匹配hello和hallo，但不匹配 hillo。  
```

### 采用连接池的完整代码  

```python
import redis    

pool = redis.ConnectionPool(host='localhost', port=6379, decode_responses=True)   
r = redis.Redis(connection_pool=pool)
list_keys = r.keys("SUBJECT*")  # 获取所有SUBJECT开头的key

for key in list_keys:
    r.delete(key)
```

