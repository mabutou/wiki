# hack wechat sqlite

```text
# login
ls -l ~/Library/Containers/com.tencent.xinWeChat/Data/Library/Application\ Support/com.tencent.xinWeChat/*/*/Contact/*.db
copy **.db file
# logout
lldb -p $(pgrep WeChat)
br set -n sqlite3_key
continue
#login
memory read --size 1 --format x --count 32 $rsi
# get key
```

```text
#!/usr/bin/python
source = """
0x600002457b60: 0xb7 0x14 0x95 0xab 0xc5 0x69 0x41 0x35
0x600002457b68: 0x99 0x26 0x36 0xae 0xce 0x04 0x90 0xef
0x600002457b70: 0x5b 0x5c 0x66 0xde 0x1a 0x32 0x2a 0x0a
0x600002457b78: 0xba 0x71 0xf6 0xc5 0x8e 0xa7 0xc8 0x0d
"""
key = '0x' + ''.join(i.partition(':')[2].replace('0x', '').replace(' ', '') for i in source.split('\n')[1:5])
print(key)
```



