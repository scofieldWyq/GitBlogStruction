title: Linux 文件属性读取
date: 2016-03-08 16:10:09
tags:
- Linux
- file attribute
- stat

---

## 简单说一下

  **使用 stat 函数，通过文件的绝对路径或者相对路径的文件名去打开相应文件的属性**
  
## 包含的头文件
  ``` bash
  #include <sys/stat.h>
  ```

## 参考函数
  ``` bash
  int stat(const char *path, struct stat *buf);

  ```
## 读取文件属性

  ``` bash
  ...

  struct stat *infobuf;

  if (stat("/etc/passwd", &infobuf) == -1) {
    perror("/etc/passwd");
  } else {
    printf("The size of /etc/passwod is %d\n", infobuf.st_size);
  }

  ...

  ```

  [stat 结构](http://scofieldwyq.github.io/2016/03/08/Linux-%E6%96%87%E4%BB%B6%E5%B1%9E%E6%80%A7%E7%9A%84%E7%BB%93%E6%9E%84%E4%BD%93/)
