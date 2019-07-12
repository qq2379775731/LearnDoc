### 标题

springMVC下载文件功能实现过程中
显示类型无法找到适合解析的错误

------

### 时间

springMVC下载文件功能实现过程中
显示类型无法找到适合解析的错误

------

### 错误提示

```
[http-nio-8080-exec-25] org.springframework.web.servlet.handler.AbstractHandlerExceptionResolver.logException Resolved 
[org.springframework.web.HttpMediaTypeNotAcceptableException: Could not find acceptable representation]
```

---

### 原因

通过调试发现在springMVC.xml配置文件中定义了

```xml
<bean id="jackson2HttpMessageConverter" class="org.springframework.http.converter.json.MappingJackson2HttpMessageConverter">
        <property name="supportedMediaTypes">
            <list>
                <value>text/html;charset=UTF-8</value>
                <value>application/json;charset=UTF-8</value>
            </list>
        </property>
    </bean>
```

而在java代码中设置的返回类型为

```java
httpHeaders.setContentType(MediaType.APPLICATION_OCTET_STREAM);
```

即"application/octet-stream"

springMVC根据配置无法匹配此类型

------

### 解决方法

在配置中加入"application/octet-stream"类型	

---

### 注释

```xml
<bean id="jackson2HttpMessageConverter" class="org.springframework.http.converter.json.MappingJackson2HttpMessageConverter">
        <property name="supportedMediaTypes">
            <list>
                <value>text/html;charset=UTF-8</value>
                <value>application/json;charset=UTF-8</value>
				<value>application/octet-stream</value>
            </list>
        </property>
    </bean>
```

在网上找过几种方法(如下)发现都不行，于是调试发现错误，现记录网上方法以便以后可能会出现类似错误
http://www.bubuko.com/infodetail-2074195.html

------

### 获取路径



------



