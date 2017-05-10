#Git

##git 创建分支

  1. 初始化当前目录

  ```
  git init
  ```

##clone

1. git clone 指定分支

  >git releases 分支到mobile目录下

  ```
  git clone  -b releases xx.git mobile
  ```


##branch

2. git 创建分支

  > 创建普通分支

  ```sh
  git checkout -b dev
  ```
  >等同于

  ```sh
  git branch dev
  git checkout dev
  ```

  > git 创建空白分支

  ```sh
  git checkout --orphan dev
  git rm -rf . //删除一些不必要的问题(直接使用rm -rf 会物理的删除文件)
  ```

1. git 查看分支

  >查看远程分支

  ```sh
  git branch -r
  ```

  >查看所有分支

  ```sh
  git branch -a
  ```

1. git 删除分支

  ```
  git branch -d <branchname>
  ```


##push

1. git 强制push

  ```sh
  git push --force origin master
  ```
##remote

1. 查看当前远程库

  ```
  git remote -v
  ```

2. 添加远程库

  ```
  git add remote add pd xx.git
  ```

##subtree(主要作用于多个版本库同时依赖同一个版本库时常用)

  1. 添加子库

  ```
  git subtree add --prefix=dist build m  --squash

  // --prefix 新建的存放目录
  // build    子库
  // m        子库分支
  // --squash 合并所有子库秀至一个提交
  ```
  2. 提交更改至子库

  ```
  git subtree push --prefix=dist build m
  ```

  3. 从子库更新内容

  ```
  git subtree pull --prefix=dist build m  --squash
  ```

##pull 与fetch
```
git pull = git fetch + git merge
```
##git回滚

>git 回滚至指定记录(1b174189f9077b53ce0add9989fb4e8206713c6f)

```
git checkout 1b174189f9077b53ce0add9989fb4e8206713c6f
```

>add但未commit(取消暂存)

  1.取消所有暂存

  ```
  git reset --hard HEAD
  ```

  2.取消暂存index.html

  ```
  git reset --hard index.html
  ```


>未add(撤销更改)

```
git checkout -- file
```
>修改已提交(撤销上次提交)

```
git revert HEAD
```
>修改提交注释

```
git commit --amend
```
>删除一些未git add文件或目录

```
git clean -fd
```
##git 忽略文件
>未添加到版本管理的(git add )

1.	新建.gitignore文件
2.	在.gitignore添加要忽略的文件

```
.DS_Store
node_modules/
dist/
npm-debug.log
```
>已经添加到版本库的(但本地不想保存源文件)

```
git rm
```
>已经添加到版本库的（本地想保存源文件）


```
git rm --cached
```
>已经添加到版本库的（本地想保存源文件）

##忽略文件的更改
```
git update-index --assume-unchanged
```
恢复对文件的更改
```
git update-index --no-assume-unchanged
```

##git 日志

>对比两个本地仓库(dev)与远程仓库(origin/dev)的具体差别

git diff dev..origin/dev
git log -p dev..origin/dev

##git 比较对比

>对比当前的工作目录里的，没有 staged(添加到索引中，没有使用`git add`命令的)
```
git diff
```

>对比当前工作目录与上次提交钱的所有差别

```
git diff HEAD
```
>对比已经暂存起来的文件和上次提交的版本之间的差异(使用`git add`命令的)

```
git diff –cached
```

##git 设置输出颜色

```
git config --global color.status auto
git config --global color.diff auto
git config --global color.branch auto
git config --global color.interactive auto
```
##git 自动转换换行符(push自动CRLF转LF，pull时LF转CRLF)

```
git config --global core.autocrlf true
```
##git 忽略权限配置

```
git config --global core.filemode false
```

##git 换行符检测

- flase `不做任何检查`
- warn `提交时检查并警告`
- true `提交时检查，如果发现混用则拒绝提交`

```
git config --global coresafecrlf
```
