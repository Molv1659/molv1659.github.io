---
title: Git 常用操作&原理
date: 2021/05/09
photos: https://github.com/Molv1659/molv1659.github.io/tree/main/cdn/article-covers/17.JPG
categories: 砂糖实验室
avatar: https://github.com/Molv1659/molv1659.github.io/tree/main/cdn/Kirito1.jpg
authorLink: http://www.sisicheng.com
---
permalink: git

![img](git-1024x707.png)

图来自 https://www.bilibili.com/video/BV1ni4y1t7jK 这个视频，简单例子演示可以去看这个。

原理示例可以看https://www.bilibili.com/video/BV11z4y1X79p 这个视频。

# Git常用操作

## 1 初始化

- git init 为当前文件夹进行Git初始化，本地库。
- git config --global user.name "your name"
- git config --global user.email "you@domain.com"

## 2 分支内的操作

- git add [file] 将文件保存到暂存区
- git add . 将所有文件保存到暂存区
- git commit 将暂存区的修改保存到代码库
- git status 查看当前状态，列出所有新修改，暂存区文件修改情况
- git log -n 查看最近n次commit记录
- git reset -hard commit_id 将工作区暂存区都恢复到之前某次提交的版本
- git diff [file] 查看工作区和暂存区的差别
- git rm [file] 将文件从工作区里和暂存区里删除
- git reflog 显示之前的操作记录
- git checkout -- [file] 把工作区的新修改撤销掉
- git reset HEAD [file] 把暂存区的新修改撤销掉
- git stash 把工作区修改内从保存到贮藏区
- git stach pop 把贮藏区内容恢复到工作区

## 3 分支操作

- git branck -a 列出当地所有分支
- git switch -c [name] 创建一个新的name分支
- git switch [name] 切换到name分支
- git merge [name] 将name分支与当前分支合并
- git branch -d [name] 删除name分支

## 4 远程库操作

- git clone [repo url] 从远程代码库下载整个代码库和历史记录
- git remote add <remote name> <url> 链接一个远程库，remote name一般就origin
- git fetch 从远程代码库下载所有变动
- git pull 从远程库拉取代码并将当前分支与他的upstream merge
- git push [remote] [branch] 将当前代码库推送到远程remote库的branch分支，remote一般就origin

# Git实现原理

![img](image.png)

总共这三种对象。如果有多个一样的文件数据，只存一次（Git会根据文件内容算出一个哈希值，同哈希值的只在物理内存上存一次，之后都是指针指过来）。Commit类指向现在最新的Tree文件夹，同时Commit类还有指向上一次commit的指针，所以版本间回溯很方便。大概就长下面这个样。

![img](image-1.png)

![img](image-2.png)

当前是add commit完，工作区暂存区代码仓库都是一致的。

![img](image-3.png)

对文件修改后，git add干的事情就是把新文件重新构建一个blob放在代码仓库，然后暂存区的Tree指向代码库里新的这个blob

![img](image-4.png)

git commit就是在代码仓库复制出一个暂存区的当前Tree，然后生成一个新的Commit类作为HEAD，同时新的Commit类指向parent。

![img](image-5.png)

开分支的话成本就很低，只是新建了一个Commit类，指向当前HEAD所指的Tree，进一步改动后才开始有blob相关的开销，所以即使debug也建议新建一个分支，调好了再切到master分支然后把debug分支merge过来

