# 批量删除failed pod

```text
export ns=kube-system
kubectl get pods --field-selector=status.phase=Failed -n $ns | cut -d' ' -f 1 | xargs kubectl delete pod -n $ns
```

```text
kubectl get pods --field-selector=status.phase=Failed -n kube-system | cut -d' ' -f 1 | xargs kubectl delete pod -n kube-system
kubectl get pods --field-selector=status.phase=Failed -n cattle-system | cut -d' ' -f 1 | xargs kubectl delete pod -n cattle-system
```

