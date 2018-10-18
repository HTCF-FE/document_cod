# 省市区地址联动

效果：

<iframe src="./demo/select/address.html" width="500px" height="500px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>

`DOM`结构如下：

```
<div id="sjld">
	<!-- 省份 -->
	<div id="shenfen" class="selectWrapper select-input">
	    <p  class="selectCopy"></p>
		<ul class="optionCopy">
		</ul>
	</div>
	<!-- 城市 -->
	<div id="chengshi"  class="selectWrapper select-input">
	    <p  class="selectCopy"></p>
		<ul class="optionCopy">
		</ul>
	</div>
	<!-- 区域 -->
	<div id="quyu" class="selectWrapper select-input">
	    <p  class="selectCopy"></p>
		<ul class="optionCopy">
		</ul>
	</div>

</div>

```

说明：

1. 需要引入`select.css`和`addressJS.js`。引入`addressJS.js`后，需要在页面打开时进行该组件的初始化。

```
$("#sjld").sjld("#shenfen","#chengshi","#quyu");
```
初始化后，会给下拉列表设置默认数据，并在`selectCopy`上添加`class`为`selectResult`，表示当前已选中数据，此时`selectCopy`会使用`selectResult`重置的选中结果样式


2. `sjld`是省市区下拉列表的容器，里面有三个`selectWrapper`下拉列表，分别添加`id`为`shenfen`，`chengshi`，`quyu`，表示省份、城市、区域

3. 每个`selectWrapper`的结构与单级下拉列表相同

4. 单级下拉列表使用`select.js`绑定下拉事件，但这里不适用`select.js`，而使用`addressJS.js`，绑定下拉事件并写有省市区地址名称的数据
