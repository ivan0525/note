git fetch和git pull都可以将远端仓库更新至本地，但是它们有什么区别？

**FETCH_HEAD：** 是一个版本链接，记录在本地的一个文件中，指向着目前已经从远程仓库取下来的分支的末端版本。

**commit-id：** 在每次本地工作完成后，都会做一个`git commit` 操作来保存当前工作到本地的repo， 此时会产生一个commit-id，这是一个能唯一标识一个版本的序列号。 在使用git push后，这个序列号还会同步到远程仓库。

**git fetch：** 这将更新`git remote` 中所有的远程仓库所包含分支的最新commit-id, 将其记录到.git/FETCH_HEAD文件中
git fetch更新远程仓库的方式如下：


```bash
git fetch origin master/dev
// 本地新建一个dev分支，并将远程origin仓库的master分支代码下载到本地

git diff dev
// 比较本地代码和刚刚从远程下载下来的代码的区别

git merge dev
// 合并dev分支到本地的master分支

git branch -d dev
// 如果不想要dev分支了，可以用该命令将它删掉
```
