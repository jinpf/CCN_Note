#CCNchat聊天实验
##单机版
首先启动ccnd： `ccndstart`

之后直接输入命令 `ccnchat  ccnx:/test_room` 便可启动聊天程序

##双机版
条件：两台电脑可以互相ping同

###启动CCNx服务：
<!--lang:shell-->
	ccndstart
###在两台电脑上分别用ccndc命令添加ccnd转发表项：
<!--lang:shell-->
	# A机添加到B机通信的转发表项（如）：
	ccndc  add ccnx:/jinpf.chat udp 10.0.2.4（B机IP）
	# B机添加到A机通信的转发表项（如）：
	ccndc  add ccnx:/jinpf.chat udp 10.0.2.15（A机IP）
	
	#添加结果可以通过ccndstatus命令查看

###分别启动聊天程序进行聊天
<!--lang:shell-->
	#A机上建立聊天室：
	ccnchat ccnx:/jinpf.chat/chat_room0
	#B机上加入聊天室：
	ccnchat ccnx:/jinpf.chat/chat_room0
![](./pic/ccnchat0.png)

###删除刚添加的FIB路由表项

在A机上，首先输入 `ccndstatus` 查看，显示如下：

![](./pic/ccnchat1.png)

注意：faceid：7为手动添加的表项

执行命令：
<!--lang:shell-->
	ccndc del ccnx:/jinpf.chat face 7
	ccndc destroy face 7	

之后执行命令 `ccndstatus` 查看，显示如下：

![](./pic/ccnchat2.png)

相关表项已被删除

除了上述方法，最简单的删除表项的方法就是先执行 `ccndstop` ，再执行 `ccndstart`。