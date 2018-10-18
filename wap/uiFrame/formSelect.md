# 表单中的下拉选项

选择类的表单元素（证件类型、生日、发卡银行、省市等）是点击出现选择器，用户选择后，将结果显示到页面上的，
用户不能手动输入。

这类元素，右侧有箭头，看起来跟**列表组件**的结构一样，因此是用**列表组件**的结构实现的。

```
<div class="form-wrap">
	<!-- 证件类型 -->
	<ul class="mui-table-view"> 
	    <li class="mui-table-view-cell mui-collapse">
	        <a class="mui-navigate-right" href="javascript:;" num="" errortip="请选择证件类型">请选择证件类型</a>
	    </li>
	</ul>
</div>
```

可以看出，这完全就是一个列表的结构，因此可以使用列表组件的class属性根据不同的情况有不同的表现。

若需要点击出现选择器，需使用选择器组件，详情见对应文章讲解~