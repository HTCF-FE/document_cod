# 带单选效果的按钮

<!-- toc -->

用于一个或多个按钮单选的情况

### 模板说明

目前有`handlebars`模板，没有`ejs`模板

* `handlebars_radio_button.html` —— 基本按钮的模板

	```{% raw %}
		<div class="radioButton {{listMoreOne ../radio_list}} {{#if ../big}} big  num_{{getLength ../radio_list}} {{/if}}">
		    <input type="radio" {{#if readonly}} readonly {{else}} {{#if ../readonly}}  readonly {{/if}} {{/if}} {{#if disabled }} disabled {{else}} {{#if ../disabled}}  disabled {{/if}} {{/if}}  {{#if checked}} checked="{{checked}}" {{/if}}  name="{{../ownIndex}}"  {{#if ../area}} area="{{../area}}" {{/if}} num="{{id}}">
		    <label class="radioButtonTxt">{{description}}</label>
		</div>
		{% endraw %}
	```

	模板说明：

	1. 带单选效果的按钮，都带有`radioButton class`，包含一个`input radio`和`label`标签，`label`标签带`radioButtonTxt class`，在`input radio`未点击时也未默认选中时，是没有`checked="checked"`属性的，此时按钮为灰色边框灰色文字，利用`input radio`的`:checked`样式选择器，修改`label`标签的样式，实现选中和未选中的效果切换（选中后边框和文字变黄）

	2. 此模板为`handlebars`模板，渲染此模板的数据格式：

		```
			big: true,
			ownIndex: '',
			area: '',
			radio_list: [{
				description: '企业投资',
				readonly: true,
				disabled: true,
				checked: true,
				id: 0
			},
			{
				description: '企业融资',
				id: 1
			}]
		```

		`big`表示此按钮是否需要`big class`，`big class`用于设置按钮宽度随父级宽度平均分配，此时同时会设置`num_* class`，表示同时有几个按钮

		`ownIndex`为按钮的`name`属性值，在渲染模板时会设置到按钮上，实现单选效果

		`area`表示这一系列按钮是否有二级效果，即每一个按钮都对应一个区域，点击按钮时，除了切换选中状态，还要切换对应的区域的显示隐藏状态（例见发布项目页面的需求类型和投资方式），如果有二级效果，那么二级区域必须设置`secondArea`属性，且属性值必须为这里的`area`属性值加上`_second`，如`area`属性值为`productType`，那么对应的二级区域的`secondArea`属性值必须为`productType_second`** （此属性的使用和二级区域的点击切换方法目前只在表单里） **

		`radio_list`为按钮列表，是一个大数组，里面是一个一个的对象，有几个对象就表示有几个按钮，每一个按钮都可以有以下几个属性：

			+ description —— 按钮的文字

			+ readonly —— 是否readonly， true是，false否

			+ disabled —— 是否disabled，true是，false否

			+ checked —— 是否默认选中，true是，false否

			+ id —— 该按钮的num值，为此按钮的字典值（对应的接口字段数据字典值），在表单校验、提交数据时、数据回显时，都需要设置此属性

	3. `listMoreOne`和`getLength`是两个`handlebars`的`helper`，作用是：

		+ listMoreOne —— 计算`radio_list`的长度，判断是否大于1，如果大于1， 则返回`btnMore`，给按钮添加右边距

		+ getLength —— 计算`radio_list`的长度，并返回，给按钮设置`num_* class`，在按钮需要`big class`时，用来计算按钮的宽度


### 各种样式各种效果的说明

以下的`DOM`结构皆为经过上面模板编译后的结果

##### 基本按钮，默认宽度`140px`，高度`46px`
 
1. 未选中状态的按钮

	<iframe src="../../demo/button/b_1.html" height="130px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;"> </iframe>

	`DOM`结构：
 
	```
		<div class="radioButton">
		    <input type="radio" name="" num="">
		    <label class="radioButtonTxt">项目直投</label>
		</div>
	```

	未选中状态为灰色边框灰色文字，点击选中，会变成黄色边框黄色文字且不可取消（此为`input radio`单选按钮选中后不可取消的自带属性）

2. 选中状态的按钮

	<iframe src="../../demo/button/b_2.html" height="130px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;"> </iframe>

	`DOM`结构：

	```
		<div class="radioButton">
		    <input type="radio" name="" num="" checked="checked">
		    <label class="radioButtonTxt">项目直投</label>
		</div>
	```

	有`checked="checked"`属性时，即`input radio`选中时，按钮为黄色边框黄色文字

##### 多个按钮并排放置

<iframe src="../../demo/button/b_5.html" height="130px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;"> </iframe>

`DOM`结构：

```
	<div class="radioButton btnMore">
	    <input type="radio" checked="checked" name="formWrapDom_0_投资方式" num="1">
	    <label class="radioButtonTxt">项目直投</label>
	</div>

	<div class="radioButton btnMore">
	    <input type="radio" name="formWrapDom_0_投资方式" num="2">
	    <label class="radioButtonTxt">债券融资</label>
	</div>

	<div class="radioButton btnMore">
	    <input type="radio" name="formWrapDom_0_投资方式" num="3">
	    <label class="radioButtonTxt">项目直投</label>
	</div>

	<div class="radioButton btnMore">
	    <input type="radio" name="formWrapDom_0_投资方式" num="4">
	    <label class="radioButtonTxt">股权融资</label>
	</div>
```

在`radioButton`上添加`btnMore  class`，按钮可以并排放置并有间距`20px`

这几个按钮的`name`属性值相同时，可以单选，若`name`属性值不相同，没有单选效果

##### 大按钮，宽度根据父级元素的宽度平均计算（去掉按钮的间距），高度`46px`
	
<iframe src="../../demo/button/b_4.html" height="130px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;"> </iframe>


`DOM`结构：

```
	<div class="radioButton btnMore big num_2">
	    <input type="radio" checked="checked" name="formWrapDom_0_投资方式" num="1">
	    <label class="radioButtonTxt">项目直投</label>
	</div>

	<div class="radioButton btnMore big num_2">
	    <input type="radio" name="formWrapDom_0_投资方式" num="2">
	    <label class="radioButtonTxt">金融产品</label>
	</div>
```

在`radioButton`上添加`big  class`，按钮可以并排放置并有间距40px

同时在`radioButton`上添加`num_2  class`，表示同时并列的有`2`个按钮，按钮宽度按照`width: calc(~"(100% - 40px) / 2");`计算（（整体宽度-按钮间距）/按钮个数）

