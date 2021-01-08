# rsync command



* 启用压缩
* 同步特定时间内文件

```text
rsync -av --delete --info=progress2 --files-from=<(find /xxpath/ -name ".tar" -mtime 0 -type f -exec basename {} \;) /path /path
```

