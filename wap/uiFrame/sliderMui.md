#  图片轮播

基于mui的图片轮播。

<iframe src="./demo/gallery/gallery.html" width="300px" height="220px" frameborder="0" scrolling="no"> </iframe>

使用方法：

1）在页面上预留存放图片轮播`DOM`的容器
```
<div class="banner">
	<!-- 空白节点，作为图片轮播的DOM结构的容器，class属性可以使用任意名字 -->
</div>
```

2）引用轮播图的样式文件`sliderMui.less`

3）引入图片轮播的`js`插件`sliderMui.js`，并调用
```
	//需要轮播的图片数组
	var imgArr = [{
		imgUrl: './1.jpg', 
		linkUrl: 'http://www.baidu.com'
	},
	{
		imgUrl: './2.jpg', 
		linkUrl: 'http://www.baidu.com'
	},
	{
		imgUrl: './3.jpg', 
		linkUrl: 'http://www.baidu.com'
	},
	{
		imgUrl: './4.jpg', 
		linkUrl: 'http://www.baidu.com'
	}];

	//调用Slider方法
	Slider( $('.banner'), imgArr );
	
```

`Slider()`需要两个参数：
	1. 存放轮播DOM结构的容器
	2. 需要轮播的图片数组。

此数组的每一条数据都是一个对象，并有两个属性：
```
	{
		imgUrl: './1.jpg', //图片地址 
		linkUrl: 'http://www.baidu.com' //图片点击跳转的链接
	}
```

之后该插件会生成对应的DOM结构插入`$('.banner')`，`mui`会为此轮播结构添加轮播事件。

