### 标题

安装及配置使用gnu global

---

### 时间

2017-5-6

---

### 内容

一.安装依赖库

```shell
$sudo apt build-dep global  
$sudo apt install libncurses5-dev libncursesw5-dev 
```

二.下载安装包并解压
三.安装

```shell
./configure --with-sqlite3   //gtags可以使用Sqlite3作为数据库，在编译时需要加这个参数  
make -j4     //四线程并行编译  
make check  
sudo make install  
sudo make install check  

```

四.使用
1.进入源码项目所在的根目录，执行

`gtags –v    #生成tag文件。 `

当然，也可以加上--sqlite3参数，下面是—help给出的参数帮助信息。
[plain] view plain copy 在CODE上查看代码片派生到我的代码片
Use Sqlite 3 API to make tag files. By default, BSD/DB 1.85 API is used.  
To use this option, you need to invoke configure script with  
--with-sqlite3 in the build phase. 
2.tag文件生成后，执行 htags命令生成HTML文件

`htags -DfFnva -t '这里填入你想要的主页title' `

3.打开生成的HTML文件夹下的html文件即可

---

### 注释

1.安装后发现无法使用search功能，出现如下信息

```shell
# ! /usr/bin/perl  

# ------------------------------------------------------------------  

# YOU ARE COMING TO THE DESTINATION ALMOST.PLEASE DO A LITTLE EFFORT.  

#  

# How to setup search form of htags  

# =================================  

#  

# You should start HTTP server so that thisscript is executed as a CGI script.  

# Setup procedure for it depends on theHTTP server which you are using.  

#  

# Use of htags-server(1) is recommended.It's simple.  

# $ htags -Df  

# $ htags-server  

# Please access at http://127.0.0.1:8000  

# Python2 http/cgi server  

# Serving HTTP on 127.0.0.1 port 8000 ...  

# You can see the output of htags through'http://127.0.0.1:8000'.  

#  

# If you are using Apache, 'HTML/.htaccess'might be helpful for you.  

# ------------------------------------------------------------------  
```

解决方法：按照信息中的方法开启服务即可

```shell
$htags-server
然后要在网页输入localhost：8000即可
（若无法方法网站：可使用$htags-server –b ip地址 端口号）
```

---

### 获取路径

http://blog.csdn.net/leon57/article/details/68930359

---

### 其他

gnu global官网：https://www.gnu.org/software/global/global.html

在ecmas中使用global，打开任意一个项目源码目录下的源码文件，按alt+x，然后输入gtags-mode即可转换为gtags
移动光标到要查看的对象处，按alt+.即可跳转

------

