# 展开收起动作

框架为列表提供了展开收起动作，需要引入`js`文件`openOrClose.js`。

效果：
 
<iframe src="./demo/select/openClose.html" width="500px" height="400px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>

  
      
### 使用方法 
  
1. `DOM`结构： 

``` 
 <div class="actionWrap">  -----展开收取的列表
		<div class="actioinList"></div>  ----列表，可以多条
 		……
 </div>
 <div class="actionBtn"></div> ----展开收起按钮
```

不论页面打开时默认展示多少条，点击展开时都可以完全展开，收起时可以收起到最开始的状态，不受默认显示条数的限制

2. 保证上面的`DOM`结构，`openOrClose.js`会自动为按钮监听点击事件

3. 点击`actionList`，会自动把当前这一条数据置为第一条