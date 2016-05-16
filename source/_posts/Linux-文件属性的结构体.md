title: Linux 文件属性的结构体
date: 2016-03-08 15:57:28
tags:
- Linux
- file
- struct
- stat
---

## 从帮助中查信息
  ``` bash
  $ man -k file | grep -i status
  fileno [ferror]      (3)  - check and reset stream status
  fstat                (3p)  - get file status
  fstatat              (2)  - get file status relative to a directory file descriptor
  fstat [stat]         (2)  - get file status
  lstat [stat]         (2)  - get file status
  stat                 (1)  - display file or file system status
  stat                 (2)  - get file status
  stat                 (3p)  - get file status

  $ man 2 stat
  ...(内容省略)
  ```

## 文件结构体所在的头文件

 - sys/stat.h
 ``` bash
 #include <sys/stat.h>
 ```

## 文件结构体

 - 结构体 \- `stat`
 ``` bash 
 struct stat {
               dev_t     st_dev;     /* ID of device containing file */
               ino_t     st_ino;     /* inode number */
               mode_t    st_mode;    /* protection */
               nlink_t   st_nlink;   /* number of hard links */
               uid_t     st_uid;     /* user ID of owner */
               gid_t     st_gid;     /* group ID of owner */
               dev_t     st_rdev;    /* device ID (if special file) */
               off_t     st_size;    /* total size, in bytes */
               blksize_t st_blksize; /* blocksize for file system I/O */
               blkcnt_t  st_blocks;  /* number of 512B blocks allocated */
               time_t    st_atime;   /* time of last access */
               time_t    st_mtime;   /* time of last modification */
               time_t    st_ctime;   /* time of last status change */
           };
 ```
