# handlebars公用的helper

<!-- toc -->

提供一些可公用的`helper`

### 判断一个数组的长度是否>1

```
Handlebars.registerHelper('listMoreOne', function(list) {
   	if( !!list && list.length > 1){
   		return 'btnMore';  
   	}
   	else{
   		return ''; 
   	}
});
```

### 获取一个数组的长度

```
Handlebars.registerHelper('getLength', function(list) {
   	return list.length;
});
```

### 判断一个变量是true/false/''/有数据

```
Handlebars.registerHelper('judgeTxt', function( txt ){
	if( !txt || txt == 'true' || txt == 'false' ){
		return false;
	}
	return txt;
})
```

### 获取一个模板作为子模版（用于组合模板）

```
Handlebars.registerHelper('include', function( fileName , list_name, list) {
	
	//先取得文件
	var html = require('html-loader!../complex/' + fileName + '.html');

	if(!!list_name && util.getVarType.isString(list_name) == 'string'){

		//对于需要循环的数据，list_name为传进来的要循环的字段名
		//生成{{#each结构}}，将html包含起来
		html = '\n{{#each '+list_name+'}}' + html + '{{/each}}\n';

		//这时如果遇到了include，会重新进入这个方法，再次解析
		//由于list_name传递的是要循环的字段名，此时list.data.root为
		//可用来解析的数据
		html =  Handlebars.compile(html)(list.data.root);
	}
	else{
		//这时如果遇到了include，会重新进入这个方法，再次解析
		//由于list_name此时没有传递，为空，此时list_name.data.root为
		//可用来解析的数据
		html =  Handlebars.compile(html)(list_name.data.root);
	}

	if( html.indexOf('{{') == -1){
		//当模板里再也没有{{}}时，表示解析完毕，这时才返回解析好的html
		return html;
	}
   	
});
```

