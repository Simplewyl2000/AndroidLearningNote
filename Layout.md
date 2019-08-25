#关于布局

由于手滑之前的部分没有保存就关掉了所以这里就不补齐了，之后有时间看布局的时候再加上吧


##

###ListView

大概整理了一下基本ListView产生视图的思路

+ 首先准备好要显示的数据集合
+ 将数据集合整合到一个Adapter中去，Adapter中必须实现了getview接口
+ 将adapter整合到listview中去



我们也可以编写自己的adapter，继承于ArrayAdaper即可，其中，为了实现自己不一样的视图展现效果，需要重写必要的接口getView
<br>
<br>

顺带提一下getView的思路

+ 首先获取在对应position的对象的值
+ 之后创建一个LayoutInflater对象并且调用inflate方法动态加载布局，并将改动态加载好的布局作为view返回
+ 在布局中获取对应的控件对象进行具体的资源文件设置
+ 返回view对象



####ListView的优化


1. 可以使用converView，相当于是使用了一个缓存，不用每次都去使用LayoutInflater进行动态加载布局
2. 虽然加载了布局但是每次都需要重新去获取控件的实例这也是十分让费时间的，这个时候我们就将控件的实例也存储起来
	+ 首先使用ViewHold，其中含有这个布局中所用控件
	+ 在每次创建好这个View的时候，若没有之前的缓存View 就把View进行标签设置`view.setTag(ViewTag）`
	
		如果是有缓存的话，就直接将view中的Viewhold实例取出来
	+ 这时候把ViewHolder中的实例进行资源设置



###ReyclerView

这是比ListView更为实用的

但首先需要添加依赖

对于ReclerView的使用

+ 首先跟ListView一样，是需要添加Adapter的

+ 关于RecyclerView的adapter的设置

	+ RecyclerView的adapter处理的对象是ViewHolder类型，也就是说直接就使用了ListView的第三种优化
	+ 在这个adapter中需要定义ViewHolder，其中ViewHolder的内容是需要加载的控件的集合
	+ 其中需要实现三个需要的接口
		+ `onCreateViewHolder`
			这是返回动态加载布局使用的view对象的方法，这个就是加载一下布局即可
		+ `onBindViewHolder`
			设置对应的控件的资源的，获取对应位置的对象，然后设置对应的资源
		+ `getItemCount`
			返回需要加载的数据的长度

+而在活动中加载RecyclerView的方法就跟ListView是一样的了



####使用RecyclerView实现不同的效果

使用的是LayoutManager

####给RecycleView添加响应事件

需要在Adapter中重写onCreateViewHolder方法在其中加入对ViewHolder中的控件进行添加OnclickListener方法，定义响应事件


###制作Nine-Patch

适应屏幕比例时的图片的拉伸
