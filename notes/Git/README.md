#Git
##git 强制更新忽略冲突
```
git push --force origin master
```
##git pull 与git fetch
git pull = git fetch + git merge
##git回滚
>修改但未提交(恢复全部)

```
git reset --hard HEAD
```

>修改但未提交(单个文件)

```
git checkout -- file
```
>修改已提交(恢复上次提交)

```
git revert HEAD 
```
>修改提交注释

```
git commit --amend
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

忽略文件的更改
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