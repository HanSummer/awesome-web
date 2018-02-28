### 参考
http://blog.csdn.net/21cnbao/article/details/56275456

### 架构
Docker中可能涉及到3个机器或者更多机器，一个运行docker命令的client， 一个包含images并以容器(container)形式运行image的主机，一个docker的images仓库。client与docker host上面的docker daemon通信。当然docker client和host可以运行于一台机器（我们做实验的时候是一台），默认的docker仓库是Docker Hub。

![](http://img.blog.csdn.net/20170221093551818?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvMjFjbmJhbw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

一般的流程中,client发pull命令从仓库把image拉到docker host，然后通过run命令指挥image到host上面弄一个container来跑这个image。

当然也可以是相反的流程，client 通过build命令在host上面创建一个自己的image，然后通过push命令把image推到仓库。之后这个image可以被别的人或者自己pull。


### 菜鸟教程架构图

![](http://www.runoob.com/wp-content/uploads/2016/04/576507-docker1.png)
