---
title: git命令使用
tags:
  - git
  - 命令
categories:
  - git
abbrlink: fb31f1f7
date: 2019-01-05 19:11:45
---
# 使用Git命令把本地项目上传到Github托管  
## &nbsp;&nbsp;&nbsp;&nbsp;我在这篇文章中将会详细实现如何把一个你在本地写好的项目（或者正在写的项目）上传到Github进行托管或者多人合作。具体步骤如下：

## （1）首先在Github上新建一个repository，我命名为NewsClient，其他的根据自己的需求填写即可

## （2）创建完成后，注意到右下角的项目URL，复制一下，以后会用到

## (3) 然后我在本地有一个项目，名称为News，终端进入我的项目目录

## (4) 执行命令：git init

## 该命令是在你的项目目录下初始化一个repository，执行成功后，会在你的目录下生成一个.git的隐藏文件。

## (5) 执行命令：git add .

## 注意该命令后面有一个“.”,小点。表示把该目录下的所有文件加入到本地暂存区中。执行成功后不会有任何提示

## (6) 执行命令：git status

## 该命令会把你本地工作区和暂存区的版本进行比较，查看当前的状态。我下面的状态是已经把所有文件加入到了暂存区中，但是还没有提交到本地历史区。（可跳过）

## (7) 执行命令：git commit -m "这里是注释。。。"

## 该命令会把本地暂存区中的文件提交到本地历史区，注意只有在本地历史区中的内容才能提交到github。执行该命令后，我们所有的文件都只是在本地。没有github任何关系。git commit -m "Initial commit"

## (8) 执行命令：git remote add origin https://github.com/username/repository.git
## git remote add origin git@github.com:username/repository.git

## 该命令是把本地历史区中的文件添加到github服务器的暂存区中。这一步是本地和远程服务器建立联系的一步。执行成功后不会显示任何结果

## (9) 执行命令：git pull origin master

## 该命令是先把github上的文件拉下来，注意在每次提交之前要首先进行pull，这是防止冲突。

## (10) 执行命令：git push -u origin master

## 这一步是真正向github提交，执行完成后，github上的repository就有和你本地一样的代码文件了。

## 初次提交是上面的命令，多次为git push origin master

