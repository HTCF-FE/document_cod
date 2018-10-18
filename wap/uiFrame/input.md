# input输入框

最基本的结构，是一行内只有一个输入区的：

```
	<div class="form-wrap">
		<!-- 姓名 -->
		<div class="formList">
			<div class="mui-input-row">
				<input type="text" class="mui-input-clear" placeholder="请输入姓名">
			</div>
		</div>
	</div>
```

说明：

1）每一个输入类的表单元素，`class`都必须含有`formList`

2）在`formList`里面，嵌套一个`class`为`mui-input-row`的节点

3）`mui-input-row`里就是`input`输入框了，如果该输入框内需要有`x`这个清除内容按钮，需要给`input`的`class`属性添加`mui-input-clear`，`mui`会自动为这个按钮添加点击清除内容的事件


现在，在这个最基本的结构上，添加点不一样的东西~

1. 添加左边的`icon`

```
	<div class="form-wrap">
		<!-- 手机号码 -->
		<div class="formList formIconLeft">
			<span class="iconfont">&#xe665;</span>
			<div class="mui-input-row">
				<input type="tel" class="mui-input-clear" placeholder="请输入11位手机号码" maxlength="11">
			</div>
		</div>
	</div>
```

说明：

在这个手机号码的表单元素中，出现了左边的`icon`图标。这时：

1）在`formList`节点上，添加了`class`属性`formIconLeft`，表示该元素内有左边的`icon`图标

2）此`icon`图标的宽度是固定的，需要有`class`属性为`iconfont`


2. 有右边的icon

```
	<div class="form-wrap">
		<!-- 手机号码 -->
		<div class="formList formIconRight">
			<div class="mui-input-row ">
				<input type="password" class="mui-input-clear" placeholder="6-12位，至少包含2个数字，2个字母">
			</div>
			<span class="iconfont noEye"></span>
		</div>
	</div>

```

说明：

在这个手机号码的表单元素中，出现了右边的眼睛`icon`。这时：

1）在`formList`节点上，添加了`class`属性`formIconRight`，表示该元素内有右边的icon图标

2）此icon图标的宽度是固定的，需要有`class`属性为`iconfont`

右边的`icon`有两种情况：

1）眼睛：需要在`span`标签上添加`class`为`noEye`

2）表示帮助的？图标：需要在`span`标签上添加`class`为`help`


3. 右边不是`icon`，而是图文验证码的图片

```
	<div class="form-wrap">
		<!-- 图文验证码 -->
		<div class="formList verifyCode">
			<div class="mui-input-row">
				<input class="mui-input-clear" type="text" placeholder="请输入图文验证码"/>
			</div>
			<img  src="" class="twyzm_img">
		</div>
	</div>

```

说明： 

1） 在`formList`节点上，添加了`class`属性`verifyCode`，表示该元素为图文验证码

2） 在`mui-input-row`节点的后面，添加了`img`标签，`class`为`twyzm_img`，为图文验证码的图片


4. 右边不是`icon`，而是短信验证码的按钮

```
	<div class="form-wrap">
		<!-- 图文验证码 -->
		<div class="formList numberCode">
			<div class="mui-input-row">
				<input class="mui-input-clear" type="text" placeholder="请输入图文验证码"/>
			</div>
			<span class="dxyzmBtn" checkTop="true">获取验证码</span>
		</div>
	</div>

```

说明： 

1） 在`formList`节点上，添加了`class`属性`numberCode`，表示该元素为短信验证码

2） 在`mui-input-row`节点的后面，添加了`span`标签，`class`为`dxyzmBtn`，为短信验证码的按钮