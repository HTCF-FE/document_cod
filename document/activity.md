## 活动页兼容性问题及解决方法整理

共有音频播放、动画播放、图片是否加载完成的判断、图片跨域加载显示、倒计时、H5页面转化为图片等几项

其中：

1. 音频播放因**`ios`手机禁止自动播放**的原因，只能在微信浏览器上做到自动播放，因此这里提供的**兼容性处理方式只在微信浏览器中有效，其他浏览器是不可以音频自动播放的**

2. H5页面转化为图片，是利用了微信浏览器中，图片自带长按出现保存图片和识别二维码的功能，因此在其他浏览器上是不会长按提示保存图片的


#### 音频播放（不同手机兼容性和浏览器兼容性问题）
使用`H5`的`audio`标签，但`ios`和`android`手机都有不同程度的兼容性问题，比如`ios`手机就禁止了`audio`的下载后自动播放功能，几个自带事件如`oncanplay`等也无法监听到。

在微信浏览器中，可以通过微信`sdk`提供的方法播放音乐，解决办法如下：

1. 引入微信sdk

2. 监听WeixinJSBridge和WeixinJSBridgeReady
    此方法也有兼容性问题，兼容写法如下：
	```
	if (typeof WeixinJSBridge == "object" && typeof WeixinJSBridge.invoke == "function") {
		playAudio();
	} else {
		//監聽客户端抛出事件"WeixinJSBridgeReady"
		if (document.addEventListener) {	document.addEventListener("WeixinJSBridgeReady", function(){
			playAudio('wx');
			}, false);
			} else if (document.attachEvent) {
			document.attachEvent("WeixinJSBridgeReady", function(){
			playAudio('wx');
			});
			document.attachEvent("onWeixinJSBridgeReady", function(){
			playAudio('wx');
			});
		}
	}
	```
`playAudio`方法里播放音乐

3. `playAudio`方法里需要将所有的audio音频都先执行一次`play`及`pause`

	如这里有三个音频：`audio_load`，`audio_door，audio_music`：
	```
	//必须先播放再马上停止
	  audio_load.play();
	  audio_load.pause();

	  audio_door.play();
	  audio_door.pause();

	  audio_music.play();
	  audio_music.pause();
	```
	如果这里只播放第一个`audio_load`，后面再播放`audio_door`和`audio_music`的时候，会放不出来，所以在这里必须先把所有的音频都`play`一下，马上再`pause`,然后在真正需要播放音乐的地方再执行`play`方法

4. `oncanplay`等`audio`自带方法无法监听，在微信浏览器也做不到，所以只能尽量把音频加载的地方放在页面顶部，使尽量早的加载

#### 动画
正常来说，`H5`页面能直接使用的动画只有`gif`图，`swf`文件属于`flash`，需要播放器才能播放，且需要兼容性高的播放器，`mp4`文件同理。

但效果丰富的动画用`gif`的话图片体积会很大，十几兆或者几十兆，放在手机上很卡（安卓手机可能完全无法显示），所以可以用`swf`文件，使用`Fanvas`工具，转化成`js`能用的图片和`canvas`方式呈现。

`Fanvas`：把`swf`转为`html5 canvas`动画的系统

`github`：https://github.com/Tencent/Fanvas

简单教程：https://www.cnblogs.com/ChenChunChang/p/8268747.html

使用方法：

1. 用`Fanvas`导入`swf`文件，导出`js`和图片

2. 按照教程引入需要的文件，在需要的地方初始化动画

3. 在`html`文件中添加用于显示当前动画的`canvas`标签

4. 若`swf`文件播放到后面有不正常的白屏或其他问题，可能是后面几帧不对，可以用`flash`处理软件查看正常的帧数并修改`Fanvas`导出的`js`中的`totalFrames`，此变量表示当前`flash`的帧数

5. 引入的`Fanvas`文件中，有一个`fanvas3-min.js`，这是`Fanvas`的底层文件，源代码不是根据`totalFrames`确定播放是否结束，且播放后会自动重播，现已修改为根据`totalFrames`的数值播放动画且播放后停止，文件见附件

6. 停止和切换动画的方法见教程

#### 图片加载完成的判断
```
var img = new Image();
img.onload = function(){
	//此时这张img已经加载完成
}
//src的设置需要放在onload之下
img.src = '***';
```

#### 图片跨域加载并显示
图片不在当前服务器上，需要跨域加载并显示，需要拿到图片并转化为`base64`格式，用`canvas`展示。
```
var canvas = document.createElement("canvas");
var ctx = canvas.getContext('2d');

//这里的宽高可以随意
canvas.width = 100;
canvas.height = 100;

var img = new Image();

//设置图片跨域访问
img.crossOrigin = 'anonymous';

//加时间戳解决跨域问题
img.src = url+"?timeStamp="+new Date(); 

img.onload = function () {
	ctx.drawImage(this,0,0,100,100);
	var base64 = canvas.toDataURL('image/jpg', 1);
	//将图片设置到页面上
	$('.phono').attr('src', base64);
};
```
**重点**在于

1. `img.crossOrigin = 'anonymous'`

2. 需要给`img.src`的路径**添加随机数（或时间戳）**

#### 倒计时
`js`的倒计时方法不是真正的按设置的`time`执行的，而是会受正在执行的其他`js`逻辑影响，如设置倒计时`3s`，每倒计`1s`时都进行一些处理比如页面上的数字`3`变成`2`，此时`2`不一定是按倒计时`1s`时出现，可能会有延迟。

解决方法：

1. 尽量不在倒计时的同时进行其他逻辑处理

2. 使用当前时间戳进行判断
	```
	//当前时间
	var startTime = new Date().getTime(); 
	//times为显示在页面上的数字
	var count = 0, offset = 0, times = 3;

	//js倒计时有延迟，所以不能直接setInterval监听1000
	var a = setInterval(function(){
		//此时的时间戳
		var n = new Date().getTime();

		if(  (n - startTime ) >=  1000  ) {
			//到1s了, times减1
			times = times - 1;

			//times为0时停止clearInterval
			if (times == 0) {
				clearInterval(a);
			}
			//重置startTime
			startTime = new Date().getTime() ;
		}
	}, 0);
	```

#### 将H5页面转化为图片
在微信浏览器中，图片自带长按保存和识别二维码功能

有些需求需要生成一张可以保存的图片，此时需要使用`html2canvas`插件

在需要转化的`html dom`结构设置好后，采用如下方法转换
	```
	html2canvas(document.getElementById('posterImg')).then(function(canvas) {
						document.body.appendChild(canvas);
	//imgData是得到的图片
	var imgData = canvas.toDataURL("image/png").replace("image/png", "image/octet-stream");
	//将这张图片设置到页面上						$("#posterpic").attr("src", imgData);
	});
	```


## 活动页常用插件

#### 进度条
使用`NProgress`插件

官网：http://ricostacruz.com/nprogress/

使用时需要引入`js`文件，`css`样式自定义

使用方法：

1. 首先将进度条定义到`0`的位置
    `NProgress.set(0.0);`
2. 进度条不会变短，在当前基础上增长的处理
    ```
    //当前进度，f是当前的数值
    var num = parseInt(f*100);
    //num小于当前进度时，不执行后面的逻辑
    if( num < step){
        return false;
    }
    //这里当f>当前进度时，设置进度条的值
    for( var m = step; m < num; m++){
        (function(m){
            //进度条前进
            NProgress.set( m/100 );
        })(m);
    }
    //step设置成num
    step = num;
    ```
3. 进度条走到100%
    `NProgress.set(1);`

#### 将H5页面转化为图片
见上面兼容性整理的最后一条