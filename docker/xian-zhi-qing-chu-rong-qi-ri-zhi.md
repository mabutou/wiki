# 限制&&清除容器日志

设置Docker容器日志文件大小限制

```text
1.新建/etc/docker/daemon.json，若有就不用新建了。添加log-dirver和log-opts参数，样例如下：

# vim /etc/docker/daemon.json

{
  "registry-mirrors": [
    "<https://sucejt9z.mirror.aliyuncs.com>"
  ],
  "log-driver":"json-file",
  "log-opts": {"max-size":"200m", "max-file":"3"}
}
{
  "log-driver":"json-file",
  "log-opts": {"max-size":"200m", "max-file":"3"}
}

max-size=200m，意味着一个容器日志大小上限是200M， 
max-file=3，意味着一个容器有三个日志，分别是id+.json、id+1.json、id+2.json。



2.然后重启docker的守护线程

命令如下：

sudo systemctl daemon-reload
sudo systemctl restart docker


【需要注意的是：设置的日志大小规则，只对新建的容器有效】
```

Container Log 預設路徑如下：

\*/var/lib/docker/containers/**&lt;container-id&gt;**/\*\*&lt;container-id&gt;\*_json.log_

可以利用下列指令進行清除。

```text
cat /dev/null > <container-id>-json.log
```

**設定 Log 文件容量上限**

每次都手動清除是件很蠢的事，可以將設定檔放置於 etc/docker/daemon.json，若無此文件，則需額外新增，設定值可參考下列內容：

```text
{
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "50m",
    "max-file": "3"
  }
}
```

接著利用下列指令重新載入，之後建立**新的 Container** 就會套用了。

```text
systemctl daemon-reload

systemctl restart docker
```

**清理 Log Script**

如果想使用排程進行 Log 的清理，可將下列 Script 存成 sh 檔後執行。

```text
path=/var/lib/docker/containers/
echo ""
echo "========== Clean Docker Containers Log =========="
echo "Path: "$path
cd $path
for file in $(ls)
do
    if [ -d $file ];then
        echo $file"-json.log"
        cat /dev/null > $file/$file-json.log
      else
        echo 0
    fi
done
echo "========== Clean Docker Containers Log =========="
echo ""
```

