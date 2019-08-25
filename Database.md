# 数据的持久化存储

## 文件存储的方式

其实很简单，就只是将数据以文件的形式存储起来，然后需要的时候再取出来


```java
FileOutputStream out = null;
BufferedWriter writer = null;

out = openFileOutput("data",Context.MODE_PRIVATE);
writer = new BufferedWriter(new OutputStreamWriter(out));
writer.write(data);
```

查看文件只需要用Android studio中的File Explore即可

---

相反，需要数据的时候从文件中进行读取即可


## SharedPreferences存储

获取sharedpreferences其实跟文件存储的区别不大

区别只是在于SP提供的接口更加的人性化，系统一些而已


### 使用过程

1. 获取SP中的editor对象，这里有三种方法，不一一列举

2. 使用editor中的多个重载方法对不同数据类型进行存储，之后调用`editor.apply()`

3. 获取对应的SP对象之后按照键值来获取数据


## SQlite数据库存储（我jio得不行）

这实际上就是使用Android中内置的轻量级数据库SQlite

### 使用步骤
1. 准备好建库建表语言
    ```java
      public static final String CREATE_BOOK = "create table Book("
      + "id integer primary key autoincrement"
      + "author text)";

    ```

2. 重写onCreat方法，使得在创建的时候可以执行建表语言

3. 在主活动中新建一个`MyDatabaseHelper`对象（继承于SQliteOpenHelper）指定建立的数据库名称即可

  + 注意这里需要重写两个方法`onCreat()`和`onUpgrade()`

  + 在建库的时候传入的版本号大于之前的就会调用onUpdate()方法

  + 很憨批的一件事情是，如果存在了之前的表，就需要删除才能重新更新这张表，爷吐了

### 关于使用

+ 添加数据
  + 使用contentValue来进行input，调用db.insert()

+ 更新数据
  + 使用contentValue来进行input，调用db.Update()

+ 删除数据
  + 直接调用db.deletel()

+ 查询数据
  + 要定义一个光标对象，调用db.qury()指向该位置
  + 使用cursor.moveToXXX,指向该指向的位置

## LitePal（哥中哥）

### 使用方法（舒服的呀痞）

1. 首先配置依赖

2. 再创建litepal.xml文件，在该文件中指定数据库的名字，并且指定版本号，指定对应映射的类

3. 在application中设置name属性

4. 编写在2中提到的Java Bean

5. 主活动中使用Connector.getDataBase即可

***

之后若是希望修改表单只需要

+ 改动这个对应的类

+ 使用set方法

+ 调用DateSupport类中的静态方法即可

+ 注意若是修改表单格式，注意更新版本号
