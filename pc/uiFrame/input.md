# input输入框

`input`输入框可以分成几类：

1. 一行只有一个输入框，如手机号码、姓名

2. 一行内有输入框和图片，如图文验证码

3. 一行内有输入框和按钮，如短信验证码

效果：
 
<iframe src="./demo/form/formInput.html" width="400px" height="340px" frameborder="0" scrolling="no" style="border: 1px dashed #ccc;padding: 20px;"> </iframe>

分别说明如下：

### 一行只有一个输入框

`DOM`结构如下：

```
<!-- 表单容器 -->
<div class="inputDom">
    <!-- 这是一个表单元素 -->
    <div class="card-input-row">
    	<!-- 该表单元素的label -->
        <label>该表单元素的label</label>
        <!-- 输入框-->
        <div class="inputRow">
            <input type="text" placeholder="请输入********" needCheck="true">
            <!-- 输入框的x按钮 --> 
            <i class="iconfont">&#xe649;</i>
        </div>
    </div>
</div>
```

以这个银行预留手机号的表单元素为例：

1. `label`标签后，是`inputRow`，里面包括`input`输入框和`x`按钮

2. `input`输入框的`placeholder`和`maxlength`根据实际情况设置

### 图文验证码

`DOM`结构如下：

```
<div class="card-input-row">
    <label>请输入图文验证码</label>
    <div class="clearfix">
        <!-- 输入框-->
        <div class="inputRow sms-code-input"> 
            <input type="text" placeholder="请输入图文验证码" maxlength="4" needCheck="true">
            <i class="iconfont">&#xe649;</i>
        </div>
        <!-- 图文验证码 -->
        <img class="verify-img" src="" > 
    </div>
</div>
```
1. `label`标签后，是`clearfix`，由于`input`和图片是`float`并列的，这里使用`clearfix`清除浮动

2. `label`后是`inputRow`，里面包括`input`输入框和`x`按钮

3. `inputRow`后，是`verify-img`，为图文验证码的图片
  
4. 由于此时`input`输入框的宽度变短，此时在`inputRow`上多了`class`为`sms-code-input`，重置了原来的样式


### 短信验证码

`DOM`结构如下：

```
<div class="card-input-row">
    <label>请输入短信验证码</label>
    <div class="clearfix">
        <!-- 输入框-->
        <div class="inputRow sms-code-input"> 
            <input type="text" placeholder="请输入短信验证码" maxlength="6" needCheck="true">
            <i class="iconfont code">&#xe649;</i> 
        </div>
        <button class="send-sms-btn">获取短信验证码</button>
        <div class="voice">收不到验证码？</div>
    </div>
</div>
```
1. `label`标签后，是`clearfix`，由于`input`和图片是`float`并列的，这里使用`clearfix`清除浮动

2. `label`后是`inputRow`，里面包括`input`输入框和`x`按钮

3. `inputRow`后，是`send-sms-btn`，为短信验证码的按钮

4. `send-sms-btn`后，是`voice`，为“收不到验证码”，为了用户收不到短信验证码的情况使用，默认是隐藏的

5. 由于此时`input`输入框的宽度变短，此时在`inputRow`上多了`class`为`sms-code-input`，重置了原来的样式