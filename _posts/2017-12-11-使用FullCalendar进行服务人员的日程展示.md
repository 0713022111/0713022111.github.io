---
title: 使用FullCalendar进行服务人员的日程展示
description: 最近系统中需要将服务人员的每天服务事项采用日历的形式进行展示，于是想到了fullcalendar；同时由于事项内容字数较多，无法完全展示，采用鼠标事件eventMouseover和eventMouseout实现鼠标移动到单个事项（event）位置上时出现标签框展示实际内容。
date: 2017-12-11 21:23:26
categories:
 - Web
 - Javascript
tags:
 - js
 - fullcalendar
---

### 引入FullCalendar  

使用FullCalendar的第一步是引用css和js文件：

```html  
<link href='../fullcalendar.min.css' rel='stylesheet' />
<link href='../fullcalendar.print.min.css' rel='stylesheet' media='print' />
<script src='../lib/moment.min.js'></script>
<script src='../lib/jquery.min.js'></script>
<script src='../fullcalendar.min.js'></script>
```

### 初始化  

在页面加载完成之后进行fullCalendar的初始化

```javascript
$(document).ready(function() {
    $('#calendar').fullCalendar({
        defaultDate: '2017-12-11',
        // defaultDate: new Date(),
        editable: true,
        eventLimit: true, // allow "more" link when too many events
        locale: "zh-cn",    //设置中文
        editable: false,
        selectable: false,
        selectHelper: true,
        slotEventOverlap:false,//视图中的事件是否可以重叠
        header: {
            left: 'prev,next,today',
            center: 'title',
            right: 'month,agendaWeek,agendaDay,list'
        },
        buttonText: {
            today: '今天',
            month: '月视图',
            week: '周视图',
            day: '日视图',
            list: '列表'
        },
    });
});
```

### 设置中文显示  

采用中文显示星期项目、年月日等，需引入locale中的```zh-cn.js```  文件  ，同时初始化时设置```locale: "zh-cn"```  

```html  
<script src='../locale/zh-cn.js'></script>
```

### 设置容器  

代码里面指定初始化一个 ```id='calendar'``` 容器，所以必须在body中加入如下代码：

```javascript
<div id='calendar'></div>
```

### 假设的events日程事件   

```json
events: [
    {
        title: '【用户：葛维俊】;【服务队员：张秀芬】;【服务内容：室内地面清扫,测量血压：每周一次，记录健康状况,购物并送货上门：粮油米面、生活用品、家居产品、瓜果蔬菜、常用药品】;【金额：50】',
        start: '2017-12-01T14:00:00',
        end: '2017-12-01T16:00:00',
        color:'#FFB90F'
    },
    {
        title: '【用户：王汝德】;【服务队员：朱美娟】;【服务内容：室内地面清扫,陪同聊天：给老人读报，聊天，分享经历见闻】;【金额：60】',
        start: '2017-12-07T15:00:00',
        end: '2017-12-07T16:00:00',
        color:'#FFB90F'

    },
    {
        title: '【用户：黄卓如】;【服务队员：王晓红】;【服务内容：室内地面清扫,通下水道,墙面局部污渍擦拭,厨房保洁：玻璃、厨房台面（油烟机除外）,厨房保洁：玻璃、厨房台面（油烟机除外）】;【金额：100】',
        start: '2017-12-10T10:30:00',
        end: '2017-12-10T12:00:00',
        color:'#FFB90F'
    },

    {
        id: 999,
        title: '【用户：卞文姑娘】;【服务队员：葛旗】;【服务内容：室内地面清扫,厨房保洁：玻璃、厨房台面（油烟机除外）,清洗鞋子,测量血压：每周一次，记录健康状况】;【金额：70】',
        start: '2017-12-09T09:00:00',
        end: '2017-12-09T11:00:00',
        color:'#FFB90F'
    },
    {
        id: 999,
        title: '【用户：张翠英】;【服务队员：葛旗】;【服务内容：室内地面清扫,厨房保洁,厨房保洁,测量血压：每周一次，记录健康状况】;【金额：90】',
        start: '2017-12-16T16:00:00'
    },
    {
        title: '【用户：任贵英】;【服务队员：冯美芳】;【服务内容：室内地面清扫,墙面局部污渍擦拭,陪同聊天：给老人读报，聊天，分享经历见闻】;【金额：60】',
        start: '2017-12-11T09:00:00',
        color:'#9F79ff'

    },
    {
        title: '【用户：何广千】;【服务队员：袁骥华】;【服务内容：清洗纱窗,测量血压：每周一次，记录健康状况,刮胡子】;【金额：50】',
        start: '2017-12-12T10:30:00',

    },
    {
        title: '【用户：张茂华】;【服务队员：蒋美芳】;【服务内容：室内地面清扫,清洗纱窗,测量血压：每周一次，记录健康状况】;【金额：50】',
        start: '2017-12-12T12:00:00'
    },
    {
        title: '【用户：徐有英】;【服务队员：黄桂明】;【服务内容：室内地面清扫,厨房保洁：玻璃、厨房台面（油烟机除外）,清洗鞋子】;【金额：50】',
        start: '2017-12-12T14:30:00'
    },
    {
        title: '【用户：王元庆】;【服务队员：黄桂明】;【服务内容：简单指甲修剪,室内地面清扫,清洗纱窗】;【50】',
        start: '2017-12-12T17:30:00'
    },
    {
        title: '【用户：胡广信】;【服务队员：袁骥华】;【服务内容：室内地面清扫,清洗鞋子,测量血压：每周一次，记录健康状况】;【金额：50】',
        start: '2017-12-15T17:30:00'
    },
    {
        title: '【用户：王义有】;【服务队员：郭丹】;【服务内容：室内地面清扫,洗发、理发(不包括染发、烫发),冰箱、微波炉清洗,衣物清洗机洗、漂水、晾晒】;【金额：80】',
        start: '2017-12-16T17:30:00'
    },
    {
        title: '【用户：李风姑娘】;【服务队员：郭丹】;【服务内容：杂物归类、收拾衣物、整理房间、被褥晾晒,洗发、理发(不包括染发、烫发),陪同聊天：给老人读报，聊天，分享经历见闻,厨房保洁：玻璃、厨房台面（油烟机除外）】;【金额：60】',
        start: '2017-12-17T17:30:00'
    },
    {
        title: '【用户：季有姑娘】;【服务队员：马玉华】;【服务内容：修脚、修趾甲,简单指甲修剪,室内地面清扫,陪同聊天：给老人读报，聊天，分享经历见闻,测量血压：每周一次，记录健康状况】;【金额：130】',
        start: '2017-12-19T17:30:00'
    },
    {
        title: '【用户：黄卓如】;【服务队员：王晓红】;【服务内容：室内地面清扫,通下水道,墙面局部污渍擦拭,厨房保洁：玻璃、厨房台面（油烟机除外）,厨房保洁：玻璃、厨房台面（油烟机除外）】;【金额：100】',
        start: '2017-12-20T10:30:00'
    },
    {
        title: '【用户：黄志锦】;【服务队员：周亚秦】;【服务内容：室内地面清扫,杂物归类、收拾衣物、整理房间、被褥晾晒,陪同聊天：给老人读报，聊天，分享经历见闻,测量血压：每周一次，记录健康状况】;【金额：80】',
        start: '2017-12-21T07:30:00'
    },
    {
        title: '【用户：耿万汉】;【服务队员：周亚秦】;【服务内容：室内地面清扫,厨房保洁：玻璃、厨房台面（油烟机除外）,杂物归类、收拾衣物、整理房间、被褥晾晒,陪同聊天：给老人读报，聊天，分享经历见闻】;【金额：80】',
        start: '2017-12-22T11:30:00'
    },
    {
        title: '【用户：胡学诗】;【服务队员：周亚秦】;【服务内容：修脚、修趾甲,室内地面清扫,陪同聊天：给老人读报，聊天，分享经历见闻】;【金额：90】',
        start: '2017-12-23T14:30:00'
    },
    {
        title: '【用户：王德中】;【服务队员：马玉华】;【服务内容：室内地面清扫,陪同聊天：给老人读报，聊天，分享经历见闻,测量血压：每周一次，记录健康状况,刮胡子】;【金额：80】',
        start: '2017-12-24T17:30:00'
    },
    {
        title: '【用户：朱瑞明】;【服务队员：马水平】;【服务内容：陪同聊天：给老人读报，聊天，分享经历见闻,刮胡子】;【金额：40】',
        start: '2017-12-25T20:00:00'
    },
    {
        title: '【用户：唐兰英】;【服务队员：马水平】;【服务内容：洗发、理发(不包括染发、烫发),陪同聊天：给老人读报，聊天，分享经历见闻】;【金额：35】',
        start: '2017-12-26T07:00:00'
    },
    {
        title: '【用户：唐建成】;【服务队员：马玉华】;【服务内容：室内地面清扫,厨房保洁：玻璃、厨房台面（油烟机除外）,薄衣物清洗手洗,陪同聊天：给老人读报，聊天，分享经历见闻,测量血压：每周一次，记录健康状况,刮胡子】;【金额：108】',
        start: '2017-12-28'
    }
],
```

### 设置鼠标事件  

#### eventMouseover事件  

```javascript
eventMouseover: function(calEvent, jsEvent) {
    var tcontent = calEvent.title.split(';');
    console.log(tcontent);
    var tooltip = '<div class="tooltipevent" style="width:230px;height:auto;background:#ffffffb0;position:absolute;z-index:10001;border:1px solid black;font-size:12px;">'+ '【开始时间：'+ calEvent.start.format("YYYY-MM-DD HH:mm") + '】'+ '</br>';
    if (calEvent.end) {
        tooltip += '【结束时间：' + calEvent.end.format("YYYY-MM-DD HH:mm") + '】'+ '</br>';
    }
    for (var i = 0; i <=tcontent.length - 1; i++) {
        tooltip += tcontent[i] + '</br>';
    }
    tooltip += '</div>';			    
    var $tooltip = $(tooltip).appendTo('body');

    $(this).mouseover(function(e) {
        $(this).css('z-index', 10000);
        $tooltip.fadeIn('500');
        $tooltip.fadeTo('10', 1.9);
    }).mousemove(function(e) {
        $tooltip.css('top', e.pageY + 10);
        $tooltip.css('left', e.pageX + 20);
    });
},
```

#### eventMouseout事件  

```javascript
eventMouseout: function(calEvent, jsEvent) {
    $(this).css('z-index', 8);
    $('.tooltipevent').remove();
},
```

### 页面效果  

<video id="video" autoplay="autoplay" controls="" preload="none" style="width:100%; height:100%; object-fit: fill">
         <source id="mp4" src="http://liyufeng.angton.com/fullcalendar_demo.mp4" 
             type="video/mp4">
</video>  