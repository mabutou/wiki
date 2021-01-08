# k8s proxy

* 三台 centos7 测试服务器上用 kubeadm 部署k8s测试环境。
* 过程中有些注意事项，提前避开能节省很多时间。
* 安装指定 docker 版本
  * kubeadm 对docker版本的支持有限。
  * 直接装最新版的会在后面步骤里报错，还得重装一次。
* 某些教程里使用的是旧版kubeadm ，对应的网络插件 weav 版本也是旧版的。
  * 我是直接装的最新版kubeadm，发现装weav时遇到版本问题。用下面命令装的
    * kubectl apply -f “[https://cloud.weave.works/k8s/net?k8s-version=$](https://cloud.weave.works/k8s/net?k8s-version=$)\(kubectl version \| base64 \| tr -d ‘’\)”
* 正确设置代理（重要）。

  * 本来kubeadm部署k8s很简单，但国内无法正常访问 [gcr.io](http://gcr.io/) 。很多人被拉取 [gcr.io](http://k8s.gcr.io/v2/) 镜像时的网络问题卡住。
  * linux 下在终端用 setproxy 或 sethttp 命令设置的代理对 docker pull 无效。需要额外设置。

  **操作步骤**

  创建目录

  `sudo mkdir -p /etc/systemd/system/docker.service.d`

  新建文件，走http代理

  `vim /etc/systemd/system/docker.service.d/http-proxy.conf`

  内容（ip和端口号根据客户端设置修改）

  ```text
  [Service]
   Environment="HTTP_PROXY=http://127.0.0.1:8001/"
  ```

```text
[Service]
Environment="HTTP_PROXY=http://127.0.0.1:8001/" "NO_PROXY=localhost,192.168.10.193,192.168.10.23,127.0.0.1,docker-registry.example.com,.corp,192.168.10.*,*.sunrise.lan,registry.lisong.pub,*.lisong.pub"
```

```text
刷新更改：

sudo systemctl daemon-reload

重新启动Docker：

sudo systemctl restart docker

验证配置是否已加载：

systemctl show --property=Environment docker

如果生效会显示对应设置参数
Environment=HTTP_PROXY=http://proxy.example.com:80/

之后的步骤里就可以 pull [gcr.io](<http://gcr.io>) 上的镜像了

详细配置参考官网文档：

<https://docs.docker.com/config/daemon/systemd/>
```

* 过程中有些注意事项，提前避开能节省很多时间。

注：如果配置的是局域网内其他机器上运行的代理客户端，需要在对应客户端开启局域网共享功能（某些 GUI 客户端没有这个选项，可以手动在配置文件里将本地监听从 127.0.0.1 改成 0.0.0.0 ）

