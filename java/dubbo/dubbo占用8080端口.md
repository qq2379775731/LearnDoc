### 标题

dubbo占用8080端口

------

### 时间

2019-7-16

------

### 错误提示



------

### 原因

zookeeper中有个内嵌的管理控制台是通过jetty启动，会占用8080 端口。

------

### 解决方法

（1）删除jetty。
（2）修改端口。
修改方法的方法有两种，一种是在启动脚本中增加 -Dzookeeper.admin.serverPort=你的端口号.一种是在zoo.cfg中增加admin.serverPort=没有被占用的端口号
（3）停用这个服务，在启动脚本中增加"-Dzookeeper.admin.enableServer=false"

------

### 注释



------

### 获取路径

https://blog.csdn.net/zhongguozhichuang/article/details/53098795

------

