[1]: max file descriptors [4096] for elasticsearch process is too low, increase to at least [65536]

[2]: max number of threads [3818] for user [es] is too low, increase to at least [4096]

[3]: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]



解决办法：

修改 etc/security/limits.conf

sudo vi /etc/security/limits.conf
在文件最后面加上

* soft nofile 65536
* hard nofile 65536
* soft nproc 4096
* hard nproc 4096
注：*后面有空格

修改 /etc/sysctl.conf

sudo vi /etc/sysctl.conf
在文件最后面加上

vm.max_map_count=262144
配置重新生效

sysctl -p
重新启动

