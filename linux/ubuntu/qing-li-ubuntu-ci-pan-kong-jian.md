---
description: '转载自 https://www.cnblogs.com/hsdchenliyang/archive/2018/02/24/8465653.html'
---

# 清理ubuntu磁盘空间

ncdu工具来查看大容量目录和文件

```text
sudo apt-get install ncdu

sudo ncdu /var/log
```

### 1. 删除大容量软件包 <a id="circle-heading-7"></a>

首先安装debian-goodies

```text
sudo apt-get install debian-goodies
```

然后输入下面的命令

```text
dpigs -H
```

输出结果

```text
441.0M texlive-latex-extra-doc
230.1M valgrind-dbg
200.6M chromium-browser
171.4M google-chrome-stable
153.4M linux-image-extra-3.19.0-39-generic
153.4M linux-image-extra-3.19.0-37-generic
151.5M maltego
144.8M wine1.7-amd64
140.6M metasploit-framework
137.4M wine1.7-i386
```

命令默认只会显示前10个结果，可指定结果的个数，比如20个

```text
dpigs -H --lines=20
```



### **2. 删除残余的配置文件** <a id="circle-heading-0"></a>

通常Debian/Ubuntu删除软件包可以用两条命令

```text
sudo apt-get remove <package-name>

sudo apt-get purge <package-name>
```

remove将会删除软件包，但会保留配置文件．purge会将软件包以及配置文件都删除．

找出系统上哪些软件包留下了残余的配置文件

```text
dpkg --list | grep "^rc"
```

![Debian/Ubuntu&#x5220;&#x9664;&#x6B8B;&#x4F59;&#x914D;&#x7F6E;&#x6587;&#x4EF6;](http://www.linuxdashen.com/wp-content/uploads/2015/12/Selection_274.png)

其中第一栏的**rc**表示软件包已经删除（**R**emove），但配置文件（**C**onfig-file）还在. 现在提取这些软件包的名称．

```text
dpkg --list | grep "^rc" | cut -d " " -f 3
```

![Debian/Ubuntu&#x5220;&#x9664;&#x6B8B;&#x4F59;&#x914D;&#x7F6E;&#x6587;&#x4EF6;](http://www.linuxdashen.com/wp-content/uploads/2015/12/doodle@www-_275.png)

删除这些软件包

```text
dpkg --list | grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
```

```text
(Reading database ... 64538 files and directories currently installed.)
Removing libapt-inst1.4:amd64 (0.8.16~exp12ubuntu10.11) ...
Purging configuration files for libapt-inst1.4:amd64 (0.8.16~exp12ubuntu10.11) ...
Removing libbind9-80 (1:9.8.1.dfsg.P1-4ubuntu0.6) ...
Purging configuration files for libbind9-80 (1:9.8.1.dfsg.P1-4ubuntu0.6) ...
```

如果你只想删除某个软件包的配置文件，那么可以使用下面的命令

```text
sudo dpkg --purge <package-name>
```

### 3. 删除没有用的deb软件安装包 <a id="circle-heading-1"></a>

通常我们用sudo apt-get install 命令安装软件包后，apt-get下载的deb安装包会保留在系统上．所以如果你经常安装软件，那么这些deb安装包会占据大量的空间．这些安装包在**/var/cache/apt/archives**目录下。在软件安装完成后，这些deb安装包就没什么用了。对于硬盘容量有限的服务器来说**apt-get clean**命令可以腾出很多空间。你可以输入下面的命令来查看/var/chace/apt/archives目录下deb安装包的总大小

```text
du -sh /var/cache/apt/archives
```

要删除这些deb包，只需要运行下面两个命令就行了．

```text
sudo apt-get clean
sudo apt-get autoclean
```

### 4. 删除孤儿软件包 <a id="circle-heading-2"></a>

有时候，你用apt-get安装一个软件包时会自动安装其他的依赖．当你删除掉这个软件包时，这些依赖也就没有用处了．这些没有用的依赖包叫做孤儿软件包，可以用下面的命令删除

```text
sudo apt-get autoremove
```

不过apt-get autoremove只会删除经apt-get自动安装的依赖包，而你自己手动安装的依赖包则不会被删除，这时我们可以用deborphan来彻底删除．

```text
sudo apt-get install deborphan
```

列出孤儿软件包

```text
deborphan
```

![Linux&#x6E05;&#x7406;&#x786C;&#x76D8;&#x7A7A;&#x95F4;](http://www.linuxdashen.com/wp-content/uploads/2015/12/matrix@vivid-_276.png)

将它们删除

```text
deborphan | xargs sudo apt-get purge -y
```

###  <a id="circle-heading-3"></a>

### 5. 删除过时的软件包 <a id="circle-heading-4"></a>

所谓过时（obsolete）的软件包是指**/etc/apt/sources.list**源文件中没有任何一个软件源提供这个软件的deb安装包．也就是说这个软件包在软件源里找不到了，不被支持了．这可能是因为下面几个原因：

* 上游开发者不维护这个软件，又没有人来接管这个软件的开发．所以Debian/Ubuntu的软件包维护人员决定将这个软件从软件源中删除．
* 这个软件成了孤儿，同时用户很少．所以它就从软件源里消失了．
* 这个软件有了一个新的名字，维护人员给它起了一个新的名字并保留旧软件包．

因为这些过时的软件不会有安全更新了，而且搞不好会在软件升级过程中引来麻烦，所以我们需要将它们删除．首先找出哪些软件包是过时的

```text
sudo aptitude search ?obsolete
```

我的输出结果

```text
i linux-image-3.2.0-29-generic - Linux kernel image for version 3.2.0 on 64
```

将它删除

```text
sudo apt-get purge linux-image-3.2.0-29-generic
```

你也可以使用下面的命令将所有过时的软件包一下清除

```text
sudo  aptitude purge ~o
```

不过需要注意的是，有些软件包虽然在软件源里找不到，但它并不是过时的软件包．比如你自己下载安装的ubuntu-tweak．ubuntu-tweak需要你从官网下载deb安装包，但不提供软件源．用上面这条命令会将这类软件包也删除．所以我建议使用apt-get purge，自己选择需要删除的软件包．

### 6. 清理日志文件 <a id="circle-heading-5"></a>

日志文件会变得越来越大，我们可以用ncdu工具来查看大日志文件．

```text
sudo apt-get install ncdu

sudo ncdu /var/log
```

![Linux&#x6E05;&#x7406;&#x786C;&#x76D8;&#x7A7A;&#x95F4;](http://www.linuxdashen.com/wp-content/uploads/2015/12/doodle@www-_277.png)

从上图可以发现，shadowsocks.log占用了24.5MiB的硬盘空间，我们可以用下面的命令来清空这个日志文件的内容．

```text
sudo dd if=/dev/null of=/var/log/shadowsocks.log
```

