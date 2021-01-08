# 虚拟机设置静态ip, Vmware 虚拟机配置全攻略 - 少数派

原文：[https://sspai.com/post/53878](https://sspai.com/post/53878)

虚拟机还能设置静态ip？Vmware 虚拟机配置全攻略

> 前言：  
> 虚拟机应该是我们大多数人都会接触到的，尽管目前虚拟机的配置都十分简单便捷，几乎可以说是上手即用。但是对于一些较不常用的操作，可能配置起来还是会繁琐一些，比如`解锁 macOS 的安装限制` ，设置 `静态 ip` 等。本文将从头开始示范如何进行 `静态 ip`的配置。
>
> 本文作为我在 `少数派` 发布的第一篇文章，可能会有一些地方做得不是很好，欢迎大家指正。

## 1. 简述 <a id="ss-3-1554652863529"></a>

用于为基于 Vmware 的虚拟机设置静态的 ip 地址，适用于有多台虚拟机之间互联的需求

## 2. 环境需求 <a id="ss-3-1554652863529"></a>

VMware WorkStation Pro 15 （仅测试`15.0.4` 版本，对早期版本可能略有不同）  
Ubuntu 18 （仅支持 Ubuntu`18` 版本，早期版本设置方式可能有所不同，本例使用的是 `Ubuntu Server 18.04.2 LTS` ）

* 本例使用的配置如下，后续不赘述：

| 类别 | 地址 |
| :--- | :--- |
| 网关（gateway） | 192.168.2.1 |
| 子网掩码（subnet mask） | 255.255.255.0 |
| VMware 虚拟网卡 ip | 192.168.2.100 |
| 虚拟机 ip | 192.168.2.10 |
| 网卡 | ens32 |

## 3. 步骤说明 <a id="ss-3-1554652863529"></a>

### 1. Vmware 配置 <a id="ss-4-1554652863529"></a>

1. 打开 `虚拟网络编辑器`，如图 ​ ![&#x8BF7;&#x8F93;&#x5165;&#x56FE;&#x7247;&#x6807;&#x9898;](https://cdn.sspai.com/2019/04/04/755457af6f262b901cbd8e835870bd43.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)
2. 选择 `VMnet8 NAT 模式`，其他配置如图 ![&#x8BF7;&#x8F93;&#x5165;&#x56FE;&#x7247;&#x6807;&#x9898;](https://cdn.sspai.com/2019/04/04/962a8b6f9a7e9f73ce21c69baec58095.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)
3. 设置 `子网网络号` 及 `子网掩码`，如图 ![&#x8BF7;&#x8F93;&#x5165;&#x56FE;&#x7247;&#x6807;&#x9898;](https://cdn.sspai.com/2019/04/04/d11a16198f2ea24993e3bbb0521b033a.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)
   * 这里需要使用私有地址，以防止不可预期错误。
   * A类私有地址为：10.0.0.0 - 10.255.255.255， 子网掩码：255.0.0.0
   * B类私有地址为：172.16.0.0 - 172.31.255.255， 子网掩码：255.255.0.0
   * C类私有地址为：192.168.0.0 - 192.168.255.255，子网掩码：255.255.255.0
4. 选择 `NAT 设置`，如图  
   ![&#x8BF7;&#x8F93;&#x5165;&#x56FE;&#x7247;&#x6807;&#x9898;](https://cdn.sspai.com/2019/04/04/d04ed59f3cc0e0a1938841826dca1b72.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

   > `NAT`（Network Address Translation，网络地址转换），用于将 `私有网络地址` 转换为 `公有网络地址`，是为了应对 `Ipv4 地址匮乏` 而提出的临时解决方案，与 `VLSM`（Variable Length Subnet Mask，可变长子网掩码）一同作为 ipv4 到 ipv6 的过渡期方案。

5. 配置 `网关地址`，其他不需要做改变，如图 ![&#x8BF7;&#x8F93;&#x5165;&#x56FE;&#x7247;&#x6807;&#x9898;](https://cdn.sspai.com/2019/04/04/9c1999b798edb17ab8568a32cea6505d.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)
   * 这里的网关主机位可以随意，不知道什么是主机位的，可以直接参考我的配置
6. 设置 `DHCP 服务器`，如图 ![&#x8BF7;&#x8F93;&#x5165;&#x56FE;&#x7247;&#x6807;&#x9898;](https://cdn.sspai.com/2019/04/04/710f50057b83346ea2028e59cad4e0eb.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

![&#x8BF7;&#x8F93;&#x5165;&#x56FE;&#x7247;&#x6807;&#x9898;](https://cdn.sspai.com/2019/04/04/8d6ae7dd6c9e22381b48046c227db9bf.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

* 这里的 `启始 ip` 跟 `结束 ip` 可以随意，注意符合上文所设置的子网网络地址即可。  
  不了解的可以参照我的配置

  > 详细了解见 &lt;计算机网络-谢希仁著&gt;，目前最新版本应为第七版

### 2. 本地网络设置 <a id="ss-4-1554652863530"></a>

1. 按 `win` + `s`，输入 `网络共享和中心` ，`enter`，在右侧找到 `更改适配器选项`，如图 ![&#x8BF7;&#x8F93;&#x5165;&#x56FE;&#x7247;&#x6807;&#x9898;](https://cdn.sspai.com/2019/04/04/0d56974fdcdc8e012b93c3f5ae4e641a.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)
2. 找到这一项并右键，选择属性，如图 ![&#x8BF7;&#x8F93;&#x5165;&#x56FE;&#x7247;&#x6807;&#x9898;](https://cdn.sspai.com/2019/04/04/3fed2b0399aea646b9b2e37ef292409a.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)
3. 如图所示配置，`ip 地址`为虚拟网卡地址，主机位可以随意。`网关` 和 `子网掩码` 按照上文的设置配置好即可 ![&#x8BF7;&#x8F93;&#x5165;&#x56FE;&#x7247;&#x6807;&#x9898;](https://cdn.sspai.com/2019/04/04/3be18b1a74647e50ca1d8c4ef60820dc.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

### 3. ubuntu 配置： <a id="ss-4-1554652863530"></a>

1. 打开配置文件

   ```text
   $ sudo vim /etc/netplan/50-cloud-init.yaml
   // 本例 ubuntu 中的文件名如此，其他版本可能不同，但均以 *.yaml 结尾
   ```

2. 查看网卡名称 使用 `ip a` 即可看到网卡信息
3. 按 `shift` + `g`， `shift` + `a`，`enter`，并输入以下配置

   ```text
   network:
    version: 2
    renderer: networkd  // 这里没有输错，是 networkd
    ethernets: 
        ens32:    // 这里的ens32 是我的网卡，替换成你自己的
            dhcp4: no
            addresses: [192.168.2.10/24]  // 虚拟机静态 ip，主机位可随意
            gateway4: 192.168.2.1    // 网关
            nameservers: 
                addresses: [192.168.2.1]  // 虚拟机的 DNS，这里填网关 ip
   ```

   * 注意：由于 `Yaml` 文件特性，所有缩进都需要使用空格，并且每项中间的空格都不能省略

4. 按 `esc` 退出插入模式，输入 `:wq` 保存并退出

   > 详细了解见 `Vim` 的基本操作

5. 使用 `sudo netplan apply` 使命令生效
6. 可以使用 `ip a` 查看当前 ip 地址进行验证，或者使用 `ping` 命令进行测试

## 4. 总结 <a id="ss-3-1554652863530"></a>

按照以上配置，理想结果可以达到：

实机 ping 通虚拟机  
![&#x8BF7;&#x8F93;&#x5165;&#x56FE;&#x7247;&#x6807;&#x9898;](https://cdn.sspai.com/2019/04/04/59ea311867ddd4d1408baf31d6c4aec7.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

虚拟机可以 ping 通网关  
![&#x8BF7;&#x8F93;&#x5165;&#x56FE;&#x7247;&#x6807;&#x9898;](https://cdn.sspai.com/2019/04/04/ceaf1d3f67f7b1b455781ef00785b00d.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

虚拟机可以连接互联网  
![&#x8BF7;&#x8F93;&#x5165;&#x56FE;&#x7247;&#x6807;&#x9898;](https://cdn.sspai.com/2019/04/04/7a6a1902fb572bd35779fc2dcf0ac6dd.png?imageView2/2/w/1120/q/40/interlace/1/ignore-error/1)

[![&#x6C90;&#x4E4B;](https://cdn.sspai.com/ui/img-placeholder.png)](https://sspai.com/u/qqn1o3ji/updates)

