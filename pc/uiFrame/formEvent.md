# formEvent.js说明

表单组件提供了`formEvent.js`，对表单组件中一些必须的基本事件进行监听。

监听的事件有：

1. 输入框focus时，出现`x`清除内容的按钮，并添加获取焦点的样式改变
 
2. 输入框blur时，隐藏`x`按钮，并去掉焦点时的样式改变

3. 点击`x`按钮，清除输入框内容
 

使用时，直接引入该文件即可。会获取页面上所有`needCheck=true`的元素，并对其添加相关事件的监听。

因此非表单元素，请勿添加`needCheck=true`属性