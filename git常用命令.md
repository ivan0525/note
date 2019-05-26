- 新建本地分支并切换到当前新建的分支

```shell
git checkout -b [分支名]
```

- 查看提交记录的电线图

```shell
git log --graph 
```

- 查看远端分支

```shell
git branch -r 
```

- 删除远端分支

```shell
git branch origin --delete [远端分支名] 
```

- 查看所有分支（本地和远程）

git branch -a

 git pull origin dev 本地分支与远程分支相关联
git pull --rebase
git rebase 分支

git reset --hard e377f60e28c8b84158 回到某一版本
git reset --hard HEAD^  强制回退到上一个版本
git checkout . # 

解决rabase后得冲突 git add . git rebase --continue

git rebase --skip 逃过
git rebase --abort 回到之前
git cherry-pick 'id’copy 某个提交
git history 查看历史
git fetch

git push origin : dev_zjq  删除远程分支
git branch -D 分支 删除本地分支

git add .
git commit -m '.........'
git pull --rebase #获取最新代码 (如果有冲突，继续一下步骤，如果无 直接git push)
git status （查看冲突的文件）
git add （修改冲突文件后，添加文件到缓存区）
git rebase --continue
git commit --amend 修改备注
git push

git branch 分支名 创建分支
创建+切换分支：git checkout -b <name>
git push --set-upstream origin test1
git checkout -b dev_zjq
git push --set-upstream origin dev_zjq 