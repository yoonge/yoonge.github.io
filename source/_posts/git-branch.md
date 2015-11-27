title: Git 远程、本地分支操作
date: 2014-11-20 18:26:48
tags: git
categories: Notes
---
## 查看本地分支

``` bash
$ git branch
* hexo
  master
```

## 查看本地和远程分支

``` bash
$ git branch -a
* hexo
  master
  remotes/origin/hexo
  remotes/origin/master
```

## 创建本地分支 test

<!--more-->

``` bash
$ git branch test

$ git branch
* hexo
  master
  test
```

## 切换到本地分支 test

``` bash
$ git checkout test
Switched to branch 'test'

$ git branch
  hexo
  master
* test
```

## 把本地分支 test 推送到远程分支

``` bash
$ git push origin test
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/yoonge/yoonge.git
* [new branch]    test -> test

$ git branch -a
  hexo
  master
* test
  remotes/origin/hexo
  remotes/origin/master
  remotes/origin/test
```

## 同步本地远程分支

``` bash
$ git fetch origin
```

## 提交本地分支数据到远程分支

``` bash
$ git push origin test:test   # <local_branch_name>:<remote_branch_name>
Everything up-to-date
```

如果当前处于 test 分支下，也可以直接：

``` bash
$ git push
```

## 删除远程分支 test

``` bash
$ git push origin :test
To https://github.com/yoonge/yoonge.git
- [deleted]    test

$ git branch -a
  hexo
  master
* test
  remotes/origin/hexo
  remotes/origin/master
```

### 删除本地分支 test

``` bash
$ git checkout hexo
Switched to branch 'hexo'

$ git branch -d test
Deleted branch test (was 131eba3).

$ git brach
* hexo
  master
```
