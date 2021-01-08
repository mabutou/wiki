# ssh 端口转发脚本

```text
#!/bin/bash
if [ $1 == "start" ]; then
    echo "port forwarding starting..."
    ssh -CfNg -L 5001:localhost:5001 nas
    ssh -CfNg -L 8096:localhost:8096 nas
    ssh -CfNg -L 9091:localhost:9091 nas
elif [ $1 == "stop" ]; then
    echo "stop port forwards"
    ssh_pids=$(ps -ef | grep -E 'ssh\ -CfNg\ -L|ssh-agent\ -l' | awk '{print $2}')
    echo ${ssh_pids}
    kill ${ssh_pids}
    echo "port forward had stopped"
else
    echo "port forwarding starting..."
    ssh -CfNg -L $1:localhost:$3 $4
fi
ps -ef | grep ssh | grep -v grep
```

