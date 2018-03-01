### 参考
http://blog.csdn.net/21cnbao/article/details/56275456

### 架构
Docker中可能涉及到3个机器或者更多机器，一个运行docker命令的client， 一个包含images并以容器(container)形式运行image的主机，一个docker的images仓库。client与docker host上面的docker daemon通信。当然docker client和host可以运行于一台机器（我们做实验的时候是一台），默认的docker仓库是Docker Hub。

![](http://img.blog.csdn.net/20170221093551818?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvMjFjbmJhbw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

一般的流程中,client发pull命令从仓库把image拉到docker host，然后通过run命令指挥image到host上面弄一个container来跑这个image。

当然也可以是相反的流程，client 通过build命令在host上面创建一个自己的image，然后通过push命令把image推到仓库。之后这个image可以被别的人或者自己pull。


### 菜鸟教程架构图

![](http://www.runoob.com/wp-content/uploads/2016/04/576507-docker1.png)

### docker在windows 7上连接终端（ssh）

首先需要知道是当前docker的虚拟IP地址：192.168.99.100

查看C:\Users\Administrator\.docker\machine\machines\default 下的config.json文件

这里的用户名默认是：docker  密码默认：tcuser  端口：22

### Docker使用pure-ftp的方法及配置

http://blog.csdn.net/k21325/article/details/72844514

### Docker 与 Docker Machine 的区别

https://www.cnblogs.com/sparkdev/p/7066789.html

Docker 是一个 Client-Server 架构的应用，人家是有官称的：Docker Engine。Docker 只是大家对 Docker Engine 的昵称，当然 Docker 还有其他的意思，比如一家公司的名称。简单起见，本文中的 Docker 等同于 Docker Engine。

提到 Docker 我们必须要知道它包含了三部分内容：

1. Docker daemon
2. 一套与 Docker daemon 交互的 REST API
3. 一个命令行客户端

下图很清晰的展示了它们之间的关系：

![](https://images2015.cnblogs.com/blog/952033/201706/952033-20170622190650538-1960823992.png)

Docker Machine 则是一个安装和管理 Docker 的工具。它有自己的命令行工具：docker-machine。
