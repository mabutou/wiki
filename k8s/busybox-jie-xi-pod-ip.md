# busybox 解析 pod ip

```text
$ kubectl run bb3 --image=busybox:1.28 --command -- sleep 3600
deployment.apps/bb3 created
$ POD_NAME=$(kubectl get pods -l run=bb3 -o jsonpath="{.items[0].metadata.name}")
$ kubectl exec -ti $POD_NAME -- nslookup kubernetes
Server:    10.32.0.10
Address 1: 10.32.0.10 kube-dns.kube-system.svc.cluster.local

Name:      kubernetes
Address 1: 10.32.0.1 kubernetes.default.svc.cluster.local
```

