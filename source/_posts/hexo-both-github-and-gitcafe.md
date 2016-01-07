title: 'Github 和 GitCafe 同步托管 Hexo 博客'
date: 2015-12-24 17:04:53
tags:
    - hexo
    - git
    - github
    - gitcafe
    - dnspod
categories: Notes
---
由于国内网络原因，托管在 github 上的 hexo 博客访问速度很慢，有时甚至打不开。于是考虑将博客同步托管到 gitcafe，然后默认线路指向 gitcafe，国外线路指向 github，这样既可以解决国内访问慢的问题，同时 github 上的备份也算是个保障 —— 毕竟人家已经相当成熟。
那么，基于 github 上已经搭建好的 hexo 博客，开始吧：

### 注册 GitCafe

首先，必须注意 git 全局变量中的 user.name 和 user.email 在 github 和 gitcafe 两个网站的注册信息必须是一致的。在 github 上搭建 hexo 博客的时候已经设置过 user.name 和 user.email，可以使用以下命令查看：

<!--more-->

``` bash
$ git config --get user.name
Yoonge

$ git config --get user.email
yoonge@zyi.tw
```

然后使用以上邮箱和用户名注册 gitcafe。

设置 git 全局变量可以使用以下命令：

``` bash
$ git config --global user.name 'Yoonge'

$ git config --global user.email 'yoonge@zyi.tw'

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

然后添加 gitcafe 的远程仓库，并 push 到该仓库：

``` bash
$ git remote add origin 'git@gitcafe.com:yoonge/yoonge.git'

$ git push origin gitcafe-pages

```

### 同步更新博客到 Github 和 GitCafe

同样在 github 上搭建 hexo 博客的时候已经设置过 \_config.yml：

``` bash
# Deployment
# Docs: http://hexo.io/docs/deployment.html
deploy:
    type: git
    repository: https://github.com/yoonge/yoonge.github.io.git
    branch: master
```

那么每次博客有更新的时候，只需要在你本地 hexo 博客目录下执行：

``` bash
$ hexo d -g    # 确保 .deploy_git 目录当前处于 master 分支
```

就可以直接将更新提交到 github。然后进入该目录下的 .deploy_git 目录，执行以下命令：

``` bash
$ cd .deploy_git    # 进入 .deploy_git 目录

$ git checkout gitcafe-pages    # 切换到 gitcafe-pages 分支

$ git merge master    # 将 master 分支合并到当前所在的 gitcafe-pages 分支

$ git push origin gitcafe-pages    # 将 gitcafe-pages 分支提交到 gitcafe 远程仓库

$ git checkout master    # 完事儿切换回 master 分支，确保博客下次更新时 .deploy_git 目录处于 master 分支    
```

这样就实现了 gitcafe 与 github 博客同步更新。当然，如果觉得每次提交需要执行这么多命令，可以写个复合命令别名添加到 .bashrc 文件：

``` bash
alias hexoall = 'hexo d -g && cd .deploy_git && git checkout gitcafe-pages && git merge master && git push origin gitcafe-pages && git checkout master && cd ..'
```

这样以后博客有更新，只需要在你本地 hexo 博客目录下执行 hexoall 就可以了。

### 设置访问线路

如果有自己的域名，推荐使用 dnspod 提供的域名解析服务：

1. 添加两条 CNAME 记录，主机记录分别为 @ 和 www，线路类型默认，记录值均为 gitcafe.io. （注意最后有个点，你不加的话也没关系，dnspod 会自动为你添加）；
2. 添加四条 A 记录，主机记录分别为 @ 和 www，线路类型国外，记录值分别为 192.30.252.153 和 192.30.252.154 。

等待设置生效，再刷新博客看下，有没有感觉快多了 ：）
