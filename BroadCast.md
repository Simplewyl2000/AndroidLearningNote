# 广播
---

### 目的

是为了接受系统级消息以及接收其他程序的消息

### 种类

+ 标准广播
+ 有序广播

其唯一区别就在于接收的对象是否有序还是全部一起接收

***



## 接收

### 动态注册

步骤：

1.创建一个消息过滤器
2.写一个Receiver继承于Broadcast
  + 其中重写onReceive方法即可对收到的广播进行相应的处理

ps：获取系统级别的一些信息比如网络环境变化这时是需要一些权限在`AndroidManifest`文件中注册的

```
<user-permision Android:name="android.permision.ACCESS_NETWORK_STATE"
```


### 静态注册

这里的静态注册是指在Manifest文件中注册的Receiver，标签中添加过滤器，然后在对应的类中重写对应的onReceive即可



### 自定义广播（也就是自己的广播，之前一直在接收嘛）

1. 标准广播

  步骤：

  1. 首先静态注册接收器，其中设置广播过滤器，设定自己的广播名称

  2. 创建一个intent对象其中以刚刚设定的广播名称

  3. sendBroadcast

2. 有序广播

  其实差不多，只是在注册接收器的时候设置一个
  `android:priority="XXX"`
  即可


  
