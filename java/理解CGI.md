## 参考 
https://www.cnblogs.com/liuzhang/p/3929198.html

##  当我们在谈到cgi的时候，我们在讨论什么

最早的Web服务器简单地响应浏览器发来的HTTP请求，并将存储在服务器上的HTML文件返回给浏览器，也就是静态html。
事物总是不断发展，网站也越来越复杂，所以出现动态技术。
但是服务器并不能直接运行 php，asp这样的文件，自己不能做，外包给别人吧，但是要与第三做个约定，我给你什么，然后你给我什么，
就是握把请求参数发送给你，然后我接收你的处理结果给客户端。那这个约定就是 common gateway interface，简称cgi。
这个协议可以用vb，c，php，python 来实现。cgi只是接口协议，根本不是什么语言。下面图可以看到流程 

![CGI 流程图](https://images0.cnblogs.com/blog/353089/201408/222132422994681.gif "CGI流程")


##  WEB服务器与cgi程序交互

WEB服务器将根据CGI程序的类型决定数据向CGI程序的传送方式，一般来讲是通过标准输入/输出流和环境变量来与CGI程序间传递数据。 如下图所示：

![CGI 交互图](https://images0.cnblogs.com/blog/353089/201408/222140260037310.gif "CGI交互")

CGI程序通过标准输入（STDIN）和标准输出（STDOUT）来进行输入输出。此外CGI程序还通过环境变量来得到输入，操作系统提供了许多环境变量，它们定义了程序的执行环境，应用程序可以存取它们。Web服务器和CGI接口又另外设置了一些环境变量，用来向CGI程序传递一些重要的参数。CGI的GET方法还通过环境变量QUERY-STRING向CGI程序传递Form中的数据。 下面是一些常用的CGI环境变量：

| 变量名 | 描述 | 
| - | - |
|CONTENT_TYPE|这个环境变量的值指示所传递来的信息的MIME类型。目前，环境变量CONTENT_TYPE一般都是：application/x-www-form-urlencoded,他表示数据来自于HTML表单。| 
|CONTENT_LENGTH|如果服务器与CGI程序信息的传递方式是POST，这个环境变量即使从标准输入STDIN中可以读到的有效数据的字节数。这个环境变量在读取所输入的数据时必须使用。|
|HTTP_COOKIE|客户机内的 COOKIE 内容。|
|HTTP_USER_AGENT|提供包含了版本数或其他专有数据的客户浏览器信息。|
|PATH_INFO|这个环境变量的值表示紧接在CGI程序名之后的其他路径信息。它常常作为CGI程序的参数出现。|
|QUERY_STRING|如果服务器与CGI程序信息的传递方式是GET，这个环境变量的值即使所传递的信息。这个信息经跟在CGI程序名的后面，两者中间用一个问号'?'分隔。|
|REMOTE_ADDR|这个环境变量的值是发送请求的客户机的IP地址，例如上面的192.168.1.67。这个值总是存在的。而且它是Web客户机需要提供给Web服务器的唯一标识，可以在CGI程序中用它来区分不同的Web客户机。|
|REMOTE_HOST|这个环境变量的值包含发送CGI请求的客户机的主机名。如果不支持你想查询，则无需定义此环境变量。|
|REQUEST_METHOD|提供脚本被调用的方法。对于使用 HTTP/1.0 协议的脚本，仅 GET 和 POST 有意义。|
|SCRIPT_FILENAME|CGI脚本的完整路径|
|SCRIPT_NAME|CGI脚本的的名称|
|SERVER_NAME|这是你的 WEB 服务器的主机名、别名或IP地址。|
|SERVER_SOFTWARE|这个环境变量的值包含了调用CGI程序的HTTP服务器的名称和版本号。例如，上面的值为Apache/2.2.14(Unix)|
