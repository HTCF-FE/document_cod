# 用户操作步骤及当前标识

框架提供操作步骤及当前标识的UI组件，有两种方式，效果如下：
 
<iframe src="./demo/stepAction/stepAction.html" width="700px" height="400px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>
   
说明：
   
1. 需要引入`stepAction.css`或`stepAction.less` 
  
2. `DOM`结构 

```  
<ul class="mui-row stepAction">
    <li num="1" class="mui-col-sm-4 mui-col-xs-4">
        <div class="stepLi">
			<span>1</span>
			<p>第一步</p>
		</div>
    </li>
    <li num="2" class="mui-col-sm-4 mui-col-xs-4 action">
        <div class="stepLi">
			<span>2</span>
			<p>第二步</p>
		</div>
    </li>
    <li num="3" class="mui-col-sm-4 mui-col-xs-4" >
        <div class="stepLi">
			<span>3</span>
			<p>第三步</p>
		</div>
    </li>
</ul>
```

`stepAction`为该组件的容器，当前的步骤用`action`标识。

这里使用了`mui`的栅格，详情见——多个元素水平放置（如：底部导航）篇

这里用三步的情况举例，若是增加或减少，需要对应修改`li`的`mui-col-sm-*   mui-col-xs-*`的数字




