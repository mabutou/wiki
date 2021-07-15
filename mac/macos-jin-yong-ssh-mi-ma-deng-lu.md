# macOS\(BSD system\) 禁用 ssh 密码登录

```text
As any BSD system you should toggle off some options in your sshd_:

sudo vim /etc/ssh/sshd_config

UsePam yes # it will not be used
ChallengeResponseAuthentication no
PasswordAuthentication no
kbdInteractiveAuthentication no
```

```text
sudo launchctl unload /System/Library/LaunchDaemons/ssh.plist
sudo launchctl load -w /System/Library/LaunchDaemons/ssh.plist 
```

