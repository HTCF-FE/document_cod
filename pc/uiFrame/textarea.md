# textarea

表单中常见的textarea文本框。

效果：
 
<iframe src="./demo/form/textarea.html" width="400px" height="200px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>
 
 
`DOM`结构如下：  
 
``` 
<!-- 表单容器 -->
<div class="inputdom">	 
	<!-- 一个textarea -->
	<div class="card-input-row">  
	    <label>该textarea的label</label>
	    <textarea needcheck="true"></textarea>
	</div>
</div>
```
说明：

1. `label`标签后，是`textarea`

2. `textarea`不需要`x`清除内容的按钮，但也有获取焦点时的样式改变


