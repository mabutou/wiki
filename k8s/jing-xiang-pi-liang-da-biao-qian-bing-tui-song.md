# 镜像批量打标签并推送

```text
#!/bin/bash
kubectl get pods -n prod -o jsonpath="{..image}" |tr -s '[[:space:]]' '\n' |sort |uniq -c > image0.txt
awk '{print $2}' image0.txt > image1.txt
for i in $(cat image1.txt)
do
docker pull ${i}
docker tag ${i} ${i}-stable
docker push ${i}-stable
rm -rf image*.txt
done
```



