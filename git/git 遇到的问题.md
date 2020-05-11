[TOC]

###  git不区分大小写问题

用git提交的时候，git默认是不会区分大小写，也就是当你创建了一个`webScoket`的文件夹，后来你将其改成`webscoket`,这个时候你用git提交的时候，会发现什么也没有提交。因为git默认是不区分大小写的，但是用`nginx`构建代码的时候，他是区分大小写的，这样就会报这不到包的错误,解决方案以下两种.

* 方案一

  配置git 使其对文件名大小写敏感 , 在`.git`的当前目录输入一下命令

  ```js
  git config core.ignorecase false
  ```

> **注意** 这个时候git已经对大小写敏感，所以有的时候他会生成两份文件,



* 方案二

  将以前的文件删除，重新新建一个，然后提交

### git pull的时候遇到“refusing to merge unrelated histories ”

当我们有两个仓库A与B的时候，我本地克隆了A仓库的代码，然后在本地进行了修改，但是提交的时候我想将其提交到B仓库，这个时候我们直接使用`git remote set-url origin https://github.com/wumx/study.git`强行将仓库的url改变，但是当我们执行`git pull`命令的时候就会出现 refusing to merge unrelated histories 这样的错误。这是因为git认为你的本地仓库与你的远端仓库不是同一个仓库.

可以使用 ： `git pull --allow-unrelated-histories `