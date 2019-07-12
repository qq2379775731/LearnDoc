### 标题

初次开启android studio时自动下载gradle卡机

------

### 时间

2017-4-28

------

### 错误提示



------

### 原因

无法翻阅外网导致无法下载gradle卡机

------

### 解决方法

1.去网上下载好对应版本的gradle
2.复制gradle至～/.gradle/wrapper/dists/（对应gradle）/（临时生成文件夹）/下
$cp */gradle-xx.zip ～/.gradle/wrapper/dists/（对应gradle）/（临时生成文件夹)
3.重新启动即可

------

### 注释

必须要复制gradle安装包而不是解压后的文件

------

### 获取路径



------



