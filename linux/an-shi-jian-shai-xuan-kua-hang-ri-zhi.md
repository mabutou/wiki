# 按时间筛选跨行日志

```text
awk 'BEGIN{FS="\n";RS="2020-12-16";ORS=""}{for(x=1;x<=NF;x++){print $x"\t"} print "\n"}' error.log | awk '{if ( $1 >= "07:55:00" && $1 <= "08:05:00") print $0 }' > error-new.log
```





