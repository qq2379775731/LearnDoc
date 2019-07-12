### 标题

配置shadowsocks

---

### 时间

2017-4-29

---

### 内容

（一）ubuntu安装shadowsocks
用PIP安装很简单，
```shell
sudo apt-get update
sudo apt-get install python-pip
sudo apt-get install python-setuptools m2crypto
```
接着安装shadowsocks
```shell
pip install shadowsocks
```
如果是ubuntu16.04 直接 (16.04 里可以直接用apt 而不用 apt-get 这是一项改进）
```shell
sudo apt install shadowsocks
```
当然你在安装时候肯定有提示需要安装一些依赖比如python-setuptools m2crypto ，依照提示安装然后再安装就好。也可以网上搜索有很多教程的。
启动shadowsocks
安装好后，在本地我们要用到sslocal ，终端输入sslocal --help 可以查看帮助
通过帮助提示我们知道各个参数怎么配置，比如 sslocal -c 后面加上我们的json配置文件，或者像下面这样直接命令参数写上运行。
比如 
```shell
sslocal -s 11.22.33.44 -p 50003 -k "123456" -l 1080 -t 600 -m aes-256-cfb
```
-s表示服务IP, -p指的是服务端的端口，-l是本地端口默认是1080, -k 是密码（要加""）, -t超时默认300,-m是加密方法默认aes-256-cfb，
为了方便我推荐直接用sslcoal -c 配置文件路径 这样的方式，简单好用。
我们可以在/home/mudao/ 下新建个文件shadowsocks.json  (mudao是我在我电脑上的用户名，这里路径你自己看你的)。内容是这样：
{
"server":"11.22.33.44",
"server_port":50003,
"local_port":1080,
"password":"123456",
"timeout":600,
"method":"aes-256-cfb"
}

server  你服务端的IP
servier_port  你服务端的端口
local_port  本地端口，一般默认1080
passwd  ss服务端设置的密码
timeout  超时设置 和服务端一样
method  加密方法 和服务端一样
确定上面的配置文件没有问题，然后我们就可以在终端输入 sslocal -c /home/mudao/shadowsocks.json 回车运行
（如果继续请不要关闭这个终端）
如果你选择这一种请跳过第二种。你可以去系统的代理设置按照说明设置代理，但一般是全局的，然而我们访问baidu,taobao等着些网站如果用代理就有点绕了，而且还会浪费服务器流量。我们最好配置我们的浏览器让它可以自动切换，该用代理用代理该直接连接自动直接连接。所以请看配置浏览器。
（二）安装GUI 图形界面程序，然后按照提示配置相对应的参数。安装教程地址：shadowsocks-qt5 安装指南（https://github.com/shadowsocks/shadowsocks-qt5/wiki/%E5%AE%89%E8%A3%85%E6%8C%87%E5%8D%97）
在ubuntu上可以这样，通过PPA源安装，仅支持Ubuntu 14.04或更高版本。
```shell
sudo add-apt-repository ppa:hzwhuang/ss-qt5
sudo apt-get update
sudo apt-get install shadowsocks-qt5
```
由于是图形界面，配置和windows基本没啥差别就不赘述了。经过上面的配置，你只是启动了sslocal 但是要上网你还需要配置下浏览器到指定到代理端口比如1080才可以正式上网。
1.配置浏览器
假如你上面任选一种方式已经开始运行sslocal了，火狐那个代理插件老是订阅不了gfwlist所以配置自动模式的话不好使。这里用的是chrome，你可以在Ubuntu软件中心下载得到。
2.安装插件
我们需要给chrome安装SwitchyOmega插件，但是没有代理之前是不能从谷歌商店安装这个插件的，但是我们可以从Github上直接下载最新版 https://github.com/FelisCatus/SwitchyOmega/releases/ （这个是chrome的）然后浏览器地址打开chrome://extensions/，将下载的插件托进去安装。
3.设置代理地址
安装好插件会自动跳到设置选项，有提示你可以跳过。左边新建情景模式-选择代理服务器-比如命名为SS（叫什么无所谓）其他默认之后创建，之后在代理协议选择SOCKS5，地址为127.0.0.1,端口默认1080 。然后保存即应用选项。
4.设置自动切换
接着点击自动切换 ( Auto switch）上面的不用管，在按照规则列表匹配请求后面选择刚才新建的SS，默认情景模式选择直接连接。点击应用选项保存。再往下规则列表设置选择AutoProxy 然后将这个地址填进去，点击下面的立即更新情景模式，会有提示更新成功！
https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt
点击浏览器右上角的SwitchyOmega图标，下面选择自动切换，然后打开google.com试试。

---

### 注释



---

### 获取路径

https://aitanlu.com/ubuntu-shadowsocks-ke-hu-duan-pei-zhi.html

---

### 其他

开机后台自动运行ss
如果你选择了第二种可以不管这个
如果你上面可以代理上网了可以进行这一步，之前我让你不要关掉终端，因为关掉终端的时候代理就随着关闭了，之后你每次开机或者关掉终端之后，下次你再想用代理就要重新在终端输入这样的命令 sslocal  -c /home/mudao/shadowsocks.json ，挺麻烦是不？
我们现在可以在你的ubuntu上安装一个叫做supervisor的程序来管理你的sslocal启动。关于supervisor更多点击这
```shell
sudo apt-get install supervisor
```
安装好后我们可以在/etc/supervisor/目录下找到supervisor.conf配置文件，我们可以用以下命令来编辑
```shell
sudo gedit /etc/supervisor/supervisor.conf
```
在这个文件的最后加上以下内容
```text
[program:shadowsocks]
command=sslocal -c /home/mudao/shadowsocks.json
autostart=true
autorestart=true
user=root
log_stderr=true
logfile=/var/log/shadowsocks.log
```
当然在16.04里你可以直接在/etc/supervisor/conf.d/下新建个文件比如ss.conf然后加入上面内容。
command = 这里json文件的路径根据你的文件路径来填写。确认无误后记得保存。sslocal 和ssserver这两个命令是被存在 /usr/local/bin/下面的，我们要拷贝一份命令文件到/bin
```shell
sudo cp /usr/local/bin/sslocal /bin  (注意空格)
```
注意：16.04 命令在 /usr/bin/下所以就用
```shell
sudo cp /usr/bin/sslocal /bin  (注意空格)
```
现在关掉你之前运行sslocal命令的终端，再打开终端输入sudo service supervisor restart 然后去打开浏览器看看可不可以继续代理上网。你也可以用ps -ef|grep sslocal命令查看sslocal是否在运行。
这个时候我们需要在/etc下编辑一个叫rc.local的文件 ，让supervisor开机启动。
```shell
sudo gedit /etc/rc.local 
```
在这个配置文件的exit 0前面一行加上 service supervisor start 保存。看你是否配置成功你可以在现在关机重启之后直接打开浏览器看是否代理成功。

------

