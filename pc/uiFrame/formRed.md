# 红色*——必填的表单元素

表单中经常见到某些输入框前后有*标识，表示该输入框必填。本框架也提供了这种结构，效果如下：

<iframe src="./demo/form/formRed.html" width="400px" height="400px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>

`DOM`结构：
 
```
<!-- 输入类 -->
<div class="card-input-row "> 
	<label><span class="star">*</span>请输入银行预留手机号</label>
	<div class="inputRow">
		<!-- 输入框 -->
		<input type="text" placeholder="请输入银行预留手机号" maxlength="11" needCheck="true">
		<!-- 输入框的x按钮 --> 
		<i class="iconfont">&#xe649;</i>
	</div>
</div>

<!-- 选择类 -->
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
</div>
```

在`label`标签中，多了一个`<span class="star">*</span>`，这就是红色的*

