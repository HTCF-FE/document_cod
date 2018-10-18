# 日历

效果如下：

点击可选择日期哦~

<iframe src="./demo/calendar/calendar.html" width="530px" height="300px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>

使用方法：

1. 引入`calendar.js`，此为日历组件的源码

2. `html`页面中放入`DOM`结构

```
	<div class="calendarBox">
	    <i class="iconfont minus">&#xe60f;</i>
	    <div class="iconfont beginput" id="txtBeginDate">
	    	<input class="calendarinput" placeholder="请选择开始日期" />
	    </div>
	    <div class="iconfont endinput" id="txtEndDate">
	    	<input class="calendarinput" placeholder="请选择结束日期"/>
	    </div>
	</div>

```

这里使用的`iconfont`图标已存在本地，见`iconfont`文件夹。

3. 初始化日历组件

```
//获取当天时间
var lowertime = new Date();
var uppertime = new Date();

//结束时间日历
function endTime(){
	$("#txtEndDate").calendar({
	    complement: true,
	    readonly: true, 
	    lowerLimit: lowertime,// 日期下限
	    callback: function () {
	      if($("#txtBeginDateCalendar")){
	        $("#txtBeginDateCalendar").remove();
	      }
	      uppertime=new Date($("#txtEndDate").find('input').val().split("-").join("/"));
	      beginTime()
	    }
	});
}
  
//开始时间日历
function beginTime(){
	$("#txtBeginDate").calendar({
	    complement: true,  
	    readonly: true, 
	    upperLimit: uppertime,   //日期上限
	    callback: function () {                              
	      if($("#txtEndDateCalendar")){
	        $("#txtEndDateCalendar").remove();
	      }
	      lowertime=new Date($("#txtBeginDate").find('input').val().split("-").join("/"));
	      endTime();
	    }
	}); 
}

//页面打开时需要执行一次
beginTime();
endTime();

```

然后就可以愉快地使用了~