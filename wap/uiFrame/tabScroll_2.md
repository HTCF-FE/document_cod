# 导航上的按钮数据确定时

此时可以有两种实现方式：

1. 请看《导航上的按钮数据不确定时》篇，使用`js`文件`tabScroll.js`和样式文件`tabScroll.less`实现

2. `html、css、js`结合实现

这里只讲第二种方式~

如图：

![PNG](./img/tabScroll_2.png)

### DOM结构

```
<div class="mui-slider">
	<div class="mui-slider-indicator mui-segmented-control mui-segmented-control-inverted">
		<a class="mui-control-item mui-active" href="#item1">已持仓<span></span></a>
		<a class="mui-control-item" href="#item2">处理中<span></span></a>
		<a class="mui-control-item" href="#item3">已赎回</a>
	</div>
	<div class="mui-slider-group" id="drapUpWrapper">
		<div id="item1" class="mui-slider-item mui-control-content mui-active">
		</div>
		<div id="item2" class="mui-slider-item mui-control-content">
		</div>
		<div id="item3" class="mui-slider-item mui-control-content">
		</div>					
	</div>
</div>
```

说明：

以可滑动区域的数量为三个的情况举例：

1. 滑动容器`mui-slider`

2. 导航`mui-slider-indicator mui-segmented-control mui-segmented-control-inverted`，这三个`class`需要同时存在

3. 导航里面是`a`标签形式的导航标签，`class`为`mui-control-item`，显示的第一个导航需要添加`class`为`mui-active`，有几个导航标签就有几个`a`标签，`href`属性需要和下面的对应区域的`id`值对应

4. `a`标签内除了导航的文案，还有`span`标签，作为两个标签中间的分隔竖线，因此最后一个`a`标签里是没有`span`的

5. `mui-slider-group`是滑动区域的容器

6. `mui-slider-group`的下一级`div`对应滑动区域，`class`为`mui-slider-item mui-control-content`，当前的区域添加`class`为`mui-active`

### CSS样式

需要引入`tabScroll_2.less`

### JS

`js`有两个步骤

1. `mui`初始化

```
mui.init();
```

2. 初始化左右滑动插件

```
$("#slider").on("slide",function(e){
			
})	

```

说明：

`$('#slider')`是左右滑动组件的容器

`function`是滑动后执行的回调函数，可以用`e.detail.slideNumber`获取当前的区域索引