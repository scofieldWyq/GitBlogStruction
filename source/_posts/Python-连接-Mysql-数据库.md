title: Python 连接 Mysql 数据库
date: 2016-03-14 15:01:19
tags:
- Python
- Mysql
- MySQLdb
- 数据库
- database

---

## 连接 mysql 数据库

 使用 MySQLdb 来做为连接 mysql 数据库。

 ``` python
 import MySQLdb
 
 try:
      # host 表示主机类型
      # user 登录的用户
      # passwd 登录密码
      # db 登录的数据库
      # port 端口号，在本地情况下可以不用写
      conn=MySQLdb.connect(host='localhost',user='root',passwd='root',db='test',port=3306) # 连接数据库
      cur=conn.cursor() # 获取数据库的指针
      cur.execute('select * from user') # 数据库操作
      cur.close() # 关闭数据库的指针
      conn.close() # 关闭数据库
except MySQLdb.Error,e: # 数据库连接失败。
      print "Mysql Error %d: %s" % (e.args[0], e.args[1])
 ```

## 问题

  如果出现了这种情况
 ``` python
 Traceback (most recent call last):
  File "db_test.py", line 1, in <module>
    import MySQLdb
ImportError: No module named MySQLdb
 ```
 说明没有安装相应的库

## 安装 MySQLdb

[Python下的Mysql模块MySQLdb安装详解](http://www.jb51.net/article/48827.htm)
[下载Mysql模块MySQLdb](https://sourceforge.net/projects/mysql-python/files/mysql-python/1.2.3/MySQL-python-1.2.3.tar.gz/download)

## 参考链接
- [python操作MySQL数据库](http://www.cnblogs.com/rollenholt/archive/2012/05/29/2524327.html)
- [Python下的Mysql模块MySQLdb安装详解](http://www.jb51.net/article/48827.htm)
- [MySQL-python-1.2.3.tar.gz](https://sourceforge.net/projects/mysql-python/files/mysql-python/1.2.3/MySQL-python-1.2.3.tar.gz/download)
