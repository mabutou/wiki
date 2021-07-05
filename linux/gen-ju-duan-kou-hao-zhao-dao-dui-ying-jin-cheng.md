# 根据端口号，找到对应进程

使用 lsof 找出 pid

```text
lsof -i:22
```

或使用 netstat 找出 pid

```text
#找出非监听端口
netstat -ntp | grep ":22"

#找出监听端口
netstat -ntpl | grep ":22"
```

1. 使用 ps 找出进程名

```text
ps -ef|grep $pid
```

