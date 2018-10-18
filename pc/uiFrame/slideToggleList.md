# 列表内容可展开收起

本框架为列表提供了展开收起的动作。

<iframe src="./demo/list/list_2.html" width="600px" height="400px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>

说明：

1. 需要引入`list.css`

2. `DOM`结构：

	```
	<ul class="listUl">  
	      <li class="item">
	          <div class="title">
	              <span class="message">标题标题标题标题标题标题</span>
	              <i class="iconfont"></i>
	          </div>
	          <div class="detail">展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容</div>
	      </li>
	      <li class="item">
	          <div class="title">
	              <span class="message">标题标题标题标题标题标题</span>
	              <i class="iconfont"></i>
	          </div>
	          <div class="detail">展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容展开内容</div>
	      </li>
	</ul>

	```

3. 需要添加实现展开收起效果的`js`语句：

	```
	$(document).on('click','.listUl .item .title',function(){
		var $this = $(this);

		if( $this.next('.detail').is(":visible") ){
			$this.find(".down").html("&#xe623;");
	    }else{
	    	$this.find(".down").html("&#xe624;");
	    }
	    $this.next('.detail').slideToggle();
	})
	```