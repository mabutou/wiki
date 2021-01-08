# shell 命令按次数输出v2访问日志的 ip 统计

```text
scp xxx:~/v2ray/v2log/access.log ./
cat access.log  | egrep -o '\s([0-9]{1,3}\.){3}[0-9]{1,3}'|sort|uniq -c|sort -nr > iptime.txt
```

