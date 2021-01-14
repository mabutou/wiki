# hz 单ip 独服 安装 proxmox 后网卡配置



```text
vim /etc/network/interfaces
```

```text
### Hetzner Online GmbH installimage
#应用interfaces.d中的其他配置文件
source /etc/network/interfaces.d/*
 
#配置loopback设备
auto lo
iface lo inet loopback
iface lo inet6 loopback
 
#设置enp35s0为手动配置模式，这个enp35s0看你原本配置文件里是啥
iface enp35s0 inet manual
 
#配置用于开vm的bridge
# xxx 替换为实际地址
auto vmbr0
iface vmbr0 inet static
address xxx
netmask 255.255.255.192
gateway xxx
broadcast xxx
bridge_ports enp35s0
bridge_stp off
bridge_fd 0
#别少了，改成自己的
up route add -net xxx netmask xxx gw xxx dev enp35s0
 
#配置IPv6
iface vmbr0 inet6 static
address xxx
netmask 64
gateway fe80::1
 
#配置用于VM之间内网传输的bridge
auto vmbr1
iface vmbr1 inet static
address 10.10.10.1
netmask 255.255.255.0
bridge_ports none
bridge_stp off
bridge_fd 0
#如果需要小鸡能够通过内网IP使用母鸡的网络访问外网，请添加下面的
post-up echo 1 > /proc/sys/net/ipv4/ip_forward
post-up iptables -t nat -A POSTROUTING -s '10.10.10.0/24' -o vmbr0-j MASQUERADE
post-down iptables -t nat -D POSTROUTING -s '10.10.10.0/24' -o vmbr0 -j MASQUERADE
```

