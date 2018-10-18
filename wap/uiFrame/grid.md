# 多个元素水平放置

### 方式一：基于mui的栅格系统

使用时只需在外围容器上添加`.mui-row`，在列上添加 `.mui-col-[sm|xs]-[1-12]`即可。详细使用方法见`mui`官方文档。

适用于元素宽度分配相对成比例的情况，如底部导航：

![PNG](./img/bottomNav.png)


### 方式二：`flexbox`

`css3`的新特性之一~但是在安卓手机尤其是某些华为手机上表现不佳，因此使用请慎重~


### 方式三：借助绝对定位`position:absolute;`

如两个元素并列，a有固定宽度，b没有固定宽度（但必须是块级元素）：
将a设置`position；absolute；`，b元素设置`margin-left`或`margin-right`的值为a元素的宽度。



