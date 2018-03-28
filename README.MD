tomcat9-cgi-for-python3是一套完全配置好的python3 CGI运行环境！

###1.使用方式
~~~
下载解压即可
~~~

###2.python3 cgi 文件存放路径
~~~
/apache-tomcat-9.0.6/webapps/ROOT/WEB-INF/cgi/
~~~


###3.运行
~~~
sh /apache-tomcat-9.0.6/bin/startup.sh
~~~

###4.关闭
~~~
sh /apache-tomcat-9.0.6/bin/shutdown.sh
~~~

###5.访问
~~~
http://localhost:8080/cgi-bin/hello.py
~~~

###6.主要配置修改
~~~
1、/conf/context.xml:
<Context>这一行修改为
<Context privileged="true">
2、/cong/web.xml
注释的释放注释
  <servlet-mapping>
        <servlet-name>cgi</servlet-name>
        <url-pattern>/cgi-bin/*</url-pattern>
    </servlet-mapping>
增加内容
<servlet>
        <servlet-name>cgi</servlet-name>
        <servlet-class>org.apache.catalina.servlets.CGIServlet</servlet-class>
        <init-param>
            <param-name>clientinputTimeout</param-name>
            <param-value>100</param-value>
        </init-param>
        <init-param>
            <param-name>debug</param-name>
            <param-value>0</param-value>
        </init-param>
        <init-param>
            <param-name>passShellEnvironment</param-name>
            <param-value>true</param-value>
        </init-param>
        <init-param>
          <param-name>cgiPathPrefix</param-name>
          <param-value>WEB-INF/cgi</param-value>
        </init-param>
        <init-param>
            <param-name>executable</param-name>
            <param-value>/Library/Frameworks/Python.framework/Versions/3.6/Resources/Python.app/Contents/MacOS/Python</param-value>
        </init-param>
        <load-on-startup>5</load-on-startup>
    </servlet>

~~~

