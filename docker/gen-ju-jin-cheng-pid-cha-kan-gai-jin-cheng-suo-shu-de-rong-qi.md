# 根据进程pid查看该进程所属的容器

```text
docker ps -q | xargs docker inspect --format '{{.State.Pid}}, {{.Name}}' | grep "PID"
```

