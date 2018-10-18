# 弹出层

效果如下：

<iframe src="./demo/elasticLayer/elasticLayer.html" width="600px" height="350px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;"> </iframe>

点击按钮后，会出现弹出层，带黑色透明背景遮罩。

点击返回按钮，隐藏弹层，执行回调函数（若配置）。

点击确定，执行回调函数。

使用方法：

1. 引入`elasticLayer.js`和`elasticLayer.less`。（也提供了`less`文件打包后生成的`elasticLayer.css`文件，可根据需要使用）

2. 调用方式：

```
//需要传递给组件的参数
var obj = {
   title: '提示', //大标题
   p: '<p class="elastic_p">这是一个弹出层</p>',
   callback : function(t){ //确定按钮的回调函数
        t.hide();
   },  
   zIndex: 100, //z-index
}

//弹出层初始化	
$.elasticLayer(obj);

```

可配置参数：

```
title: '弹层',  //如果不传默认为'弹层'
p: '', 
yesTxt : '确定' , //确定按钮的文案，不传默认为确定
celTxt : '返回', //返回按钮的文案，不传默认为返回
callback : $.noop,  //确定按钮的回调函数，默认为空(jQuery的空函数，仅仅想要传递一个空函数的时候可以使用)
callbackCel: $.noop, //取消按钮的回调函数
zIndex: 100 //该弹层的z-index，因为不知道有几个弹层和弹层顺序，不传默认为100
```

每次新生成弹层都会清除掉之前的弹层，因此`DOM`结构只会一个。
