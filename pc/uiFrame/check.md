# 复选框

效果如下：

<iframe src="./demo/check/check.html" width="400px" height="240px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>


使用方式：

1. 引入`check.css`

2. `DOM`结构

```
方式一：
<div class="type_1">
	<!-- 未选中 -->
	<i class="iconfont checkBox">&#xe648;</i>  
	<span class="txt">点击这里查看效果</span>
</div>
<div class="type_1">
	<!-- 选中 -->
	<i class="iconfont checkBox select">&#xe647;</i>  
	<span class="txt">点击这里查看效果</span>
</div>


方式二：
<div class="type_2">
	<!-- 未选中 -->
	<i class="checkBox"></i>  
	<span class="txt">点击这里查看效果</span>
</div>

<div class="type_2">
	<!-- 选中 -->
	<i class="checkBox select"></i>  
	<span class="txt">点击这里查看效果</span>
</div>
```

说明：

1. 方式一，选中后给`checkbox`添加`class select`并修改`html`内容为`&#xe647;`

2. 方式二，选中后给`checkbox`添加`class select`