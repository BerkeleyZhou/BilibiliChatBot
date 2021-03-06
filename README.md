# Bilibili Chat Bot 介绍&使用说明

## 概述

Bilibili Chat Bot（后文简称BCB）是一个基于bilibili私信API的自动化工具

在这里，你仅需要几行代码就能够实现非常复杂的自动化逻辑

## 和Bilibili自带“自动回复”功能的区别和BCB的优势

BCB最大的优点是高度可自定义话和强大的可扩展性

在Bilibili私信的“自动回复”中，用户只能创建精准回复或者模糊回复一类的简单功能，而通过BCB，你可以自定义文字识别模式，无论是关键词识别，还是正则表达式，甚至是使用强大的第三方人工智能API进行语义分析都不在话下。

除此之外，BCB还会在未来的开发中提供更多极为强大的功能，包括，查询私信用户的粉丝数、关注数；检查发私信者是否关注了你；检查发私信者是否转发了某条动态等等

## 实现原理

最基本的实现逻辑就是调用Bilibili的私信api，接收和发送私信。

但是，除此之外，我向项目中引入了反射系统和生命周期系统，用户仅需要编写简单的逻辑代码交给主程序反射执行，便可实现强大复杂的功能

BCB中的生命周期参考了Unity引擎的生命周期系统，两者开发逻辑几乎一样

BCB中的生命周期目前逻辑如下（14/6/2020）：

![image](https://github.com/BerkeleyZhou/BilibiliChatBot/blob/master/ReadmeResource/Annotation%202020-06-14%20202959.jpg)

## 演示

现在画面中左边的代码即逻辑代码TestBehaviour，如同在Unity游戏引擎中脚本需要继承MonoBehaviour类一样，BCB中的逻辑代码需要继承ChatBehaviour类

![image](https://github.com/BerkeleyZhou/BilibiliChatBot/blob/master/ReadmeResource/TestBehaviour_show.gif)

编写好的ChatBehaviour逻辑代码需要放入Modules等待主程序反射

然后启动主程序，可以看到每秒钟会进行一次Update更新，每五秒中会检查一次聊天记录Session列表

如果有新用户发送消息，会获得新用户的Session信息，包括UID，seqno信息等等

![image](https://github.com/BerkeleyZhou/BilibiliChatBot/blob/master/ReadmeResource/ChatEngine_TestBehaviour_show.gif)

在这个案例中，我们进行了简单的逻辑判断，如果用户发送的信息是“测试语句1”，我们就回复“收到消息“测试语句1”，自动回复”