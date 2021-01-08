# shell proxy

```bash
export hostip=127.0.0.1
export https_proxy=http://${hostip}:8234; export http_proxy=http://${hostip}:8234; export all_proxy=socks5://${hostip}:8235; git config --global http.proxy 'socks5://${hostip}:8234'; git config --global https.proxy 'socks5://${hostip}:8235'; echo 'Set proxy successfully'
alias curl="curl -x ${hostip}:8234"
alias wget="wget -e "https_proxy=${hostip}:8235""
git config --global http.proxy 'socks5://${hostip}:1080' git config --global https.proxy 'socks5://${hostip}:1080'
export https_proxy=http://${hostip}:8001; export http_proxy=http://${hostip}:8001; export all_proxy=socks5://${hostip}:1081
```

