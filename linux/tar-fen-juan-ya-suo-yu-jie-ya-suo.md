# tar分卷压缩与解压缩

## 分卷压缩

举例：将10G大小的log文件2017.log打包压缩并分割成多个100m的文件

## 分卷压缩gz

## 去掉z，压缩为tar

tar zcf - 2017.log \|split -d -b 100m - logs.tar.gz.

## 生成文件： logs.tar.gz.00 logs.tar.gz.01

## 分卷压缩bz2

tar jcf - 2017.log \|split -d -b 100m - logs.tar.bz2.

## 生成文件： logs.tar.bz2.00 logs.tar.bz2.01

最后要提醒但是那两个”-”不要漏了，那是tar的ouput和split的input的参数

## 合并分卷解压缩

## 解压gz分卷

cat logs.tar.gz\* \| tar zx

## 解压bz2分卷

cat logs.tar.gz\* \| tar jx

