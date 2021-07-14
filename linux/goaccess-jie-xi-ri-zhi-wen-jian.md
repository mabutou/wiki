# goaccess 解析日志文件

traefik 日志

docker 版本

```text
cat ./traefik.log | docker run -p 7890:7890 --rm -i -e LANG="zh_CN.UTF-8" allinurl/goaccess -a -o html --time-format=%H:%M:%S --date-format=%d/%b/%Y --log-format='%h %^[%d:%t %^] "%r" %s %b "%R" "%u" %^ "%v" %^ %T' --max-items=20 --real-time-html - > ./index.html
```

golang 版本

```bash
goaccess -a -o html --time-format=%H:%M:%S --date-format=%d/%b/%Y --log-format='%h %^[%d:%t %^] "%r" %s %b "%R" "%u" %^ "%v" %^ %T' --max-items=20 --real-time-html -f log.log > index.html
```

