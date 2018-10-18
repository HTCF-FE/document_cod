# textarea

表单中常见的textarea文本框。但是这个文本框适应文字内容高度，即默认是一行，随着文字的增多，文本框的高度会随之增加。

效果： 
 
<iframe src="./demo/textarea/textarea.html" width="400px" height="200px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>
 
 
`DOM`结构如下：   

``` 
<div class="formBox hasPad left noBor">
	<div class="formList">						
		<div class="mui-input-row">
			<textarea rows="2" placeholder="请输入通讯地址" maxlength="100"></textarea>
		</div>
	</div>  
</div>

```
说明：

1. 需要引入`autoTextarea.js`，调用方式：

```
autoTextarea( $('textarea')[0] );   //传递的参数必须是dom节点而不是jQuery节点
```

2. 需要引入`newFormMui.css`


