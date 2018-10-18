# GitBook使用方法（本地命令行版）

`GitBook`无论访问网页版还是下载编辑器使用，网络速度都很慢，又不想每次都翻墙，因此这里使用本地命令行方式:imp:

### 环境准备

需要安装`node`

需要安装`git`，安装后需能够使用`git bash`，这是用来敲`git`命令的

需要安装`GitBook`，在任意一个文件夹下打开命令行，执行命令：` npm install gitbook-cli -g`

`gitbook-cli`是`GitBook`的命令行工具

安装完后，执行命令` gitbook -V`，查看`GitBook`版本，以验证安装成功


### 创建一本书

1. 没有现成的`git`库，需要在本地建立

	在准备放置这本书的目录中，打开`git bash`，执行命令：`gitbook init`，初始化一本书

	此时会出现两个文件：`README.md`和`SUMMARY.md`

	`README.md`是本书的简介，`SUMMARY.md`是本书的目录



	

