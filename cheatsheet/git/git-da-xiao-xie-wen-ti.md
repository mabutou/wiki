# Git 大小写问题



> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/64923954)

针对以下几个问题，来谈谈在使用 git 时，会遇到的大小写问题：

1. 新克隆的仓库，什么都没做，却存在修改
2. 切换分支，切几次都不成功，但也不报错
3. 推送本地分支到远端时报错：can not be resolved to branch
4. 切换分支后，本地的头节点与远端上的不一致（切换之前已经 fetch all 了）
5. 本地更新分支时报错：can not lock ref xxx: ref xxx is at xxx but expected xxx

### **第一个问题**

1. 当仓库中存在文件名相同，但是大小写不同时，如果你在 windows 上进行克隆操作，克隆完成后，进入仓库去执行 git status 查看是会存在修改的，为此 git-2.20 版本增加了 warning 来提示用户：

> _warning: the following paths have collided \(e.g. case-sensitive paths on a case-sensitive filesystem\) and only one from the same colliding group is in the working tree:_

1. 如果你仓库使用了 LFS，也有可能出现刚克隆完，就存在修改的问题，这个问题，以后再详细阐述吧

**解决方案的话**：没有好的解决方案，建议在 linux 下，将出问题的文件名修改掉，上库

### **第二个问题**

1. 正常切换分支时，git 是会在命令窗口中输出:

> _Switching to branch xxx_

1. 如果当前目录下，存在跟你分支命同名的文件夹或文件时，在 git-2.21 版本之前，执行 git checkout 时，是不会有任何输出的，但可以通过 git checkout xxx -- 来切换分支，通过 git checkout -- xxx 来回退文件
2. git-2.21 为了消除分支名和文件名同名的歧义，增加了日志打印：

> _Fatal: xxx could be both a local file and a tracking branch._  
> _Please use -- \(and optionally --no-guess\) to disambiguate_

1. 分析下命令 git checkout xxx：

> _如果是本地分支名，切换过去_  
> _如果是被跟踪的路径名，重置它_  
> _如果是远端分支名，创建分支，并切换过去_

### 第三个问题

对于分支名带有 / 的会出现上述报错，先简单地来复现一下：

1. 创建一个分支为：A/test-1
2. 再创建一个分支为：a/new-1
3. 将分支 a/new-1 推送到远端，报错：

> Fatal: can not be resolved to branch

问题的原因是：

1. 创建分支时，git 会在本地. git/refs/heads / 文件夹下创建一个以分支名命名的文件，用来跟踪这个分支指向的头节点
2. 上述过程，首先会创建 A 文件夹，然后在它下面创建 test-1 文件
3. 当创建第二个分支时，由于 windows 是不区分大小写的，所以直接在 A 文件夹下创建了 new-1 文件
4. 最后执行 git push origin a/new-1 时就报错了

解决方案就是：

1. 重命名分支名
2. 删除 A/test-1 分支，同时在删除 A 文件夹，再创建 a/new-1 分支

### 第四个问题

这是本地存在分支名和 tag 名同名的情况，所以也一起说一下。

虽然它们名字相同，但是头节点不同，这样可能会导致在开发过程基于它们拉出来的分支会不一样，开发的功能也会有影响。

解决方案：重命名分支或者 tag

### 总结

分支 / Tag 命名很重要，就像命名函数，变量一样，要有意义，能自解释，不产生歧义、冲突。如果开发平台有涉及 windows 的话，还要注意大小写的问题，要尽量避免

