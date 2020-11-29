---
title: Git 使用手则
categories:
  - 工具
tags:
  - Git
abbrlink: '8161'
date: 2020-11-28 23:48:50
top: 1
summary: 一.知识点
	     二.异常解决
---



## 一.知识点总结

1. ### 提交文件

   ### `$ git add readme.txt`  

   ### `$ git commit -m "wrote a readme file"`

2. ### 查看仓库状态

   ### `$ git status`

3. ### 查看修改内容

   ### `$ git diff readme.txt `

   > ### git diff比较的是工作目录中当前文件和暂存区域快照之间的差异， 也就是修改之后还没有暂存起来的变化内容。若要查看已暂存的将要添加到下次提交里的内容，可以用 git diff --cached 命令。
   >
   > ### 请注意，git diff 本身只显示尚未暂存的改动，而不是自上次提交以来所做的所有改动。 所以有时候你一下子暂存了所有更新过的文件后，运行 git diff 后却什么也没有，就是这个原因。

   ### `git diff HEAD -- readme.txt` 查看工作区和版本库里面最新版本的区别

4. ### 显示从最近到最远的提交日志

   ### `$ git log`  （显示全面）

   ### `$ git log --pretty=oneline `  （只显示版本号）

   ### `$ git reflog`  （查看命令历史）

5. ### 回退版本

   ### `$ git reset --hard HEAD^` （回退了一个版本）

   ### `$ git reset --hard HEAD~100`  （回退了一百个版本）

   ### `$ git reset --hard 1094a`  （指定版本回退）

6. ### 丢弃工作区的修改

   ### `$ git checkout -- readme.txt`

   ### `$ git restore readme.txt`

   > ### 一种是`readme.txt`自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
   >
   > ### 一种是`readme.txt`已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

   ### 丢弃暂存区的修改

   ### `$ git reset HEAD readme.txt`

7. ### 删除版本库文件

   ### `$ git rm test.txt`

   > ### 同时本机文件也被删除

8. ### 提交远程

   ### `$ git push origin <分支名>`

   > ### 第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。

9. ### 抓取远程

   #### `$ git pull`

10. ### 分支使用

   1. #### 查看分支：`git branch`

   2. #### 创建分支：`git branch <name>` 

   3. #### 切换分支：`git checkout <name> `或者`git switch <name> `

   4. #### 创建+切换分支：`git checkout -b <name>`或者`git switch -c  <name>`

   5. #### 合并某分支到当前分支：`git merge <name> ` （快速合并）

      #### 禁用快速合并，并创建一个commit

      ####  `$ git merge --no-ff -m "注释" dev`

   6. #### 删除分支：`git branch -d <name> `

      #### 强制删除：`git branch -D <name> `

11. ### 查看分支合并情况

    > #### 详细情况 `git log --graph`
    >
    > #### 版本号全显示 `git log --graph --pretty=oneline`
    >
    > #### 版本号简略显示 `git log --graph --pretty=oneline --abbrev-commit`

12. ### Bug分支

    > #### 工作现场“储藏” `$ git stash`
    >
    > #### 查看工作储藏 `$ git stash list`
    >
    > #### 恢复后，stash内容并不删除 `$ git stash apply`
    >
    > #### 恢复的同时把stash内容删除 `$ git stash pop`
    >
    > #### 特定恢复 `$ git stash apply <name>` 
    >
    > #### 复制一个特定的提交到当前分支 `$ git cherry-pick <版本号>`

13. ### 多人协作

    > #### 查看远程库的信息  `$ git remote`
    >
    > #### 查看远程库的详细信息  `$ git remote`
    >
    > #### 在本地创建和远程分支对应的分支
    >
    > ####  `git checkout -b branch-name origin/branch-name`
    >
    > #### 建立本地分支和远程分支的关联
    >
    > #### `git branch --set-upstream branch-name origin/branch-name`

14. ### Rebase

    > #### 历史记录变为直线型 `$ git rebase`  
    >
    > #### 停止转变 `$ git rebase --quit`

15. ### 标签管理

    > #### 创建标签 `$ git tag v1.0`
    >
    > #### 创建具体标签 `$ git tag v0.9 <版本号>`
    >
    > #### 查看标签 `$ git tag`
    >
    > #### 查看标签信息 `git show <tagname>`
    >
    > #### 创建带有说明的标签，用`-a`指定标签名，`-m`指定说明文字：
    >
    > #### `$ git tag -a v0.1 -m "version 0.1 released" 1094adb`
    >
    > #### 删除标签 `$ git tag -d v0.1`
    >
    > #### 推送标签 `git push origin <tagname>`
    >
    > #### 一次性推送全部尚未推送到远程的本地标签 `$ git push origin --tags`
    >
    > #### 删除远程标签，先删除本地，再删除远端
    >
    > #### `$ git push origin :refs/tags/v0.9`

## 二.异常解决

1. ### 出现 END 不要慌张 ，按 Q 键 即可

2. ### Github查看仓库地址，点击下载按钮的拓展即可

3. ### 删除文件 

   ### `$ rm test.txt`

   ### 新建文件夹

   ### `$ mkdir <files>`

4. ### 查看文件

   ### `$ cat test.txt`

   ### 查看文件夹下文件列表

   ### `$ ls`

   ### 创建文件

   ### `$ touch <文件名>`

5. ### 定位文件

   1. #### 先定位磁盘 `cd C:` (有：)

   2. #### 在定位文件夹 `cd Echochao` (无：)

## 三.别名备份

### 	定义别名`$ git config --global alias.st status`

### 	`撤销别名`

1. ### `git status`  ---> `git st`

2. ### `git commit` ---> `git ci`

3. ### `git chekout` ---> `git co`

4. ### `git branch`  ---> `git br`

5. ### `git log --graph --pretty=oneline --abbrev-commit`

   ### ---> `git lg`

6. 

