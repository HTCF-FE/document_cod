# 弹框

本框架提供了**二种**弹框，效果见图：

![PNG](./img/elasticlayer/elasticlayer_1.png)  ![PNG](./img/elasticlayer/elasticlayer_2.png)

分别说明如下：

### 一. 白底，有两个按钮

如图：

![PNG](./img/elasticlayer/elasticlayer_1.png)

需要引入样式文件`elasticlayer.less`和`js`文件`elasticlayer.js`。

标题、文案、取消确定两个按钮的文案和点击后执行的动作都是可以配置的，可配置参数如下：

```
id :  'elasticLayer', //弹层的唯一id
zIndex: 10000000, //该弹层的z-index，因为不知道有几个弹层和弹层顺序，不传默认为10000000

//标题
title: '尊敬的用户',  //如果不传默认为'尊敬的用户'
iconTxt: '', //标题icon的值, 默认为空
iconType: 'green', //icon的颜色

//中间区域
p: '', //弹层中间区域文案

//按钮
yesTxt : '确定' , //确定按钮的文案，不传默认为确定
celTxt : '取消', //返回按钮的文案，不传默认为取消
yesButtonPosition: 'left', //确定按钮在左边还是在右边，不传的话，默认为'left'，在左边，如果在右边，传'right'
callbackCel: $.noop, //取消按钮的回调函数，默认为空
callback : $.noop,  //确定按钮的回调函数，默认为空

//按钮是否需要配置为链接
needYesHref: false, //是否需要把确定按钮改成a标签，默认false
needCelHref: false, //是否需要把取消按钮改成a标签，默认false
yesHref: 'javascript:;', //确定按钮a链接的默认href
celHref: 'javascript:;', //取消按钮a链接的默认href
```

### 二. 帮助知道了

如图：

![PNG](./img/elasticlayer/elasticlayer_2.png)

需要引入样式文件`elasticlayerTwo.less`和`js`文件`elasticlayerTwo.js`。

可配置参数如下：

```
title: '帮助',  //如果不传默认为'帮助'
p: '', 
buttonTxt: '知道了', 
zIndex: 100, //该弹层的z-index，因为不知道有几个弹层和弹层顺序，不传默认为100
callback : $.noop  //点击知道了按钮的回调函数
```



