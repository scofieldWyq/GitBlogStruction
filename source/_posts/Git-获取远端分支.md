title: Git 获取远端分支
date: 2016-03-13 11:27:58
tags:
- Git
- fetch
- checkout
- branch
---

## 将远程分支信息获取到本地
``` bash
$ git fetch
```

## 将远程分支映射到本地
``` bash
$ git checkout -b changeCodeStruct_local origin/changeCodeStruct
Branch changeCodeStruct_local set up to track remote branch changeCodeStruct from origin.
Switched to a new branch 'changeCodeStruct_local'
$ git branch
* changeCodeStruct_local
  dev
  master

```

## 结束

这样就可以把远端的分支获取到了。
