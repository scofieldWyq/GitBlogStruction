title: Man为什么查不到和书上的相似的结果
date: 2016-03-04 10:33:37
tags:
- Linux
- Man
- command line
- keyword -k

---

## 解决man无法找到你想要的内容
 - [安装好man后，发现你查询的内容是 No manual entry for *** ](#q1)
 - [man -k {file} | grep {read} 没有结果](#q2)

## <span id="q1">1.安装好 `man` 后，发现你查询的内容是 `No manual entry for ***` </span>

 **原因： 没有安装 `man-pages`**

 **解决方案**
 ``` bash
 $ sudo yum install -y man-pages //如果权限问题，切换到root下
 ```

## <span id="q2">2.man -k {file} | grep {read} 没有结果</span>

 **原因：本地数据库没有更新**

 **解决方案**
 ``` bash 
 $ sudo makewhatis //如果权限问题，切换到 root 下
 ```
