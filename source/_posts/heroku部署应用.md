---
title: heroku部署应用
tags:
  - heroku
  - 变量
categories:
  - heroku部署应用
abbrlink: 502b664d
date: 2019-01-08 15:56:43
---
``` js

heroku create "应用名"  #创建应用

git init  #初始化

heroku git:remote -a "应用名"  #连接到应用

git add . 

git commit -am "make it better"

git push heroku master

heroku config:set "变量内容" #添加变量

heroku open #打开应用