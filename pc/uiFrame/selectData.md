# 数据回显的下拉选择

1. 回显数据，可以继续选择：

	给`selectCopy`添加`class`为`selectResult`，设置`num`属性值为对应的下拉列表中那项选中数据的`num`属性值，并设置`selectCopy`的`html`为该项选中数据的文案
2. 回显数据，不可继续填写：

	除了第一步的操作，还需要给`selectCopy`添加`class`为`stopClick`，禁止下拉操作