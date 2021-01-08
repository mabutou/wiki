# firewall-cmd

```text
firewall-cmd --zone=public --list-rich-rules
firewall-cmd --zone=public --add-port=8000/tcp --permanent
firewall-cmd --permanent --add-rich-rule="rule family="ipv4" source address="172.17.0.0/16" accept"
firewall-cmd --reload
```

