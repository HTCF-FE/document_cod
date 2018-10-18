# 表单中的错误提示

错误提示不仅可用于按钮，也可用于表单校验中提示错误。

本框架提供的表单组件集成了错误提示组件，效果如下 ：

<iframe src="./demo/form/formError.html" width="400px" height="460px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>

`DOM`结构：

```
<div class="inputDom">
	<!-- 一个表单元素 -->
	<div class="card-input-row ">
		<label>银行预留手机号</label>
		<div class="inputRow">
			<!-- 输入框 -->
			<input type="text" placeholder="请输入银行预留手机号" maxlength="11" needCheck="true">
			<!-- 输入框的x按钮 --> 
			<i class="iconfont">&#xe649;</i>
		</div>
		<!-- 错误提示 -->
		<div class="error-tip">请输入银行预留手机号</div>
	</div>

	<!-- 又一个表单元素 -->
	<div class="card-input-row ">
		<!-- label -->
		<label><span class="star">*</span>证件类型</label>
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
		<!-- 错误提示 -->
		<div class="error-tip">请选择证件类型</div>
	</div>

	<!-- 再来一个~ -->
	<div class="card-input-row ">
		<!-- 一个textarea -->
		<label>该textarea的label</label>
		<textarea needcheck="true"></textarea>
		<!-- 错误提示 -->
		<div class="error-tip">请选择证件类型</div>
	</div>
</div>
```

说明：

1. 在`card-input-row`的最后，添加节点`<div class="error-tip></div>`，即在表单组件内集合了前面所说的错误提示的组件

2. 需要引入`check.css`和`errorTip.css`，在`check.css`中对`errorTip`的样式做了重置（添加了绝对定位）

3. 任何表单元素都可以直接使用