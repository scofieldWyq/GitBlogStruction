title: node 安装
date: 2016-03-01 11:15:33
tags:
- node
- install

---
# 关于Node

> Node 是一个服务器端 JavaScript 解释器，它将改变服务器应该如何工作的概念。它的目标是帮助程序员构建高度可伸缩的应用程序，编写能够处理数万条同时连接到一个（只有一个）物理机的连接代码。

---

> Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient. Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world.

---

# 安装Node

## Node for Mac

   - 安装 `Homebrew`
   ![node_install_p_2](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/node_install_p_2.png?raw=true)
    [安装Homebrew](http://brew.sh/)
   - 安装 node
    ```{bash}
    $ brew install node
    $ node --version
    v5.5.0
    ```
   **这样在 Mac 下的 Node 就安装好了**

## Node for Windows
  - 下载安装文件

  ![image](https://nodejs.org/static/images/logos/nodejs-new-white-pantone.png)
  [官网](http://www.nodejs.org/download/)
  ![node_install_p_1](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/node_install_p_1.png?raw=true)

  - 安装Node

    双击它，默认是安装在`C:\Program Files\nodejs`下面

    打开`C:\Program Files\nodejs`目录你会发现里面自带了npm,直接用npm安装相环境既可进入`node.js command prompt` 命令窗口进入nodejs 安装目录 `C:\Program Files\nodejs`

    键入命令：`cd C:\Program Files\nodejs` 既可

  - 现在开始安装相关环境

    键入命令：`npm install express` 回车等待安装 `express`........

    键入命令：`npm install mysql` 回车等待安装 `mysql`........

    ........安装什么组件，取决于环境搭建需求

    默认情况下上述组件都是安装在`C:\Program Files\nodejs\node_modules`文件夹下 这也是nodejs相关组件的自动查找路径

  **这样在 Windows 下的 Node 就安装好了**

## Node for Linux

  - 下载 `Node`
    ```{bash}
    $ wget http://nodejs.org/dist/v0.8.7/node-v0.8.7.tar.gz
    ```

  - 解压文件
    ```{bash}
    $ tar -zxvf node-v0.8.7.tar.gz
    ```

  - 检查所需要配置
    ```{bash}
    $ ./configure

     出现错误提示：
     Exception: Call to '(echo | $(echo ${CXX_host:-$(which g++)}) -m32 -E -

     > /dev/null 2>&1) && echo "-m32" || true' returned exit status 0. while

    loading dependencies of /opt/node-v0.8.7/node.gyp while trying to load

    /opt/node-v0.8.7/node.gyp
    ```
    + 如出现以上错误，安装gcc-c++
    ```{bash}
    $ yum install gcc-c++
    ```
  - 进行安装(时间比较长)：
    ```{bash}
    $ make install
    ```

  - 检查是否成功安装，输入命令：
    ```{bash}
    $ node -v
    v5.5.0
    ```
    **这样在 Linux 下的 Node 就安装好了**

**安装完 node 后 npm 也就安装完了**

---

# 参考链接

- [Node](https://nodejs.org/en/)
- [下载Node](https://nodejs.org/en/download/)
- [Node.js 教程](http://www.runoob.com/nodejs/nodejs-tutorial.html)
- [Node.js 究竟是什么？](http://www.ibm.com/developerworks/cn/opensource/os-nodejs/)
- [windows 下安装nodejs及其配置环境](http://www.cnblogs.com/pigtail/archive/2013/01/08/2850486.html)
