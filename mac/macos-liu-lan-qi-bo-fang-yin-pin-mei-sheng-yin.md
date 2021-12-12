# MacOS 浏览器播放音频没声音

* 系统设置的音频输出选项有可能此时也看不到对应设备。
* 重置coreaudiod进程：

```
sudo killall coreaudiod
```

