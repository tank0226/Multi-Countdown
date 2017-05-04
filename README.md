# Multi-Countdown 多倒计时器


## 过程
2017年初玩仙境传说手游时，因为刷miniboss赚钱的需求（miniboss打死后30分钟刷新一次），需要频繁用我的apple watch倒计时。

但是一次只能定一个时间，换句话说只能跟踪一个怪的刷新时间。找了一圈没有合适的倒计时工具，那么自己写一个好了。。。。。

就是可以设置多个倒计时器，然后到期后还能根据生存时间计算下次出现时间（例如miniboss出现后平均2分钟就会被灭，那么即便错过一次也大概能估计下次出现时间）。

开始只是单机版，用localstorage将配置存在浏览器本机，但后来发现有两个需求：

1. 电脑配置之后希望手机也能看。
2. 对于公会可以用众包的方式，任何队员找到某小怪出现时间线就可以记录后方便其他人

于是又写了一个服务器端（ASP.NET）。任何人设定一个秘钥就能和其他人共享倒计时，也可以方便跨设备共用。

有了这个之后，基本上只要勤奋点就而已霸单个线的miniboss了……

在设计上我尽可能也避免纯网游用，其实还是可以有其他用处的，但我暂时没想到，嘿嘿。

## 技术说明

HTML项目mc.html用的是bootstrap框架，手机PC自适应，部分设置项必须PC大屏才能设置（删除、修改），一定程度上避免手机误操作。
	
服务器端mc.ashx是ASP.NET代码，将用户配置json内容保存在默认的mc目录下（需要自己新建）。文件名混淆后md5加密，有管理员后门可以设定。

	
## 一些技术细节

主要是在处理团队模式时要考虑互相覆盖的问题，所以团队版提交时会先获取服务器最新数据再更新

## 截图演示

电脑版：
![](https://github.com/zerochocobo/Multi-Countdown/blob/master/snap/pc.png?raw=true)

手机版：
![](https://github.com/zerochocobo/Multi-Countdown/blob/master/snap/mobile.png?raw=true)
