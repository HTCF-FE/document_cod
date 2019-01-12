# 图片轮播

框架提供了图片轮播组件，需要引入`Slider.js`。

![PNG](./img/Slider.png)

使用方法：

1）在页面上预留存放图片轮播`DOM`的容器
```
<div id="banner">
	<!-- 空白节点，作为图片轮播的DOM结构的容器 -->
</div>
```

2）引用轮播图的样式文件`Slider.less`

3）引入图片轮播的`js`文件`Slider.js`，并调用
```
	//需要轮播的图片数组
	var imgArr = [{
		src: './1.jpg', 
		url: 'http://www.baidu.com'
	},
	{
		src: './2.jpg', 
		url: 'http://www.baidu.com'
	},
	{
		src: './3.jpg', 
		url: 'http://www.baidu.com'
	},
	{
		src: './4.jpg', 
		url: 'http://www.baidu.com'
	}];

	//初始化轮播图，#banner为预留的轮播图容器
    $('#banner').Slider({
        type:1,  
        img:imgArr //轮播的图片
    }); 
	
```

本组件提供4种轮播方式：透明度切换、上下、左右、3D。使用时需要传递`type`表示使用哪种轮播方式。

组件会生成对应的`DOM`结构插入`$('#banner')`。

