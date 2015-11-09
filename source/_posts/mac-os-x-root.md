title: Mac OS X 下开启 root 用户
date: 2013-01-03 10:39:38
tags:
- mac
- os x
categories: Notes
---
在 Mac OS X 下使用 su 指令想暂时切入 root 用户下，输入密码会发现无法登陆 root 用户。
这是因为默认情况下 root 用户密码未被设置，需要先用 passwd 命令来设置一下:

``` bash
passwd root

Changing password for root.
Old Password:
New Password:
Retype New Password:
passwd: authentication token failure
```

<!--more-->

提示失败，试试 sudo ：

``` bash
sudo passwd root
```

好了，这时再用 su ：

``` bash
appletekiMacBook-Air:~ apple$ su
Password:
sh-3.2#
```

搞定。使用 root 完毕，用 exit 退出即可。
