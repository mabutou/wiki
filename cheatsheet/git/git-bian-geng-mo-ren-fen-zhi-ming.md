# Git 变更默认分支名

[牛さんの部落格](https://wayou.github.io/)

## Git 变更默认分支名

2020 11 月 15 日

## Git 变更默认分支名

目前 GitHub 上创建的仓库默认分支为 `main`，如果想回到以前的 `master` 名称，可通过如下方式完成。

### 分支重命名

`man git-branch` 可得到：

> ```text
>    -m, --move
>       Move/rename a branch and the corresponding reflog.
> ```

通过 `-m` 参数可修改分支名，而不影响 Git 提交历史。

```text
$ git branch -m main master
```

上述命令将 `main` 分支重命名为了 `master`，这样就回到了熟悉的味道。

但这只个变更只是本地的，需要同步到远端。

```text
$ git push -u origin master
```

上述命令将新建的 `master` 分支同步到远端并设置 upstream 到了该分支。

### 切换默认分支

到 GitHub 的仓库设置中选择 master 为默认分支。

### 删除旧分支

删除原来的 main 分支 `git push origin --delete main`

### 其他 clone 的同步

对于已经 clone 的仓库通过如下步骤进行同步：

* `git fetch` 拉取远端分支信息
* `git remote set-head origin -a` 更新本地 upstream
* `git branch -m main master`

### 相关资源

* [How to change git default branch from master](https://levelup.gitconnected.com/how-to-change-git-default-branch-from-master-3933afab08f9)

