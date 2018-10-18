# 图片查看器

框架提供了点击图片后，将图片放大显示，并可以任意缩放图片查看的功能。

效果： 
 
<iframe src="./demo/zoomFn/zoomFn.html" width="600px" height="400px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>

说明：

1. 需要引入`Zoomfn.js`和`Zoomfn.css`

2. 需要在`html`中添加`DOM`结构

```
<!-- 图片放大 -->
<div class="Zoomfn">
	<div class="mask"></div>
	<i class="iconfont closebtn">&#xe631;</i>
    <div class="enlargebox">
    	<img class="enlarge" src="">
    </div>
</div>
```          

3. 页面打开时，对该组件进行初始化

```
$("***").Zoomfn();

```

`$(***)`为需要绑定点击放大的图片`DOM`节点      