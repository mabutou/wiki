# hetzner\_box



username xxx

上传ssh公钥（23端口）

```text
cat .ssh/id_rsa.pub >> storagebox_authorized_keys (公钥汇总)

echo -e "mkdir .ssh \\n chmod 700 .ssh \\n put storagebox_authorized_keys .ssh/authorized_keys \\n chmod 600 .ssh/authorized_keys" | sftp -P 23 xxx@xxx.your-storagebox.de
```

挂载命令

```text
sftp -oPort=23 xxx@xxx.your-storagebox.de
```

传输

```text
rsync -e 'ssh -p 23' -avP access.log xxx@xxx.your-storagebox.de:/home

rsync -e 'ssh -p 23' -avP xxx@xxx.your-storagebox.de:/home/xxx.7z ./
```

```text
scp -P 23 access.log xxx@xxx.your-storagebox.de:/home
```

