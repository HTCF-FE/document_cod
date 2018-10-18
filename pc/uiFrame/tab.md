# tab标签

框架内提供点击可切换区域的tab标签。点击试试：

<iframe src="./demo/tab/tab.html" width="600px" height="700px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>


说明：

1. 需要引入`tab.css`或`tab.less`

2. 需要引入`tab.js`，提供标签点击的切换动作

3. `DOM`结构

```
	<!-- 第一种 -->
	<div class="tabTypeOne">
		<!-- tab标签 -->
        <div class="tabHeader">
            <span class="tab active" num="0">买入</span>
            <span class="tab" num="1">赎回</span>
        </div>  
        <!-- 内容区域 -->
        <div class="tabBody">
	        <div class="tabContent" num="0">
	        	这是买入区域
	        </div>
	        <div class="tabContent" num="1">
	       		这是赎回区域
	        </div>
	    </div>
    </div>

    <!-- 第二种 -->
    <div class="tabTypeTwo">
		<!-- tab标签 -->
        <div class="tabHeader flexbox">
            <span class="tab flex1 active" num="0">买入</span>
            <span class="tab flex1" num="1">赎回</span>
        </div>  
        <!-- 内容区域 -->
        <div class="tabBody">
	        <div class="tabContent" num="0">
	        	这是买入区域
	        </div>
	        <div class="tabContent" num="1">
	       		这是赎回区域
	        </div>
	    </div>
    </div>

    <!-- 第三种 -->
    <div class="tabTypeThree">
		<!-- tab标签 -->
        <div class="tabHeader flexbox">
            <span class="tab flex1 active" num="0">买入</span>
            <span class="tab flex1" num="1">赎回</span>
        </div>  
        <!-- 内容区域 -->
        <div class="tabBody">
	        <div class="tabContent" num="0">
	        	这是买入区域
	        </div>
	        <div class="tabContent" num="1">
	       		这是赎回区域
	        </div>
	    </div>
    </div>
```

当前标签被添加`class`为`active`。
