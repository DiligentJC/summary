# Git常用命令整理

## 配置Git

```sh
# 配置全局用户
$ git config --global user.name '[name]'
$ git config --global user.email '[email]'
# 生成ssh密钥，添加公钥到仓库
$ ssh-keygen -t rsa -C '[email]'
$ cat ~/.ssh/id_rsa.pub
# 查看Git版本
$ git --version
# 查看用户配置
$ cat ~/.gitconfig
# 查看当前项目的Git配置
$ cat .git/config
```

## 查看Git仓库状态

```sh
# 查看提交历史
$ git log -[num]                 # 最近[num]条提交
          --oneline              # 日志记录一行显示
          --grep '[keyword]'     # 关键字查找
          --graph                # 图形化显示
          --stat                 # 列出文件更改列表
# 查看工作区和暂存区状态
$ git status
# 查看本地分支
$ git branch
# 查看远程本地所有分支
$ git branch -a
```
## 常用命令

```sh
# 克隆到本地
$ git clone [仓库地址]
# 新建本地仓库
$ git init
# 关联远程仓库
$ git remote add origin [仓库地址]
# 添加文件到暂存区
$ git add .
# 提交到仓库
$ git commit
# 追加提交
$ git commit --amend
# 推送到远程仓库
$ git push origin [本地分支名]:[远程分支名]
# 关联远程分支提交
$ git push -u origin [远程分支名]
# 拉取远程分支 pull = fetch + merge
$ git pull
# 拉取远程对应分支
$ git pull origin [远程分支名]
# 删除本地分支
$ git branch -D [本地分支名]
# 查看Git操作历史
$ git reflog
# 恢复暂存区到工作区
$ git restore --staged [文件名]
# 新建并切换分支
$ git checkout -b [本地分支名]
$ git switch -c [本地分支名]
# 未提交修改保存到堆栈中
$ git stash -u
# 查看储存记录
$ git stash list
# 恢复修改，不删除stash记录
$ git stash apply "stash@{index}"
# 恢复修改，删除stash记录
$ git stash pop "stash@{index}"
# 合并多个commit
$ git rebase -i
# 将commit修改应用到当前分支
$ git cherry-pick [commit]
```

## 回退命令

```sh
# 回退版本，重置工作区、暂存区
$	git reset --hard [commit]
# 回退版本，修改回退到工作区
$	git reset --mixed [commit]
# 回退版本，修改回退到暂存区
$	git reset --soft [commit]
# 舍弃工作区修改
$ git restore [file]
# 暂存区撤出到工作区
$ git restore --staged [file]
# 删除没有被版本控制的文件和目录
$ git clean -df
```

## Push到Gerrit提示MergeConflict

> 解决方法：
> 1. **switch**新建temp分支
> 2. **reset **回退版本
> 3. **pull **拉取最新
> 4. **cherry-pick**要合并的提交
> 5. 处理冲突
> 6. **add **到暂存区
> 7. **git cherry-pick --continue**
> 8. **push**到远端

**后续有用到其他命令再补充......**

