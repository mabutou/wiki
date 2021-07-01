# 修改引导卷大小

web控制台编辑大小。

### 重建分区表

1. 安装软件

Debian/Ubuntu

```text
apt -y install cloud-guest-utils gdisk
```

Centos/Oracle

```text
yum install cloud-guest-utils gdisk
```

1. 调整分区表 不一定是 1，df -hl 看下容量最多的区是多少就写几

```text
growpart /dev/sda 1
```

如果报错： unexpected output in sfdisk –version \[sfdisk，来自 util-linux 2.23.2\]

执行下面这句修复，之后再执行 growpart /dev/sda 3

```text
LANG=en_US.UTF-8
```

1. 调整分区

Debian/Ubuntu

```text
resize2fs /dev/sda3
```

调整ext4的分区  
   Centos/Oracle

```text
xfs_growfs /
```

查看是否生效（有可能没生效，重启后再看）

```text
 df -h
```

重启

```text
reboot
```

