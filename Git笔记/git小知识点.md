## 图像化分支
在bash中输入`gitk`就可以进入分支的图形化界面

## 解决`gitk`中文乱码的方法
```
  git config --global gui.encoding utf-8
```

## 新建分支
```
  git branch [分支名]
```

## 新建分支并切换到该分支
```
  git checkout -b [分支名]
```

## 删除分支
```
  git branch -d [分支名]
```

## 当合并代码时出错或冲突，可以取消本次合并
```
  git merge --abort
```

## 查看提交的历史、各个分支的指向
```
  git log --oneline --decorate --graph --all
```
