### 标题

配置openssh服务器

---

### 时间

2017-5-15

---

### 内容

1.下载openssh-server

```shell
$sudo apt install openssh-server
2.查看是否开启服务,出现如下服务即可
$

ps -e | grep ssh
1109 ?        00:00:00 sshd
```

3.如果未开启服务

```shell
$sudo server ssh [start|restart]
4.外部链接ssh服务器
Linux:$

ssh user@hostname 如：ssh hhj@192.168.43.103
```

---

### 注释

把虚拟机当服务器
内网访问时使用net或bridge都可，但手机访问时要用bridge模式，把虚拟机的ip地址改为内网ip

```shell
$ifconfig eth0 192.168.*.* netmask 255.255.255.0
```

1.外网访问时如果机器在局域网内则要使用局域网的虚拟服务器功能（或使用花生壳等软件：http://hsk.oray.com/news/2781.html）
2.机器直接连接外网时，可使用虚拟机的端口映射功能
（在vmware palystation下）

```shell
$sudo gedit /etc/vmware/vmnet8/nat/nat.conf打开配置文件
```


在[incomingtcp]下的位置加上你要映射的端口 如：9999（主机映射端口）=192.168.43.103（虚拟机ip）：22（ssh默认端口）

---

### 获取路径



---

### 其他

移动网络和电信网络无法互ping，电信网络无法通过ssh链接移动网络的服务器
Linux下如何修改ip地址
最简单的方法，输入setup，配置界面就出来了～
或者跟一般Linux一样，在/etc/sysconfig/network-scripts下找到ifcfg-eth0文件，编辑：
DEVICE=eth0
IPADDR=192.168.0.254
域名服务器配置文件：/etc/ resolv.conf

以下方法，可使修改直接生效：
修改ip地址

```shell
ifconfig eth0 192.168.0.20 netmask 255.255.255.0
```

修改default gateway

```shell
route add default gw 192.168.0.254
```

修改dns
修改/etc/resolv.conf

修改host name

```shell
hostname fc2
```

启动生效:
修改/etc/sysconfig/network

获取地址：http://www.cppblog.com/niewenlong/archive/2008/06/05/52277.aspx

------

