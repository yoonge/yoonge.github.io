title: 'Github 和 GitCafe 同步托管 Hexo 博客'
date: 2015-12-24 17:04:53
tags:
    - hexo
    - git
    - github
    - gitcafe
categories: Notes
---
由于国内网络原因，托管在 github 上的 hexo 博客访问速度很慢，有时甚至打不开。于是考虑将博客同步托管到 gitcafe，然后默认线路指向 gitcafe，海外线路指向 github，这样既可以解决国内访问慢的问题，同时 github 上的备份也算是个保障 —— 毕竟人家已经相当成熟。
那么，基于 github 上已经搭建好的 hexo 博客，开始吧：

### 注册 GitCafe

首先，必须注意 git 全局变量中的 user.name 和 user.email 在 github 和 gitcafe 两个网站的注册信息必须是一致的。在 github 上搭建 hexo 博客的时候已经设置过 git 全局变量，可以使用以下命令查看：

``` bash
$ git config --get user.name
Yoonge

$ git config --get user.email
yoonge@zyi.tw
```

使用以上邮箱和用户名注册 gitcafe。

设置 git 全局变量可以使用以下命令：

``` bash
$ git config --global user.name 'Yoonge'

$ git config --get user.email 'yoonge@zyi.tw'

```

### 创建 GitCafe 项目

参照 gitcafe 官网说明创建一个与用户名相同的项目（我这里是 yoonge），然后进入你的本地 hexo 博客目录下的 .deploy_git 目录，创建 gitcafe-pages 分支，并切换到该分支：

``` bash
$ git branch gitcafe-pages

$ git branch
* master
  gitcafe-pages

$ git checkout gitcafe-pages
Switched to branch 'gitcafe-pages'
```

To be continued...
