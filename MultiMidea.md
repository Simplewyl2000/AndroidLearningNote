# 多媒体

### 通知

跟其他很多系统服务一样，要先获取manager，再创建一个notification对象，调用manager创建这样一个活动

#### 注意，在设置通知震动是需权限的
例如：
```java
Notification nocification = new NotificationCompat.Bulider(context,channel)
                              .setContentTitle("This is content title")
                              .setContentText("")
                              .setSmallIcon(R.drwaable.small)
                              .setautoconceal(true)
                              .setContentIntent(pi)
                              .setVibrate(new long[]{0,1000,0,1000})
                              .setLight()
                              .bulid();
```


### 摄像头和相册

此处省略，具体调用过程在使用时候查询

+ 注意存SD卡是需要申请权限的


### 播放音频，视频

* API很齐全，介绍几个基础的
  ```java
  start()
  pause()
  resume()
  seekTo()
  ```
