# 表格

效果如下：

<iframe src="./demo/table/table.html" width="500px" height="300px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>

第一行灰色底为表头，表头下方为表格内容。

需要引入`table.css`。

`DOM`结构如下：   

```
<div class="table">
	<p class="title">表格名称</p>
	<div>
		<!-- 表头 -->
		<p class="header mui-row">
			<span class="mui-col-sm-4 mui-col-xs-4">管理费率</span>
			<span class="mui-col-sm-4 mui-col-xs-4">托管费</span>
			<span class="mui-col-sm-4 mui-col-xs-4">销售服务费</span>
		</p>
		<!-- 表格内容 -->
		<p class="mui-row">
			<span class="mui-col-sm-4 mui-col-xs-4 ellipsis ellip_1">1.50(每年)</span>
			<span class="mui-col-sm-4 mui-col-xs-4 ellipsis ellip_2">0.25</span>
			<span class="mui-col-sm-4 mui-col-xs-4 ellipsis ellip_3">--</span>
		</p>
		<p class="mui-row">
			<span class="mui-col-sm-4 mui-col-xs-4 ellipsis ellip_1">1.50(每年)</span>
			<span class="mui-col-sm-4 mui-col-xs-4 ellipsis ellip_2">0.25</span>
			<span class="mui-col-sm-4 mui-col-xs-4 ellipsis ellip_3">--</span>
		</p>
		<p class="mui-row">
			<span class="mui-col-sm-4 mui-col-xs-4 ellipsis ellip_1">1.50(每年)</span>
			<span class="mui-col-sm-4 mui-col-xs-4 ellipsis ellip_2">0.25</span>
			<span class="mui-col-sm-4 mui-col-xs-4 ellipsis ellip_3">--</span>
		</p>
	</div>					
</div>
```

说明：

1. `table`是表格容器，`title`是表格的名称

2. 带有`class`为`header`的`p`标签为表头，下面的`p`为表格内容，一个`mui-row`即一行，行数任意

3. 这个例子中，每一行有三个格子，因此`mui-col-sm-*  mui-col-xs-*`的数字为4，这是`mui`的栅格样式，若是改成其他数量，对应改这两个`class`的数字即可

