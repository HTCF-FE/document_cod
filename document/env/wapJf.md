# wap金服的环境配置及启动方法

<!-- toc -->

### 环境准备

需安装`Node`，需全局安装`gulp`和`webpack`

安装好后，准备好项目代码，需要使用`npm`包管理器在项目根目录下安装项目文件`package.json`中的模块

### 安装package.json中的模块

在项目的根目录下执行命令`npm install`

此命令后，因`package.json`中配置了`postinstall`命令，会执行`postinstall`命令，即执行`conf/changeFile.js`文件中的代码

`conf/changeFile.js`文件的任务是从`doc/replaceFile`文件夹中，将文件复制到对应的`npm`安装下来的本地`node_modules`中的模块里，覆盖原来的文件

此操作是由于直接安装下来的模块不满足我们的需求，因此进行了改动，改动如下：

1. 为了自动打出`**?v=*****`格式的版本号，修改了`gulp-rev、gulp-rev-collector、rev-path`三个模块中的`index.js`文件

2. 为了提供`less`文件引用路径的公共变量，在引用文件时，不再在`@import`中使用相对路径`../`，而是直接使用变量定位到目标文件夹，修改了`gulp-less`模块下的`index.js`文件，为该插件新增了`extractPath`参数，用于设置不同的公共路径变量，此变量在`gulpfile.js`中设置，但在此替换的`index.js`文件中接收并处理

3. 为了提供`html`文件打包时`@@include`中引用路径的公共变量，理由同上。。修改了`gulp-advanced-file-include`下的`lib/index.js`文件，为该插件新增了`extractPath`参数，用于设置不同的公共路径变量，此变量在`gulpfile.js`中设置，但在此替换的`index.js`文件中接收并处理

### 执行gulp命令，打包文件，启动项目

最简单的命令是`gulp`，没有任何参数，此时打包的是本地环境股份的代码

可以添加参数`env` ，用来指定不同环境：1--联调环境，2--测试环境，3--预生产环境，4--生产环境，此时命令为：`gulp --env 1/2/3/4`

`env`默认为0（不指定的情况下），表示打包本地代码

也可以添加参数`envOrigin`，用来指定打包明泽代码或者是股份代码：1--表示股份，0--明泽，默认为1,

因此环境命令可以有几下几种可能： 

```
	gulp ，此时打包本地股份代码
	gulp --envOrigin 0, 打包本地明泽代码
	gulp --env 1, 打包联调环境股份代码
	gulp --env 1 --envOrigin 0， 打包联调环境明泽代码
	gulp --env 2，打包测试股份代码
	gulp --env 2 --envOrigin 0， 打包测试明泽代码
```

其他环境以此类推……

执行命令后，执行的是`gulpfile.js`中的代码，会做如下事情：

1. 获取本地`ip`（此`ip`仅在本地和联调环境环境有用）
	
	* 放在`gulp-connect`插件的配置中，当使用`ip`访问页面时，其他在公司内网的人可以访问到该电脑上的页面
	* 替换本地`root.js`文件中的`localIp`这几个字，作为项目中`ajax`的请求地址，本地接口由`gulp-mock-server`插件模拟

2. 判断打包的是明泽代码还是股份代码（仅在本地和联调环境有用）
	
	根据`env`和`envOrigin`的值，替换`root.js`中的env和envOrigin，打包出正确的本地代码

3. 打包各类型的文件，`html、js、less、css、图片`等

4. 监听各文件的修改，打包对应的文件，并重启服务