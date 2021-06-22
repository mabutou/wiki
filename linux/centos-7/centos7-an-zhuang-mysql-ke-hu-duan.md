# centos7 安装 MySQL 客户端

**仅安装 MySQL 客户端**

```text
# 添加rpm源
[root@k8s-master ~]# rpm -ivh https://repo.mysql.com//mysql57-community-release-el7-11.noarch.rpm
[root@test1 ~]#
# 通过yum搜索
[root@test1 ~]# yum search mysql-community
[root@test1 ~]#
# 安装x64位的 mysql客户端
[root@test1 ~]# yum install mysql-community-client.x86_64
```

