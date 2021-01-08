# new user && group

```text
sudo useradd -r -m -s /bin/bash mabutou
```

其中参数的意义如下：

```text
-r：建立系统账号
-m：自动建立用户的登入目录
-s：指定用户登入后所使用的shell
输入ls /home/，可以看到用户目录被成功创建了：
```

**注意：千万不要使用普通的编辑命令来修改`sudoers`文件。由于该文件的特殊性，错误的语法将导致你无法在系统里获取提升权限。正确的修改方式是使用`visudo`命令。**

`visudo`命令将打开一个文字编辑器，但是在保存文件的时候，将会验证`sudoers`文件的语法。这将防止你配置错误导致`sudo`命令受阻。

```text
sudo passwd mabutou
```

将该用户添加至`sudo`分组中。

在`Ubuntu`系统下，我们可以输入命令：

```text
sudo usermod -aG sudo username
```

其中`username`我们用相应的用户名替换。

在`CentOS`下，`wheel`组代替了`sudo`组，所以我们将用户添加至`wheel`组中：

```text
sudo usermod -aG wheel username
```

**注意：在CentOS下，请留意`wheel`组是否被注释，如果被注释，请将注释去掉：**

```text
%wheel ALL=(ALL) ALL
```

完成后，我们保存退出。现在返回到我们想要给予权限的用户

```text
su - mabutou
```

测试一下`sudo`命令：

```text
sudo visudo
```

输入用户密码后，如果编辑器打开，那么我们就已经成功地给予了用户`sudo`权限了。

## **删除用户**

1. 执行`userdel`：`sudo userdel` mabutou
2. 删除用户目录：`sudo rm -rf /home/mabutou`

