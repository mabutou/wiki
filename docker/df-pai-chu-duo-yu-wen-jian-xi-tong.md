# df 排除 多余文件系统

```text
df -h|awk '{if($1 != "overlay" && $1 !="shm" && $1 != "tmpfs") print $0}'
```



