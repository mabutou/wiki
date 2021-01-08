# Force delete POD

问题：kubelet delete pod之后总处于Terminating，无法移除

解决：加参数 –force –grace-period=0，grace-period表示过渡存活期，默认30s，在删除POD之前允许POD慢慢终止其上的容器进程，从而优雅退出，0表示立即终止POD

`kubectl delete po -n –force –grace-period=0`

