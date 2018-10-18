# 表单中的下拉选项

使用框架提供的下拉选择，在此基础上添加了样式的重置等。

点击看看：

<iframe src="./demo/form/formSelect.html" width="400px" height="300px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>

这是在表单中的下拉列表，具有下拉列表的特点，又遵守了表单的样式规则。

`DOM`结构： 

```
<div class="card-input-row "> 
	<!-- label --> 
	<label>证件类型</label>
	<!-- 下拉列表 -->
	<div class="selectWrapper select-input singleSelect">
	    <p class="selectCopy" num="">请选择证件类型</p> 
		<ul class="optionCopy">
			<li num="0">身份证</li>
			<li num="4">回乡证</li>
			<li num="D">台胞证</li>
			<li num="6">外国护照</li>
		</ul>
	</div>
</div>

```

说明：

1. 与其他表单元素一样，下拉列表作为一个表单元素，用`card-input-row`包起来，并有`label`标签

2. 需要引入`select.css`和`check.css`、`select.js`，在`check.css`中，对表单下拉样式做了重置，因此需要将`select.css`放在`check.css`前，否则重置会失效

3. 如果表单中只有下拉列表的话，不需要引入`formEvent.js`
