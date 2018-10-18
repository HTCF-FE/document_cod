# 表单数据回显

表单组件提供了常见的数据回显效果：

<iframe src="./demo/form/formData.html" width="400px" height="1100px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe> 


`DOM`结构如下：

```
<div class="inputDom">

	<h5>已数据回显，可以继续输入</h5>

	<div class="card-input-row ">
		<label>银行预留手机号</label>
		<!-- 输入框 -->
		<div class="inputRow">
			<input type="text" placeholder="请输入银行预留手机号" maxlength="11" value="18212341234" needCheck="true">
			<!-- 输入框的x按钮 --> 
			<i class="iconfont">&#xe649;</i>
		</div>
		<!-- 错误提示 --> 
		<div class="error-tip">请输入银行预留手机号</div>
	</div>

	<h5>已数据回显，不可以继续输入</h5>

	<div class="card-input-row ">
		<label>银行预留手机号</label>
		<!-- 输入框 -->
		<div class="inputRow">
			<input type="text" placeholder="请输入银行预留手机号" maxlength="11" value="18212341234" disabled="disabled" class="stopClick" needCheck="true">
			<!-- 输入框的x按钮 --> 
			<i class="iconfont">&#xe649;</i>
		</div>
		<!-- 错误提示 -->
		<div class="error-tip">请输入银行预留手机号</div>
	</div>

	<h5>已数据回显，可以继续选择</h5>

	<div class="card-input-row ">
		<!-- label -->
		<label><span class="star">*</span>证件类型</label>
		<!-- 下拉列表 -->
		<div class="selectWrapper select-input singleSelect">
		    <p class="selectCopy selectResult" num="4">回乡证</p>
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

	<h5>已数据回显，不可以继续选择</h5>

	<div class="card-input-row ">
		<!-- label -->
		<label><span class="star">*</span>证件类型</label>
		<!-- 下拉列表 -->
		<div class="selectWrapper select-input singleSelect">
		    <p class="selectCopy selectResult stopClick" num="4">回乡证</p>
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

	<h5>已数据回显，可以继续输入</h5>

	<div class="card-input-row ">
		<!-- 一个textarea -->
		<label>该textarea的label</label>
		<textarea needCheck="true">数据回显啦</textarea>
		<!-- 错误提示 -->
		<div class="error-tip">请选择证件类型</div>
	</div>

	<h5>已数据回显，不可以继续输入</h5>

	<div class="card-input-row ">
		<!-- 一个textarea -->
		<label>该textarea的label</label>
		<textarea needcheck="true" class="stopClick" disabled="disabled">数据回显啦</textarea>
		<!-- 错误提示 -->
		<div class="error-tip">请选择证件类型</div>
	</div>

</div>
```

这里举例了不同情况下的数据回显效果，按`input`输入框、下拉选项，`textarea`三种情况看：

1. `input`输入框

	1）回显数据，可以继续填写：

		给`input`设置`value`值即可

	2） 回显数据，不可继续填写：

		给`input`设置`value`值，并添加`class`为`stopClick`，添加属性`disbled=disabled`

2. 下拉选项
	
	下拉选项的数据回显在下拉选项部分已经讲述，这里重复一下：
 
	1）回显数据，可以继续选择：

		给`selectCopy`添加`class`为`selectResult`，设置`num`属性值为对应的下拉列表中那项选中数据的`num`属性值，并设置`selectCopy`的`html`为该项选中数据的文案

	2） 回显数据，不可继续填写：

		除了第一步的操作，还需要给`selectCopy`添加`class`为`stopClick`，禁止下拉操作

3. `textarea`

	）回显数据，可以继续填写：

		给`textarea`设置`value`值即可 

	2） 回显数据，不可继续填写：

		给`textarea`设置`value`值，并添加`class`为`stopClick`，添加属性`disbled=disabled`
