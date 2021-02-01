# 查看大文件

1 查看文件的前多少行

head -10000 /var/lib/mysql/slowquery.log &gt; temp.log

2 查看文件的后多少行

tail -10000 /var/lib/mysql/slowquery.log &gt; temp.log

3 查看文件的几行到几行

sed -n '10,10000p' /var/lib/mysql/slowquery.log &gt; temp.log

