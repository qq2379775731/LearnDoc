### 标题

安装及配置opengrok

---

### 时间

2017-5-6

---

### 内容

一.安装java（环境配置见‘配置环境变量’）
二.安装tomcat
1.去github官网下载tomcat安装包
2.安装`$tar xvfz apache-tomcat-*.tar.gz  `

3.执行./bin下的startup.sh `$./startup.sh`

打开浏览器输入localhost：8080，如果有响应表明安装成功
三.安装opengrok
1.下载安装包
2.解压安装包

```shell
$tar -xzvf opengrok-*.tar.gz
$cd opengrok-*
$mkdir -p DATA/data  //建立一个专门放索引和数据的目录，可自己选择
$ln -sf <你要看的源码的目录> ‘pwd’/DATA/src  //将你要看的源码的目录映射到src
```

3.修改Opengrok文件，在头部加入如下语句

```text
OPENGROK_DISTRIBUTION_BASE=/opengrok-0.9/lib  	// OpenGrok解压的目录，主要要加上lib  
OPENGROK_INSTANCE_BASE=/opengrok-0.9/DATA    // 前面刚建立的目录  
EXUBERANT_CTAGS=/usr/bin/ctags  // ctags的全部路径  
JAVA_HOME=/usr/java/jdk1.6.0_20  // JAVA安装的目录  
OPENGROK_APP_SERVER="Tomcat"  // 使用的服务是Tomcat。Opengrok也支持glassfish。  
OPENGROK_WAR_TARGET=/apache-tomcat-6.0.26/webapps  // tomcat6的webapps目录
```

4.执行Opengrok

```shell
$./OpenGrok deploy //将source.war复制到tomcat的webapps目录（source.war会自己解压）
$./OpenGrok index //建立索引
```

5.打开浏览器输入localhost：8080/source即可看到源码

---

### 注释

1.遇到缺少logging.properties的错误
将Opengrok/doc下的logging.properties复制到/DATA即可

---

### 获取路径

http://www.xuebuyuan.com/1430163.html?mobile=1
http://blog.csdn.net/yahoozhuo/article/details/5917810

---

### 其他

OpenGrok官网：http://opengrok.github.io/OpenGrok/

------

