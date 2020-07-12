---
title: basic
date: 2020-07-11 23:08:35
tags:
---
## Git配置相关
### 获取本地SSH并绑定至Github
1. 获取SSH：`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
    __"your_email@example.com"需替换为注册github的邮箱__

1. 查看SSH：`cat ~/.ssh/id_rsa.pub`
SSH地址是以ssh-rsa开头，自己邮箱地址结尾的。

1. 进入github首页，单机头像，选中settings


