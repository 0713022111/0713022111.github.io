---
title: Sublime Text3插件Color Highlight安装无反应
description: 安装插件Color Highlight使颜色高亮显示
date: 2017-12-28 20:38:16
categories:
 - Sublime
tags:
 - Sublime
---

  通过```Install Package```安装好插件```Color Highlight```后，随后点击```首选项 >> 插件设置 >> Color Highlight Settings ```对```User```进行配置，此配置将会在sublime text启动时加载而忽略掉```Default```配置；    

![](https://liyufeng.angton.com/color_hightlight.png)

配置完后重启Sublime Text3，颜色没有显示语法高亮；调出控制台查看，报如下错误：  

```
Traceback (most recent call last):
  File "E:\Software\Sublime Text 3x64\Data\Packages\Color Highlight\ColorHighlight.py", line 984, in _update_view
    highlight_colors(view, **kwargs)
  File "E:\Software\Sublime Text 3x64\Data\Packages\Color Highlight\ColorHighlight.py", line 592, in highlight_colors
    colorizer.setup_color_scheme(view_settings)
  File "E:\Software\Sublime Text 3x64\Data\Packages\Color Highlight\colorizer.py", line 259, in setup_color_scheme
    content = self.color_scheme.content()
  File "E:\Software\Sublime Text 3x64\Data\Packages\Color Highlight\colorizer.py", line 102, in content
    content = read_package(self.path)
  File "E:\Software\Sublime Text 3x64\Data\Packages\Color Highlight\colorizer.py", line 59, in read_package
    res = f.read()
UnicodeDecodeError: 'gbk' codec can't decode byte 0x92 in position 3656: illegal multibyte sequence
```

分析为主题选择有问题，重新选个主题，ok。  

![](https://liyufeng.angton.com/color_hightlight001.png)