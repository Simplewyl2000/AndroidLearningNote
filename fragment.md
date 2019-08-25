# 碎片

### 目的

+ 使得app在平板上依旧可以美观

### 定义

可以看成是一种嵌入在活动中的UI片段

换句话说是一个迷你型的活动

### 使用

其实在使用的时候跟活动真的很像

每次写一个碎片都是需要他的class文件需要编写其的onCreat方法等等，加载其布局

在其关联的活动布局文件中调用`fragment`标签即可，在其属性中添加android：name="对应的碎片名称"


### 特点

可以动态加载

+ 创建一个fragmentManager
+ 利用创建的fragmentManager创建一个transition对象
+ 使用这个transition对特定的对象改变布局

其中，可以调用addToBackStack()方法对切换了的布局进行返回


---

### 碎片与活动之间的通信

只需要使用getFragmentManager().findViewById()方法来找到碎片即可

而对于活动只需要getActivity()

获取了各自的实例想要互相操作就很简单了

### 碎片的生命周期

1.运行状态

2.暂停状态

3.停止状态

	+ 活动被停止
	+ 被remove但是有addBackToStack

4.销毁状态

---

### 使用限定符

在res中创建一个layout-XXX文件夹

这个XXX就是限定符

在layout-XXX中也是使用相同的布局命名

模拟器会自动根据设备来判断使用哪个布局
