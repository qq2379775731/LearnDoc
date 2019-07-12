### 标题

can't find gtk+-2.0

------

### 时间

2017-5-25

------

### 错误提示

```shell
gcc helloworld.c -o helloworld `pkg-config --cflags --libs gtk+-2.0`
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
helloworld.c:1:21: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.

```

---

### 原因

I only had the normal gtk3 files installed, not the developement files needed for cmake to make use of:

------

### 解决方法

```shell
sudo apt-get install build-essential libgtk-3-dev
```

---

### 注释



------

### 获取路径

https://askubuntu.com/questions/779065/pkg-config-not-finding-gtk-3-0

------



