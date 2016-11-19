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