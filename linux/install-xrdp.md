# install xrdp

```text
卸载 tightvncserver (避免连接报错)
apt-get purge tightvncserver xrdp
apt-get install tightvncserver xrdp
adduser xrdp ssl-cert
systemctl enable xrdp
systemctl restart xrdp

tail -f /var/log/xrdp.log
tail -f /var/log/xrdp-sesman.log
```

