###  Github上面下载文件经常出现无法连接问题。

从Github上直接下载文件时候可能会出现无法连接的情况。例如，从raw.githubusercontent.com 这个域名下载的时候，如果未使用代理或者没有翻墙直接使用国内网络的话。经常会出现无法连接的情况。
当然通过代理和翻墙能够很好地解决这个问题。但是对于一些小白用户没有代理或者翻墙软件怎么办？
有一个比较简单的方法，通过修改本机hosts来解决。
如果是Mac或者Linux用户，直接修改 /etc/hosts 文件（记得使用root权限修改哦）
如果是windows用户，直接修改 C:\WINDOWS\system32\drivers\etc\hosts 文件，记得打开hosts的修改权限哦（不知道怎么打开的直接百度一下，这里就不说了）

添加以下内容到你的hosts文件中。



192.30.253.112    github.com 
192.30.253.119    gist.github.com
151.101.184.133    assets-cdn.github.com
151.101.184.133    raw.githubusercontent.com
151.101.184.133    gist.githubusercontent.com
151.101.184.133    cloud.githubusercontent.com
151.101.184.133    camo.githubusercontent.com
151.101.184.133    avatars0.githubusercontent.com
151.101.184.133    avatars1.githubusercontent.com
151.101.184.133    avatars2.githubusercontent.com
151.101.184.133    avatars3.githubusercontent.com
151.101.184.133    avatars4.githubusercontent.com
151.101.184.133    avatars5.githubusercontent.com
151.101.184.133    avatars6.githubusercontent.com
151.101.184.133    avatars7.githubusercontent.com
151.101.184.133    avatars8.githubusercontent.com
151.101.185.194    github.global.ssl.fastly.net



  这个有用

```css
199.232.68.133  raw.githubusercontent.com
```





```
# github 
204.232.175.78 http://documentcloud.github.com 207.97.227.239 http://github.com 
204.232.175.94 http://gist.github.com 
107.21.116.220 http://help.github.com 
207.97.227.252 http://nodeload.github.com 199.27.76.130 http://raw.github.com 
107.22.3.110 http://status.github.com 
204.232.175.78 http://training.github.com 207.97.227.243 http://www.github.com
```



if above are not avaliable,  go to http://ip.tool.chinaz.com/