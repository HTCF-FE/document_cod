# 表单数据回显

表单组件提供了常见的数据回显效果：

按`input`输入框、下拉选项，`textarea`三种情况看：

1. `input`输入框

	1）回显数据，可以继续填写：

		给`input`设置`value`值即可

	2） 回显数据，不可继续填写：

		给`input`设置`value`值，并添加属性`disbled=disabled`

2. 下拉选项
	
	下拉选项的数据回显在下拉选项部分已经讲述，这里重复一下：
 
	1）回显数据，可以继续选择：

		给`mui-navigate-right`添加`class`为`hasSelect`，设置`num`属性值为对应的下拉列表中那项选中数据的`num`属性值，并设置`mui-navigate-right`的`html`为该项选中数据的文案

	2） 回显数据，不可继续填写：

		除了第一步的操作，还需要给`mui-navigate-right`添加`class`为`unable`，禁止下拉操作

3. `textarea`

	）回显数据，可以继续填写：

		给`textarea`设置`value`值即可 

	2） 回显数据，不可继续填写：

		给`textarea`设置`value`值，并添加属性`disbled=disabled`
