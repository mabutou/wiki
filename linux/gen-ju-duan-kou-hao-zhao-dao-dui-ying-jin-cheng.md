# 根据端口号，找到对应进程

安装netstat

```
yum install net-tools     [On CentOS/RHEL]
apt install net-tools     [On Debian/Ubuntu]
zypper install net-tools  [On OpenSuse]
pacman -S net-tools      [On Arch Linux]
```

查询某个端口连接数

```
netstat -nat|grep -i "3306"|wc -l
```

使用 lsof 找出 pid

```
lsof -i:22
```

或使用 netstat 找出 pid

```
#找出非监听端口
netstat -ntp | grep ":22"

#找出监听端口
netstat -ntpl | grep ":22"
```

1. 使用 ps 找出进程名

```
ps -ef|grep $pid
```
