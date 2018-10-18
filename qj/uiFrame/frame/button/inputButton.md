# 不带单选效果的按钮

<!-- toc -->

1. `input`模仿的按钮

2. `div`模仿的带`icon`的按钮

### 模板说明

有`ejs`和`handlebars`模板

##### ejs模板

* `ejs/button.html` —— 基本按钮的模板
	
	```
		<% if (!width){ var width = '140px';} %>
		<% if (!btnMore){ var btnMore = '';} %>
		<input type="button" class="btn <%= type%> <%= btnMore%>" value="<%= value%>" style="width:<%= width%>">
	```
	
	`width` —— 按钮宽度，不传的话，默认140px

	`btnMore —— 按钮是否多个并列，不传的话默认为空

	`type` —— 按钮样式类别，必传

	`value` —— 按钮文字，必传

* `ejs/disabledButton.html` —— 不可点击的按钮模板

	```
		<% if (!width){ var width = '140px';} %>
		<% if (!btnMore){ var btnMore = '';} %>
		<input type="button" class="btn <%= type%> <%= btnMore%>" value="<%= value%>" style="width:<%= width%>" disabled="disabled">
	```

	各变量概念同上，比上面的模板多了`disabled="disabled"`属性

* `ejs/iconButton.html` —— 带`icon`的按钮模板

	```
		<% var w = ''; if (!!width){ w = 'width:'+width+';';} %>
		<% var h = ''; if (!!height){ h = 'height:'+height+';line-height:'+height+';' ;} %>
		<% if (!btnMore){ var btnMore = '';} %>
		<div class="btn <%= type%> <%= btnMore%>" style="<%= w%><%= h%>">
			<span class="iconfont"><%- icon%></span>
			<span class="value"><%= value%></span>
		</div> 
	```

	各变量概念同上，另：

	`w` —— 按钮宽度，可不传

	`h` —— 按钮高度，可不传

	`icon` —— `icon`

##### handlebars模板
	
* `handlebars/button.html` —— 基本按钮的模板

	```{% raw %}
		<input type="button" class="btn {{type}} {{listMoreOne ../list}} {{#if ../big}} num_{{getLength ../list}} {{/if}} form_btn_{{@index}}" value="{{buttonTxt}}" style="width:{{width}}" {{#if readonly}} readonly {{else}} {{#if ../readonly}}  readonly {{/if}} {{/if}} {{#if disabled }} disabled {{else}} {{#if ../disabled}}  disabled {{/if}} {{/if}}  >
		{% endraw %}
	```

	此模板为`handlebars`模板，渲染此模板的数据格式：

	```
		big: true,
		ownIndex: '',
		area: '',
		list: [{
			buttonTxt: '企业投资',
			readonly: true,
			disabled: true,
			checked: true,
			width: '',
		},
		{
			buttonTxt: '企业融资',
		}]
	```

	`big`表示此按钮是否需要`big class`，`big class`用于设置按钮宽度随父级宽度平均分配，此时同时会设置`num_* class`，表示同时有几个按钮

	`list`为按钮列表，是一个大数组，里面是一个一个的对象，有几个对象就表示有几个按钮，每一个按钮都可以有以下几个属性：

		+ buttonTxt —— 按钮的文字

		+ readonly —— 是否readonly， true是，false否

		+ disabled —— 是否disabled，true是，false否

		+ checked —— 是否默认选中，true是，false否

		+ width —— 该按钮的宽度，不传的话默认为`140px`

	`listMoreOne`和`getLength`是两个`handlebars`的`helper`，作用是：

		+ listMoreOne —— 计算`list`的长度，判断是否大于1，如果大于1， 则返回`btnMore`，给按钮添加右边距

		+ getLength —— 计算`list`的长度，并返回，给按钮设置`num_* class`，在按钮需要`big class`时，用来计算按钮的宽度

	`form_btn_*`用来给按钮设置一个区别于`list`中其他按钮的`class`值

### 各种样式各种效果的说明

以下的`DOM`结构皆为经过上面模板编译后的结果

##### 基本按钮，默认宽度`140px`，高度`46px`

<iframe src="../../demo/button/button_1.html" height="750px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;"> </iframe>
 
一个最基本的按钮的`dom`结构：`<input type="button" class="btn" value="">` 

在此基础上，根据需要添加不同的`type_*`的`class`，形成不同样式的按钮：

```
	<p>一个黄底白字的按钮</p>
	<input type="button" class="btn type_1" value="这是一个按钮">

	<p>一个灰边白底灰字的按钮</p>
	<input type="button" class="btn type_2" value="这是一个按钮">

	<p>一个灰底白字的按钮</p>
	<input type="button" class="btn type_3" value="这是一个按钮">

	<p>一个白底黄字的按钮</p>
	<input type="button" class="btn type_4" value="这是一个按钮">

	<p>一个黄底棕色字的按钮</p>
	<input type="button" class="btn type_5" value="这是一个按钮">

	<p>一个白底深蓝色边框，深蓝色字的按钮</p>
	<input type="button" class="btn type_6" value="这是一个按钮">

	<p>一个白底红色边框，红字的按钮</p>
	<input type="button" class="btn type_7" value="这是一个按钮">
``` 

##### 不可点击（此效果目前只有黄底白字的按钮有）
	
<iframe src="../../demo/button/button_2.html" height="80px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;"> </iframe>

在基本的黄底白字的按钮的`dom`结构基础上，添加`disabled="disabled"`属性，实现不可点击的效果

此时按钮的底色和文字颜色同`type_3`时的灰底白字的按钮相同，但要注意，仅是样式看起来相同而已

```
	<input type="button" class="btn type_1" value="这是一个按钮" disabled="disabled">
```

##### 椭圆形按钮
	
<iframe src="../../demo/button/button_3.html" height="430px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;"> </iframe>

```
	<input type="button" class="btn type_1 r_l_radius" value="这是一个按钮">
	<input type="button" class="btn type_2 r_l_radius" value="这是一个按钮">
	<input type="button" class="btn type_3 r_l_radius" value="这是一个按钮">
	<input type="button" class="btn type_4 r_l_radius" value="这是一个按钮">
	<input type="button" class="btn type_5 r_l_radius" value="这是一个按钮">
	<input type="button" class="btn type_6 r_l_radius" value="这是一个按钮">
	<input type="button" class="btn type_7 r_l_radius" value="这是一个按钮">
```

在以上按钮`dom`结构的基础上，添加`r_l_radius class`

##### 多个按钮并列

<iframe src="../../demo/button/button_4.html" height="80px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;"> </iframe>

```
	<input type="button" class="btn type_1 btnMore" value="这是一个按钮">
	<input type="button" class="btn type_2 btnMore" value="这是一个按钮">
	<input type="button" class="btn type_3 btnMore" value="这是一个按钮">
``` 

添加`btnMore class`，会给按钮设置右边距`20px`

##### 带icon的按钮 

<iframe src="../../demo/button/button_5.html" height="140px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;"> </iframe>

`DOM`结构：

```
	<div class="btn type_6">
		<span class="iconfont">&#xe60c;</span>
		<span class="value">收藏</span>
	</div>

	<div class="btn type_1">
		<span class="iconfont">&#xe60c;</span>
		<span class="value">收藏</span>
	</div>
```

##### 固定172px宽的按钮

<iframe src="../../demo/button/button_6.html" height="540px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;"> </iframe>

```
	<input type="button" class="btn type_1 big" value="这是一个按钮">
	<input type="button" class="btn type_2 big" value="这是一个按钮">
	<input type="button" class="btn type_3 big" value="这是一个按钮">
	<input type="button" class="btn type_4 big" value="这是一个按钮">
	<input type="button" class="btn type_5 big" value="这是一个按钮">
	<input type="button" class="btn type_6 big" value="这是一个按钮">
	<input type="button" class="btn type_1 big" value="这是一个按钮" disabled="disabled">
	<input type="button" class="btn type_7 big" value="这是一个按钮">
```

添加`big class`

##### 自定义宽高的按钮
	
<iframe src="../../demo/button/button_7.html" height="340px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;"> </iframe>

```
	<input type="button" class="btn type_1" value="这是一个按钮" style="width:184px;height:32px;line-height:32px;">

	<input type="button" class="btn type_2" value="这是一个按钮" style="width:100px;">

	<input type="button" class="btn type_7" value="这是一个按钮" style="height:60px;line-height:60px;">

	<input type="button" class="btn type_4 r_l_radius" value="这是一个按钮" style="width:184px;">

	<input type="button" class="btn type_1 r_l_radius" value="这是一个按钮" disabled="disabled" style="width:160px;height:40px;line-height:40px;">
```

##### 按钮宽度根据父元素宽度平均分配 
	
<iframe src="../../demo/button/button_8.html" height="80px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;"></iframe>

```
	<input type="button" class="btn type_1 btnMore num_2" value="这是一个按钮">
	<input type="button" class="btn type_1 btnMore num_2" value="这是一个按钮">
```

在`btnMore`的基础上，添加`num_* class`，表示当前是几个按钮平均分配

目前只有`num_2`，后期如果有新需求可以继续添加`num_*`的样式~ 