### 标题

git绑定github

---

### 时间

2017-4-28

---

### 内容

第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有
id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，
打开Shell（Windows下打开Git Bash），创建SSH Key：

```shell
$ ssh-keygen -t rsa -C "youremail@example.com"
```

你需要把邮件地址换成你自己的邮件地址，然后一路回车，使用默认值即可，
如果一切顺利的话，可以在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
第2步：登陆GitHub，打开“Account settings”，“SSH Keys”页面：
然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容，,点“Add Key”

---

### 注释



---

### 获取路径

http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374385852170d9c7adf13c30429b9660d0eb689dd43a000

---

### 其他

添加远程库：`git remote add origin ssh地址`
添加后，远程库的名字就是origin，这是Git默认的叫法，也可以改成别的，但是origin
这个名字一看就知道是远程库。
推送：`git push -u origin master`
由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分
支关联起来，在以后的推送或者拉取时就可以简化命令`git push  origin master`
克隆库:`git clone ssh地址`

------

