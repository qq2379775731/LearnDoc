### Docker命令

```shell
# 列举docker镜像
$  docker images
# 搜索远程镜像
$  docker search 镜像名
# 拉取远程镜像
$  docker pull 镜像名[:TAG]
# 删除镜像
$  docker rmi 镜像名[:TAG]
# 运行容器  --name(定义容器名) -d(后台运行) -p 主机端口:容器程序端口(将容器内运行程序的端口映射到主机上)
$  docker run --name 容器名 -d 镜像名[:TAG]
# 查看运行中的容器 -a(查看所有容器)
$  docker ps
# 停止容器运行
$  docker stop 容器id
# 删除容器
$  docker rm 容器id
# 查看容器日志
$  docker logs 容器名
```





