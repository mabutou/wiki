# ripgrep 筛选指定时间范围日志

```text
yum install yum-utils -y
yum-config-manager --add-repo=https://copr.fedorainfracloud.org/coprs/carlwgeorge/ripgrep/repo/epel-7/carlwgeorge-ripgrep-epel-7.repo
yum install ripgrep -y
```

```text
rg "04/Mar/2021" access.log | sed  -n '/00:00:00/,/23:59:59/p' > 04-gateway01.log
```



