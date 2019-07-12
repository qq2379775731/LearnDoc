### 标题

安装eclipse及环境配置

---

### 时间

2017-4-28

---

### 内容

1.下载jdk , jdk-8u77-linux-x64.tar.gz
2.下载 eclipse, eclipse-jee-mars-2-linux-gtk-x86_64.tar.gz
注：我下载的都是64位的，因为我的系统是64位系统
3.将jdk解压到 /opt/jvm/文件夹中
操作步骤：

```shell
sudo mkdir /opt/jvm
sudo tar zxvf jdk-8u77-linux-x64.tar.gz -C /opt/jvm
```

4.配置jdk的环境变量，打开 /etc/profile文件（sudo vim /etc/profile），在文件末尾添加下语句：

```shell
export JAVA_HOME=/opt/jvm/jdk1.8.0_77
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH
```

保存后退出。
使其立即生效：

```shell
sudo source /etc/profile
```

查看是否安装成功：java -version  出现
说明jdk安装成功。
5.安装 eclipse  将其解压到/opt/文件夹中

```shell
sudo tar zxvf eclipse-jee-mars-2-linux-gtk-x86_64.tar.gz -C /opt/jvm
```

6.创建eclipse桌面快捷方式图标。

```shell
cd desktop
sudo touch eclipse.desktop
sudo vim eclipse.desktop
```

输入以下内容：

[Desktop Entry]
Encoding=UTF-8
Name=Eclipse
Comment=Eclipse
Exec=/opt/eclipse/eclipse
Icon=/opt/eclipse/icon.xpm
Terminal=false
StartupNotify=true
Type=Application
Categories=Application;Development;

保存。

执行:`sudo chmod u+x eclipse.desktop` 将其变为可执行文件.
在桌面打开 eclipse ，结果提示没有安装JDK，JRE环境，明明我们安装过。
解决方法：在/opt/eclipse/文件夹中创建一个指向JRE路径的软链接。

```shell
$sudo ln -sf $JRE_HOME jre
```

打开Eclipse
到此eclipse就全部安装完啦。

---

### 注释

上面安装eclipse,jdk的路径可自定(之后的配置路径都要随之修改)，如若安装在/home及用户目录下，会因
用户权限不够而无法适用jre软链接，可以在用户环境变量中配置jdk或安装eclipse到别处

---

### 获取路径

http://www.linuxidc.com/Linux/2016-07/133482.htm

---

### 其他



------

