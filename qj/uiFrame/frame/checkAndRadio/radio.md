# 单选

一个单选框，选中后不可取消

<iframe src="../../demo/checkAndRadio/r_1.html" height="60px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;"> </iframe>

目前只有`handlebars`模板，没有`ejs`模板
 
```{% raw %}
<div class="radio">
	<div class="radioBox">
	    <input type="radio" {{#if readonly}} readonly {{else}} {{#if ../readonly}}  readonly {{/if}} {{/if}} {{#if disabled }} disabled {{else}} {{#if ../disabled}}  disabled {{/if}} {{/if}} {{#if checked}} checked="checked" {{/if}} num="{{id}}" name="{{../ownIndex}}" area="{{../area}}">
	    <label class="iconfont"></label>
	</div>
	<span>{{description}}</span>
</div>
{% endraw %}
```

用`input radio`模拟，根据`radio`的选中和未选中的`:checked`样式选择器，改变`label`标签的样式，达到选中状态样式切换的效果

--- 

可用变量：

* readonly - `boolean`类型，是否只读，`true`-是，`false`-否

* disabled - `boolean`类型，是否disabled，`true`-是，`false`-否

* checked - `boolean`类型，是否默认选中，`true`-是，`false`-否

* id - `string`类型，作为`num`属性值（为对应的接口字段数据字典值），在表单校验、提交数据时、数据回显时，都需要设置此属性

* ownIndex - `string`类型，作为`name`属性值，使多个单选框具有单选效果，如果只有一个单选框，可不设置

* description - `string`类型，该多选框的文案

** 未选中时为灰色框，选中后变为黄色框 **

可用如下格式的数据渲染：

```
var radio = {
	readonly: false, 
	disabled: false, 
	checked: true, 
	id: '1', 
	ownIndex: '',  
	descriptiion: '按钮'
}
```



