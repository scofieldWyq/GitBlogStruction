title: Linux 目录操作
date: 2016-03-08 16:09:48
tags:
- Linux
- Directory
- opendir
- readdir
- closedir
- seekdir
- Directory_operation

---

## 简单说明一下

  **目录是文件的列表，在Linux下对于目录来说是有系统调用可以使用来操作目录的。**

  **目录的操作需要一个目录文件绝对路径或者当前目录的相对路径。**

  **目录操作的大概过程为：打开目录，读取目录内容放入目录的结构体里面，然后对于结构体的数据进行呈现，最后不需要的时候关闭目录。**

  **打开目录，会得到一个打开的目录文件描述符 `DIR` (一个无符号整数)，读取目录内容需要目录的文件描述符.**

  **`DIR` 作为 打开目录的文件描述符的宏参数**

---

## open

 - 函数参考
  ``` bash
  DIR *opendir(const char *name); /* name: 目录的绝对路径或者相对路径 */
  ```

- 开始打开文件
  ``` bash
  /**
  使用该函数打开目录，返回的目录文件描述符可以用于读取目录内容。

  */
  ...
  DIR *dir_ptr ; /* 目录文件描述符指针 */

  if ((dir_ptr = opendir("/")) == NULL) { /* 打开目录 */
    fprintf(stderr, "something error: %s", name);
  }
  ...

  ```
  ---

## read

  - 函数参考
  ``` bash
  int readdir(unsigned int fd, struct old_linux_dirent *dirp,
                   unsigned int count);
  ```

  - 开始读取目录内容
  ``` bash
  /**
  使用该目录文件描述符，读取目录文件的内容，放入结构体指针中。

  */
  ...
  struct dirent *direntp; /* 目录结构体指针 */

  while ((direntp = readdir(dir_ptr)) != NULL) { /* 读取存入结构体 */
    printf("%s\n", direntp->d_name);
  }
  ...

  ```

  [dirent 结构体的内容](http://scofieldwyq.github.io/2016/03/08/Linux-%E7%9B%AE%E5%BD%95%E5%86%85%E5%AE%B9%E7%9A%84%E7%BB%93%E6%9E%84/)

## close

  - 函数参考
  ``` bash
  int closedir(DIR *dirp);
  ```

  - 关闭目录
  ``` bash 
  /**
  使用目录文件描述符关闭目录。

  */
  ...
  closedir(dir_ptr);
  ...

  ```

---

## move curser
