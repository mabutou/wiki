# Linux logrotate

```text
❯ sudo cat /etc/logrotate.d/iotop
/home/xxx/iotop.log {
  daily
  rotate 3
  compress
  missingok
  notifempty
  dateext
  copytruncate
}
❯ sudo crontab -l
0 0 * * * /usr/sbin/logrotate /etc/logrotate.d/iotop > /dev/null 2>&1 &
```

