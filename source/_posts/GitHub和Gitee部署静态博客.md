---
title: GitHub和Gitee部署静态博客
date: 2021-09-07 09:53:13
tags:
---

# 说明

之前顺利从GitHub上构建了静态博客，但是考虑到访问速度问题，决定将原来的博客迁移到Gitee同步部署。但是，设置上略有不同，此处所记录的就是这个设置过程。

<!--more-->
# 配置文件的修改

在站点根目录下找到`_config.yml`,将里边的`deploy`节点修改成下边的形式，其中`repository`等于`username`，即

```
deploy:
  type: git
  repo:
     github: git@github.com:[username]/[username].github.io.git,master
     gitee: git@gitee.com:[username]/[username].git,master
```

将上边的仓库`url`的[username]/[repository]改成自己的项目地址，这里使用的是SSH协议的Git仓库地址，即：

```
git@[domain]:[username]/[username].git
```

推荐使用SSH协议的地址，免去每次pull/push输入账号密码的繁琐，也确保安全。
