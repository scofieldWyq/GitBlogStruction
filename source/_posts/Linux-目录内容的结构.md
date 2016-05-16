title: Linux 目录内容的结构
date: 2016-03-08 15:41:10
tags:
- Linux
- Directory
- struct
- dirent

---

## 从帮助中查信息

  ``` bash
  $ man -k direct | grep read
  readdir              (2)  - read directory entry
  readdir              (3p)  - read a directory
  readdir              (3)  - read a directory
  readdir_r [readdir]  (3p)  - read a directory
  readdir_r [readdir]  (3)  - read a directory
  readlinkat           (2)  - read value of a symbolic link relative to a directory file descriptor
  seekdir              (3)  - set the position of the next readdir() call in the directory stream

  $ man 3 readdir
  ...(内容省略)

  ```

## 目录结构所在的头文件

  - dirent.h
   ``` bash
    #include <dirent.h>
   ```

## 保存目录内容的结构体

  - 结构体 \- `dirent`
   ``` bash 
   struct dirent {
                 ino_t          d_ino;       /* inode number */
                 off_t          d_off;       /* offset to the next dirent */
                 unsigned short d_reclen;    /* length of this record */
                 unsigned char  d_type;      /* type of file; not supported
                                                by all file system types */
                 char           d_name[256]; /* filename */
             };
   ```
