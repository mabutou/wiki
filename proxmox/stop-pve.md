# stop pve

```text
killall -9 corosync
systemctl stop pve-cluster
systemctl stop pvedaemon
systemctl stop pveproxy
systemctl stop pvestatd
```

