title: 将 Sublime Text 添加到右键菜单
date: 2014-12-25 11:56:30
tags:
    - sublime text
    - windows
    - regedit
categories: Notes
---
经常右键编辑文件，右键菜单里居然找不到 Sublime Text，不能忍，果断祭出注册表大法：

1. 打开注册表：Win + R 打开运行对话框，输入 regedit，回车；
2. 找到 HKEY_CLASSES_ROOT → \* → shell，邮件新建**项**，命名为 Sublime Text 2；
3. 再在 Sublime Text 2 上右键新建**字符串值**，命名为 Icon，值为 “Sublime Text 2 所在的路径,0”，比如我这里就是：
``` bash
D:\Program Files (x86)\Sublime Text 2\sublime_text.exe,0
```
4. 最后在 Sublime Text 2 下面新建**项** command，双击**默认**，输入值：
``` bash
D:\Program Files (x86)\Sublime Text 2\sublime_text.exe %1
```
5. 关闭注册表，不用重启，即刻生效。

赶紧随便找个文本文件试试，Sublime Text 2 果然已经出现在了右键菜单，还带图标呢 ：）
