# mac 执行sed -i指令时，提示extra characters at the end of command

执行命令如下时，总报extra characters at the end of command错误：

```
sed -i "s/192.168.0.2/192.168.0.3/g" *.rptdesign  
```

&#x20;

原因：

unix与linux在执行sed指令时有些区别，-i指令后面多加一个""空白符即可，如

```
sed -i "" "s/192.168.0.2/192.168.0.3/g" *.rptdesign  
```
