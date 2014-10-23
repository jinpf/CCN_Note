#CCNx安装
原文摘自：[http://www.ndner.cn/?p=77](http://www.ndner.cn/?p=77) **其原为ccnx-0.6.2的安装教程，在ccnx-0.8.2目前也适用**

**CCNx协议是针对终端到终端的应用程序之间的通信而设计的，所以它被集成到应用程序，而不是被实现为一个单独的层。**

##1.准备工作
在CCNx官方网站的发布页面下载安装包并解压，或者在Github：[https://github.com/ProjectCCNx/ccnx](https://github.com/ProjectCCNx/ccnx)下载也行
<!--lang:shell-->
	git clone https://github.com/ProjectCCNx/ccnx.git
	cd ccnx
	git checkout ccnx-0.8.2
之后各种依赖包：

* 一些必备开发包

<!--lang:shell-->
	sudo apt-get install python-dev libssl-dev libexpat1-dev libxml2-dev

* 安装OpenJDK（使用Android时要用到）

<!--lang:shell-->
	sudo apt-get install openjdk-7-jdk
* 安装libpcap-dev（跟踪和记录数据包的）

<!--lang:shell-->
	sudo apt-get install libpcap-dev
* 安装athena-jot（输出数据用的）

<!--lang:shell-->
	sudo apt-get install athena-jot
* 安装ant（类似于make的编译工具（针对Java））

<!--lang:shell-->
	sudo apt-get install ant
* 安装libecryptfs0 （加密文件系统，CCNx很重视对内容的加密保护）

<!--lang:shell-->
	sudo apt-get install libecryptfs0
* 安装了automake（用来产生GNU标准的Makefiles）

<!--lang:shell-->
	sudo apt-get install automake
* 安装gawk（一种模式扫描和处理的语言）

<!--lang:shell-->
	sudo apt-get install gawk

至此，官方的链接InstallingCCNx 中的准备软件和README中提到的都已经安装好了。

##2.编译CCNx
在源代码的根目录下配置并编译：
<!--lang:shell-->
	./configure
	make
测试：
<!--lang:shell-->
	make test
测试这一步比较慢，测试完成就安装结束。

##3.安装
<!--lang:shell-->
	make install