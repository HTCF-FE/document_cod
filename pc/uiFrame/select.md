# 单级

框架提供下拉列表组件。需要引入`select.less`。有两种样式供选择，分别说明如下：

###  种类一

点击试试：

<iframe src="./demo/select/select_1.html" width="400px" height="340px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>

`DOM`结构如下：

```
<!-- 第一个 -->
<div class="selectWrapper select-box singleSelect">
	<!--该下拉列表的标签 --> 
	<p class="title">产品类型</p>
	<!-- 下拉列表结果-->
	<p class="selectCopy" num=""></p>
	<!-- 下拉列表 -->
	<ul class="optionCopy">
		<li num="7">债权投资</li>
		……
	</ul>
</div>

```

说明：

1. 下拉列表容器`selectWrapper`，添加`select-box`表示这是第一种下拉列表，添加`singleSelect`，`select.js`会为`singleSelect`绑定点击下拉事件
	
> 这里`singleSelect`是为了与多级下拉列表（如地址联动）的下拉事件做区分。

> 多级下拉列表的`DOM`结构与单级下拉列表相同，但某些样式不同，下拉事件也不同，因此这里为单级下拉列表添加`singleSelect`

2. `selectCopy`具有`num`属性。下拉列表中的每条`li`都有对应的`num`属性，点击选中后，会将`num`值设置到`selectCopy`上，方便获取选中的数据，可用于校验是否已选

3. 选中数据后，会在`selectCopy`上添加`class`为`selectResult`，表示当前已选中数据，此时`selectCopy`会使用`selectResult`重置的选中结果样式


###  种类二

点击试试：

<iframe src="./demo/select/select_2.html" width="400px" height="340px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>

`DOM`结构如下：

```
<!-- 第二个 -->
<div class="selectWrapper select-input singleSelect">
	<!-- 下拉列表结果-->
	<p class="selectCopy" num=""></p>
	<!-- 下拉列表 -->
	<ul class="optionCopy">
		<li num="7">债权投资</li>
		……
	</ul>
</div>

```

说明：

1. 下拉列表容器`selectWrapper`，添加`select-input`表示这是第二种下拉列表，添加`singleSelect`，`select.js`会为`singleSelect`绑定点击下拉事件
	
> 这里`singleSelect`是为了与多级下拉列表（如地址联动）的下拉事件做区分。

> 多级下拉列表的`DOM`结构与单级下拉列表相同，但某些样式不同，下拉事件也不同，因此这里为单级下拉列表添加`singleSelect`

2. `selectCopy`具有`num`属性。下拉列表中的每条`li`都有对应的`num`属性，点击选中后，会将`num`值设置到`selectCopy`上，方便获取选中的数据，可用于校验是否已选。

3. 选中数据后，会在`selectCopy`上添加`class`为`selectResult`，表示当前已选中数据，此时`selectCopy`会使用`selectResult`重置的选中结果样式

