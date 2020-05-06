# git

​	1 [初始化](#初始化)

​	2 [将改动的文件添加到版本管理库](#将改动的文件添加到版本管理库)

​	3 [将代码提交到版本管理库](#将代码提交到版本管理库)

​	4[查看当前仓库状态](#查看当前仓库状态)

​	5[查看版本仓库与工作区的不同内容](#查看版本仓库与工作区的不同内容)

​	6[查看git提交历史](#查看git提交历史)

​	7[版本回退](#版本回退)

​	8[查看命令历史](#查看命令历史)

​	9[撤销修改](#撤销修改)

​	10[文件删除](#文件删除)

​	11[查看当前分支](#查看当前分支)

​	12[创建新分支](#创建新分支)

​	13[切换新分支](#切换新分支)

​	14[创建新的分支并且切换过去](#创建新的分支并且切换过去)

​	15[合并分支](#合并分支)

​	16[删除分支](#删除分支)

​	17[本地储存](#本地储存)

​	18[查看远程分支](#查看远程分支)

​	19[从远程拉取](#从远程拉取)

​	20[推送远端](#推送远端)

​	21[将本地分支与远程分支建立联系](#将本地分支与远程分支建立联系)

​	22[创建tag](#创建tag)

​	23[查看所有tag](#查看所有tag)

​	24[查看tag具体信息](#查看tag具体信息)

​	25[删除Tag](#删除Tag)

​	26[推送标签到远程](#推送标签到远程)

### 初始化
> git init

### 将改动的文件添加到版本管理库
  "*" 代表全部文件
>git add <文件名或者 * >

### 将代码提交到版本管理库
> git commit -m "提交信息"

### 查看当前仓库状态
  也就是那些文件修改过，但是看不到修改的内容
> git status

### 查看版本仓库与工作区的不同内容
  文件名可以不加 ，不加为全部
> git diff <文件名>

### 查看git提交历史
> git log
>   如果查看自己的提交历史时嫌信息过多
> git log --pretty=oneline
### 版本回退
  HEAD版,HEAD^代表上一个版本 ，HEAD^^代表上上一个版本，HEAD~10 代表前推十个版本
> git reset --hard HEAD^  //回退到上个版本
> git reset --hard HEAD~10 //回退到前十个版本
> git reset --hard <commit_id> //回退到固定的版本

### 查看命令历史
>git reflog

### 撤销修改
*  checkout 与 -- 与 文件名之间都必须有空格<br />
  语句有两次含义：<br />
  1. 当你没有执行git add 的时候，将工作区的代码撤销到你最后一次commit的版本库里，
  2. 当你执行了 git add 的时候， 将你工作区的代码撤销到你最后一次git add 的暂存区里
> git checkout -- < 文件名称 >
* 将暂存区的修改撤销掉
>git reset HEAD < 文件名称 >

### 文件删除
  此操作是从版本库里删除
> git rm < 文件名称 >

### 查看当前分支
> git branch

### 创建新分支
> git branch < 分支名称 >

### 切换新分支
> git checkout < 分支名称 >

### 创建新的分支并且切换过去
* 仅仅在本地的
> git checkout -b < 分支名称 >
* 在本地创建和远程分支对应的分支
> git checkout -b branch-name origin/branch-name

### 合并分支
  合并指定分支到当前分支
* 普通模式 走的是快速前进 merge之后是直接将 master的指针指向 dev 的提交上的
> git merge < 分支名称 >
* 禁用 快速前进模式 merge之后master 需要重新commit
> git merge --no-ff -m "< message >" < 分支名称 >

### 删除分支
* 删除的是已经合并的分支，没有的合并过的分支会报错
> git branch -d < 分支名称 >
* 删除的是尚未合并的分支
> git branch -D < 分支名称 >

### 本地储存
* 当你正在dev分支上修改代码时，其他有个bug需要及时处理，但是你现在的代码只写了一半，提交以后会影响其他同事的工作，就可以使用本地存储。
> git stash
* 保存当前的状态，包括新建的文件
> git stash -u
* 查看本地存储的列表
> git stash list
* 找回本地存储的文件
> git stash apply < stash@{n} >
* 找回stash状态中某一个文件的修改
> git checkout <stash@{n}> -- <file-path>
* 找回最后一次存储的文件 ，且删除
> git stash pop
* 删除所有的stash
> git stash clear

### 查看远程分支
* 简略信息
> git remote
* 详细信息
> git remote -v

### 从远程拉取
> git pull

### 推送远端
> git push
* 如果是第一次推送，且远端没有这个分支需要执行以下命令
> git push origin < 分支名称 >

### 将本地分支与远程分支建立联系
> git branch --set-upstream branch-name origin/branch-name

### 创建tag
* 不带信息的
> git tag v1.0
* 带有信息的
> git tag -a <tagname> -m "blablabla..."
* 对应某次commit创建tag
> git tag < commit_id >
### 查看所有tag
> git tag
### 查看tag具体信息
> git show < tag_name >
### 删除Tag
* 删除本地tag
> git tag -d < tag_name >
* 删除远程tag ，需要先删除本地tag 然后执行以下命令
> git push origin :refs/tags/< tagname >
### 推送标签到远程
* 单个推送
> git push origin < tag_name >
* 全部推送
> git push origin --tags

