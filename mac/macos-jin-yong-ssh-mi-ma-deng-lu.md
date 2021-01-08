# macOS 禁用 ssh 密码登录

```text
As any BSD system you should toggle off some options in your sshd_:

sudo vim /etc/ssh/sshd_config

UsePam yes # it will not be used
ChallengeResponseAuthentication no
PasswordAuthentication no
kbdInteractiveAuthentication no
```

