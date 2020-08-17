---
title: Git 常用命令
article-thumbnail: false
keywords: [git]
top: 100
toc: true
tags: [git]
date: 2020-06-22 09:02:29
thumbnail:
categories: Tools
---
Git是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。
<!-- more -->

**常用命令**
```code
mkdir testgit //创建目录 

cd testgit //进入创建的目录 

pwd //显示当前目录位置

git init //仓库初始化 

touch learngit.md  //创建md文件

ls //查看当前目录下文件

vim learngit.md //进入vim 模式

i //进入输入模式(Insert mode)

esc + shift + : //退出输入模式，切换到命令模式

:wq // 保存并退出vim

git add learngit.md //提交当前文件至暂存库
git add .  //t  //提交该目录下所以文件至暂存库

git commit -m "最终提交仓库“ //最终提交仓库，其中-m后面输入的是本次提交的说明

git status //查看仓库状态

git diff //查看修改记录

git log //查看历史提交（commit)记录（提交id)
git log --pretty=oneline //单行简化查看

cat learngit.md //查看文件文本内容

git reset --hard HEAD^ //回退上一个版本，^以此类推回退版本数，回退100可用：HEAD~100
git reset --hard commit_id //commit_id可由git log 查看）

git reflog //查看历史提交id记录（不同于git log ），可用来重新回到未来版本

git checkout -- learngit.md //丢弃上一步工作区的修改
git reset HEAD learngit.md // 如果修改后已提交暂存区，再重复上一步

rm learngit.md //删除本地文件

git rm learngit.md //删除版本库中的文件

git checkout -- learngit.md //如工作区文件删除或修改，还原与版本库相同的版本

ssh-keygen -t rsa -C "youremail@example.com" //创建SSH Key

ssh -T git@github.com  //测试是否连接自己的github账号

git remote add origin git@github.com:Aimerence/learngit.git //关联远程主机

git push -u origin master // -u 将本地master与远程master分支关联起来，简化推送/拉取命令，将本地库推送到远程仓库
git push origin master //以后只需要直接提交了

git clone git@github.com:Aimerence/learngit.git //克隆远程库到本地

git checkout -b dev //创建dev分支，并切换到dev分支，相当于下面两个命令
git branch dev
git checkout dev

git switch -c dev //创建并切换到新的dev分支
 git switch master //切换到已有的master分支

git branch //查看当前所在的分支

git merge dev //合并分支

git branch -d dev //删除分支

git branch -D <name> //强制删除一个没有被合并过的分支

git remote //查看远程库信息
git remote -v //查看更详细信息

 git push origin master //推送主分支
 git push origin dev //推送开发分支

git checkout -b dev origin/dev //创建远程origin的dev分支到本地

git branch --set-upstream-to=origin/dev dev //设置dev和origin/dev的链接

git pull //拉下来进行本地冲突处理

git tag v1.0 //打标签
git tag //查看所以标签
git tag v0.9 commit-id //指定打标签
git show <tagname> //查看标签信息

```

**参考文档**
- [廖雪峰的git教程](https://www.liaoxuefeng.com/wiki/896043488029600)

- [Git官方网站](https://git-scm.com/)

- [Git Cheat Sheet](https://gitee.com/liaoxuefeng/learn-java/raw/master/teach/git-cheatsheet.pdf)
