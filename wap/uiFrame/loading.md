# loading加载中

与服务器发送`ajax`请求时，由于有等待的时间，为了用户体验，需要在页面上显示`loading`的图标，本框架提供了两种`loading`：

1. 白色背景+金色`logo`，`logo`的位置在页面上方

2. 透明背景+`logo`，`logo`为黑色背景金色图案，`logo`的位置在页面中间

效果如图：

![PNG](./img/loading/loading_1.png)  ![PNG](./img/loading/loading_2.png)  

### DOM结构

```
	<!-- 1 -->
	<div class="v_center box" style="position: fixed; top: 0px; right: 0px; left: 0px; bottom: 0px; background: rgb(255, 255, 255); z-index: 999; padding-top: 2rem; display: none;" id="loading">
		<div class="load" style="text-align:center">
			<span class="iconfont loadingIcon" style="font-size:3rem;color:#f4cf5c;display:inline-block"></span>
			<span style="display:block;line-height:2rem;font-size:1.2rem;color:#7d7c7d;height:2rem;vertical-align:top;margin-top:1.5rem">加载中...</span>
		</div>
	</div>

	<!-- 2 -->
	<div class="listLoading" style="position: fixed;z-index: 997;background: rgba(255, 255, 255, 0);top: 0px;left: 0px;width: 100%;height: 100%;display: none;display: block;">
		<div class="blackBg" style="position:absolute;margin;auto;top:0;left:0;right:0;bottom:0;background:#333;line-height:5rem;width:5rem;height:5rem;margin: auto;text-align: center;border-radius: 1rem">
			<span class="iconfont loadingIcon" style="margin:0 auto;font-size:3rem;color:#f4cf5c;display:inline-block"></span>
		</div>
	</div>
```

为了使用方便，这两种`loading`的样式都写在行内

