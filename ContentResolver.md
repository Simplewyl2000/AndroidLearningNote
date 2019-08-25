# 内容提供器

实质就是定义一个可以供其他程序访问可以被访问的数据的一个借口


### 运行时权限详解

Andorid中的危险权限一共9组24个


##### 在Android6.0以上其实不能光靠注册安装时候的权限来获得权限，用户有权利去控制运行时权限

1. 首先判断是否拥有权限：

```java

ContextCompat.checkSelPermossion(Context,Manifest.permissin.CALL_PHONE) != PackageManger.PERMISSION_GRANTED

```

2. 若没有，则申请，并且完成对申请结果的反应
```java
ActivityCompat.requestPermission()

```java

@Override
public void onRequestPermissionResult(){
  switch(requsetCode){
    case 1:
          if(grantResult.length>0 && grantResult[0] == PackageManger.PERMISSION_GRANTED)
          {}
          else
          {}

  }

}

```


## 内容提供器

### 使用提供器

#### 查询

1. 首先通过`getContentResolver()`获取一个Cursor对象，然后对数据进行CRUD的操作

  + 获取这个对象则是需先写好一个uri对象（指定需要查找的表）
  + 传入这个uri对象获取Cursor

#### 增删改

通过`getContentResolver.insert(uri,valuse)`等方法来进行增删改
  + values是一个ContentValue对象


### 创建自己的内容提供器

1. 在提供数据的程序中创建一个MyProvider继承于ContentProvider
  + 由于ContentProvider是一个抽象类，其中的六个抽象方法都必须完善
  + 并且需要提供自己的urimatcher，意思就是必须在别人提供了uri之后可以实现，访问到对应的数据
  + 每一个对应的方法都要实现uri匹配
  + manifest文件中需要注册provider


    关于uri匹配
    1. #代表任意长度字符 * 代表任意长度数字
    2. 使用urimatcher去返回对应的判断值
