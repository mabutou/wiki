# 常规日志ip统计

```text
grep -E -o "([0-9]{1,3}[\.]){3}[0-9]{1,3}" xxx.log|sort|uniq -c|sort -nr > ip.txt
```

