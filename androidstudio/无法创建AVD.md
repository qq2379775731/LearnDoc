### 标题

android studio 无法创建 AVD

------

### 时间

2017-4-26

------

### 错误提示

[  35614]   WARN - roid.tools.ndk.GradleWorkspace - NDK support for project 'My
Application' is disabled because the project doesn't contain any valid native 
configurations. 
[1096629]   WARN - s.RepoProgressIndicatorAdapter - java.io.FileNotFoundExcepti
on: /tmp/StudioDownloadersys-img2-1.xml (没有那个文件或目录) 
[1138379]   WARN - vdmanager.AvdManagerConnection - Failed to create the SD car
d. 
[1138379]   WARN - vdmanager.AvdManagerConnection - Failed to create sdcard in 
the AVD folder. 

------

### 原因

64位系统无法运行32位的程序

------

### 解决方法

安装 32位支持库

```shell
sudo apt-get install libgcc1:i386
```

---

### 注释

注释：
老版本为ia32-lib,但在新版本中被取代

------

### 获取路径

https://askubuntu.com/questions/647940/failed-to-create-sd-card-in-avd-folder

------



