title: Git 安装
date: 2016-03-01 11:14:49
tags:

- Git
- install
- Mac
- Windows
- Linux

---

![](http://git-scm.com/images/logo@2x.png)
> [Git 官网](http://git-scm.com/)

---

- [Mac 安装 Git](#mac)
- [Windows 安装 Git](#windows)
- [Linux 安装 Git](#linux)

# <span id="mac">Mac 安装 Git</span>

## Mac 本身就有 Git 了

```{bash}
$ which git
/usr/bin/git
$ git --version
git version 2.5.4 (Apple Git-61)
```

## Mac 还没有安装 Git

  **使用homebrew来安装 Git - command line**

### 安装 homebrew
 - [安装 homebrew](http://brew.sh/),安装后

 ```{bash}
 $ which brew
/usr/local/bin/brew
$ brew --version
Homebrew 0.9.5 (git revision e15a; last commit 2016-02-03)
 ```
然后就安装好了。。。

## Git 官网的方式安装
![git](http://git-scm.com/images/logo@2x.png)
[官方文档的方式安装 － http://git-scm.com/](http://git-scm.com/download/)

---

# <span id="windows">Windows 安装 Git</span>

## 1. 来源于[廖雪峰的Git教学网站](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137396287703354d8c6c01c904c7d9ff056ae23da865a000)
> 实话实说，Windows是最烂的开发平台，如果不是开发Windows游戏或者在IE里调试页面，一般不推荐用Windows。不过，既然已经上了微软的贼船，也是有办法安装Git的。
-- 来源于[廖雪峰的  Git 教学](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137396287703354d8c6c01c904c7d9ff056ae23da865a000)

Windows下要使用很多Linux/Unix的工具时，需要Cygwin这样的模拟环境，Git也一样。Cygwin的安装和配置都比较复杂，就不建议你折腾了。不过，有高人已经把模拟环境和Git都打包好了，名叫msysgit，只需要下载一个单独的exe安装程序，其他什么也不用装，绝对好用。

msysgit是Windows版的Git，从http://msysgit.github.io/下载，然后按默认选项安装即可。

安装完成后，在开始菜单里找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功！
![image](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/git_install_1.jpeg?raw=true)
安装完成后，还需要最后一步设置，在命令行输入：

```{bash}
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

因为Git是分布式版本控制系统，所以，每个机器都必须自报家门：你的名字和Email地址。你也许会担心，如果有人故意冒充别人怎么办？这个不必担心，首先我们相信大家都是善良无知的群众，其次，真的有冒充的也是有办法可查的。

注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

## 2.官网的教学方法
![image](http://git-scm.com/images/logo@2x.png)
[下载链接](http://git-scm.com/download/win)

[Git安装教程](http://jingyan.baidu.com/article/7f766dafba84f04101e1d0b0.html)


# <span id="linux">Linux 安装 Git</span>

- 不同的版本有不同包管理工具
- 我使用的是`Centos`

**安装Git**
```{bash}
$ sudo yum install -y git //然后输入你的 password
```
**安装过程**
```{bash}
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: mirrors.btte.net
 * extras: mirrors.pubyun.com
 * updates: mirrors.btte.net
Setting up Install Process
Resolving Dependencies
--> Running transaction check
---> Package git.x86_64 0:1.7.1-3.el6_4.1 will be installed
--> Processing Dependency: perl-Git = 1.7.1-3.el6_4.1 for package: git-1.7.1-3.el6_4.1.x86_64
--> Processing Dependency: rsync for package: git-1.7.1-3.el6_4.1.x86_64
--> Processing Dependency: perl(Git) for package: git-1.7.1-3.el6_4.1.x86_64
--> Processing Dependency: perl(Error) for package: git-1.7.1-3.el6_4.1.x86_64
--> Processing Dependency: openssh-clients for package: git-1.7.1-3.el6_4.1.x86_64
--> Running transaction check
---> Package openssh-clients.x86_64 0:5.3p1-112.el6_7 will be installed
--> Processing Dependency: openssh = 5.3p1-112.el6_7 for package: openssh-clients-5.3p1-112.el6_7.x86_64
--> Processing Dependency: libedit.so.0()(64bit) for package: openssh-clients-5.3p1-112.el6_7.x86_64
---> Package perl-Error.noarch 1:0.17015-4.el6 will be installed
---> Package perl-Git.noarch 0:1.7.1-3.el6_4.1 will be installed
---> Package rsync.x86_64 0:3.0.6-12.el6 will be installed
--> Running transaction check
---> Package libedit.x86_64 0:2.11-4.20080712cvs.1.el6 will be installed
---> Package openssh.x86_64 0:5.3p1-94.el6 will be updated
--> Processing Dependency: openssh = 5.3p1-94.el6 for package: openssh-server-5.3p1-94.el6.x86_64
---> Package openssh.x86_64 0:5.3p1-112.el6_7 will be an update
--> Running transaction check
---> Package openssh-server.x86_64 0:5.3p1-94.el6 will be updated
---> Package openssh-server.x86_64 0:5.3p1-112.el6_7 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package             Arch       Version                       Repository   Size
================================================================================
Installing:
 git                 x86_64     1.7.1-3.el6_4.1               base        4.6 M
Installing for dependencies:
 libedit             x86_64     2.11-4.20080712cvs.1.el6      base         74 k
 openssh-clients     x86_64     5.3p1-112.el6_7               updates     438 k
 perl-Error          noarch     1:0.17015-4.el6               base         29 k
 perl-Git            noarch     1.7.1-3.el6_4.1               base         28 k
 rsync               x86_64     3.0.6-12.el6                  base        335 k
Updating for dependencies:
 openssh             x86_64     5.3p1-112.el6_7               updates     274 k
 openssh-server      x86_64     5.3p1-112.el6_7               updates     324 k

Transaction Summary
================================================================================
Install       6 Package(s)
Upgrade       2 Package(s)

Total download size: 6.1 M
Downloading Packages:
--------------------------------------------------------------------------------
Total                                           1.8 MB/s | 6.1 MB     00:03     
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction

  Updating   : openssh-5.3p1-112.el6_7.x86_64                              1/10

  Installing : 1:perl-Error-0.17015-4.el6.noarch                           2/10

  Installing : libedit-2.11-4.20080712cvs.1.el6.x86_64                     3/10

  Installing : openssh-clients-5.3p1-112.el6_7.x86_64                      4/10

  Installing : rsync-3.0.6-12.el6.x86_64                                   5/10

  Installing : perl-Git-1.7.1-3.el6_4.1.noarch                             6/10

  Installing : git-1.7.1-3.el6_4.1.x86_64                                  7/10

  Updating   : openssh-server-5.3p1-112.el6_7.x86_64                       8/10

  Cleanup    : openssh-server-5.3p1-94.el6.x86_64                          9/10

  Cleanup    : openssh-5.3p1-94.el6.x86_64                                10/10

  Verifying  : openssh-clients-5.3p1-112.el6_7.x86_64                      1/10

  Verifying  : perl-Git-1.7.1-3.el6_4.1.noarch                             2/10

  Verifying  : 1:perl-Error-0.17015-4.el6.noarch                           3/10

  Verifying  : rsync-3.0.6-12.el6.x86_64                                   4/10

  Verifying  : libedit-2.11-4.20080712cvs.1.el6.x86_64                     5/10

  Verifying  : openssh-5.3p1-112.el6_7.x86_64                              6/10

  Verifying  : git-1.7.1-3.el6_4.1.x86_64                                  7/10

  Verifying  : openssh-server-5.3p1-112.el6_7.x86_64                       8/10

  Verifying  : openssh-5.3p1-94.el6.x86_64                                 9/10

  Verifying  : openssh-server-5.3p1-94.el6.x86_64                         10/10

Installed:
  git.x86_64 0:1.7.1-3.el6_4.1                                                  

Dependency Installed:
  libedit.x86_64 0:2.11-4.20080712cvs.1.el6                                     
  openssh-clients.x86_64 0:5.3p1-112.el6_7                                      
  perl-Error.noarch 1:0.17015-4.el6                                             
  perl-Git.noarch 0:1.7.1-3.el6_4.1                                             
  rsync.x86_64 0:3.0.6-12.el6                                                   

Dependency Updated:
  openssh.x86_64 0:5.3p1-112.el6_7    openssh-server.x86_64 0:5.3p1-112.el6_7   

Complete!

```
**安装完成后**

```{bash}
$ which git
/usr/bin/git
$ git --version
git version 1.7.1
```
**OK, 其他版本的Linux大概也就是这样的了**

## 参考链接

- [Homebrew](http://brew.sh/)
- [http://git-scm.com/](http://git-scm.com/)
- [廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
- [git - 简易指南](http://www.bootcss.com/p/git-guide/)
- [Git详解之一：Git起步](http://blog.jobbole.com/25775/)
- [GIT](http://baike.baidu.com/link?url=IWINhIXDsfMCThAtC_aHb8bPWrwsgwBuZfwPzbGBjoOeOT6F6GYyTV8F4Jn4JnpP90laupdcCRcCn9z--V02mobrOnLMr2Q1H5h4aNJEfRC)
- [推荐！手把手教你使用Git](http://blog.jobbole.com/78960/)
- [如何在windows下安装GIT](http://jingyan.baidu.com/article/90895e0fb3495f64ed6b0b50.html)
- [GitHub Guides](https://guides.github.com/activities/hello-world/)
