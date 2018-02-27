## 参考
https://www.cnblogs.com/Wonghy/p/5542277.html

## 流程图
![](http://img.my.csdn.net/uploads/201211/06/1352205938_6030.jpg)

1. web客户向Servlet容器发出HTTP请求;

2. Servlet容器解析web的HTTP请求.

3. Servlet容器创建一个HttpRequest对象,在这个对象中封装了http请求信息;

4. Servlet容器创建一个HttpResponse对象;

5. Servlet容器（如果访问的该servlet不是在服务器启动时创建的，则先创建servlet实例并调用init()方法初始化对象）调用HttpServlet的service()方法,把HttpRequest和HttpResponse对象为service方法的参数传给HttpServlet对象;

6. HttpServlet调用HttpRequest的有关方法,获取HTTP请求信息;

7. HttpServlet调用HttpResponse的有关方法,生成响应数据;

8. Servlet容器把HttpServlet的响应结果传给web客户. 

## Tomcat装载servlet三种方法：

1、Serlvet容器启动时自动装载某些Servlet,实现它只需要在web.xml文件中<servlet>  </servlet>之间添加<load-on-startup>1</load-on-startup>，数字越小，优先级越大。

2、在Servlet容器启动时，客户首次向Servlet发送请求

3、Servlet类文件被更新后，重新装载Servlet
