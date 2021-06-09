# 转发本地代理到服务器

```text
# 转发本地端口到远程
ssh -R localhost:6152:localhost:6152 xxx@xxx
ssh -R localhost:6153:localhost:6153 xxx@xxx
配置ip
export hostip=localhost

export https_proxy=http://${hostip}:6152
export http_proxy=http://${hostip}:6152
export all_proxy=socks5://${hostip}:6153
git config --global http.proxy 'socks5://${hostip}:6153'
git config --global https.proxy 'socks5://${hostip}:6153'
alias curl="curl -x ${hostip}:6152"
alias wget="wget -e "https_proxy=${hostip}:6153""
echo 'Set proxy successfully'
```



