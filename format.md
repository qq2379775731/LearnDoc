### 标题

tomcat编码改为UTF-8

---

### 时间



---

### 内容

tomcat8以后默认编码格式是utf-8；7之前的都是iso8859-1
如果默认情况下，tomcat使用的的编码方式：iso8859-1 
修改tomcat下的conf/server.xml文件
找到如下代码：

```xml
<Connector port="8080" protocol="HTTP/1.1" connectionTimeout="20000" redirectPort="8443" />
```

这段代码规定了Tomcat监听HTTP请求的端口号等信息。
可以在这里添加一个属性：URIEncoding，将该属性值设置为UTF-8，即可让Tomcat（默认ISO-8859-1编码）以UTF-8的编码处理get请求。
修改完成后：

```xml
<Connector port="8080"  protocol="HTTP/1.1" connectionTimeout="20000" redirectPort="8443" URIEncoding="UTF-8" />
```

---

### 注释



---

### 获取路径



---

### 其他



------

