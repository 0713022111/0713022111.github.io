---
title: Python+Selenium实现开机启动自动登陆系统监控平台
description: Python+Selenium实现开机启动，打开谷歌浏览器自动登陆系统，打开监控平台。
date: 2018-07-02 23:28:23
categories:
 - Python  
tags:
 - Python
 - Selenium
---  
### 准备安装包  

序号 | 类目 | 版本  
:-: | :-: | :-:   
1 | Python | 3.7.0  
2 | selenium | 3.13.0  
3 | Google Chrome | 68.0  
4 | ChromeDriver | 2.39  
5 | os | window7  
  
### 安装  
#### 安装python
官网下载Python安装包，进行安装。需要对底下的```Add Python3.7 to PATH```进行打勾，然后选择Install Now。  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/selenium_002.png "安装Python3.7")   
![Alt text](http://p92ijvt1x.bkt.clouddn.com/selenium_003.png "安装Python3.7完成")  
#### 安装selenium  
调出命令提示符，使用```pip3 install selenium```命令安装selenium。 
![Alt text](http://p92ijvt1x.bkt.clouddn.com/selenium_004.png "安装selenium")  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/selenium_005.png "安装selenium完成")  
#### 安装ChromeDriver  
[ChromeDriver官方下载点](https://sites.google.com/a/chromium.org/chromedriver/downloads)  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/selenium_101.png "选择浏览器对应的webdriver")  
将下载下来的```chromedriver.exe```文件拷贝到python的安装目录下。  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/selenium_006.png "拷贝到python的安装目录")
#### 编写脚本  
编写脚本，名为chrome.py。  
```python  
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import time

browser = webdriver.Chrome()
browser.get("http://XXX.XXX.XXX.XXX:8080/login")
time.sleep(2)
name = browser.find_element_by_name("username")
name.send_keys("USERNAME")
passwd = browser.find_element_by_name("password")
passwd.send_keys("PASSWORD")
login_button = browser.find_elements_by_class_name("button")[0]
login_button.click()
time.sleep(2)
second_url = 'http://XXX.XXX.XXX.XXX:8080/web/#/homeService/callCenter'
browser.get(second_url)
body = browser.find_elements_by_tag_name("html")[0]
time.sleep(1)
#键盘F11开全屏，谷歌浏览器不起作用，貌似F几的键都不起作用
#body.send_keys('\ue03b')
#键盘END键，谷歌浏览器起作用
#body.send_keys('\ue010')
#browser.set_window_size(1280,800)
browser.maximize_window()  
```  
附个Keys按键。  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/selenium_008.png "Keys按键一览")
最后想弄个```F11```全屏的，结果不起作用，此处记载，后期寻法解决。到脚本所在目录下执行脚本。  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/selenium_007.png "执行脚本")  
执行效果如下。  
![Alt text](http://p92ijvt1x.bkt.clouddn.com/IMG_3195.GIF "自动化效果")  
#### 随机启动运行脚本  
将脚本拷贝到```启动```目录下，就会随机启动执行脚本。
![Alt text](http://p92ijvt1x.bkt.clouddn.com/selenium_009.png "脚本放置到启动目录")  
### 题外  
原先的谷歌浏览器版本比较低，所以卸载旧的，出现点击新版本的安装包无反应，结果是卸载不彻底，注册表清理不干净的问题，最后附上清除.reg文件。  
[谷歌注册表彻底删除.reg](http://p92ijvt1x.bkt.clouddn.com/%E8%B0%B7%E6%AD%8C%E6%B3%A8%E5%86%8C%E8%A1%A8%E5%BD%BB%E5%BA%95%E5%88%A0%E9%99%A4.reg)  

