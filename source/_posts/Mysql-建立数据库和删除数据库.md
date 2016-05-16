title: Mysql 建立数据库和删除数据库
date: 2016-03-16 12:05:37
tags:
- Mysql
- database

---

## 创建数据库

 - CREATE DATABASE `databaseName`
 ``` sql
   mysql> CREATE DATABASE test;
   Query OK, 1 row affected (0.05 sec)
   mysql> SHOW DATABASES;
  +--------------------+
  | Database           |
  +--------------------+
  | information_schema |
  | demo               |
  | mysql              |
  | performance_schema |
  | studentSystem      |
  | sys                |
  | test               |
  | zh                 |
  +--------------------+
  8 rows in set (0.03 sec)

 ```

 - CREATE DATABASE IF NOT EXISTS `databaseName`
 ``` sql
   mysql> CREATE DATABASE IF NOT EXISTS test1;
   Query OK, 1 row affected (0.00 sec)

   mysql> SHOW DATABASES;
   +--------------------+
   | Database           |
   +--------------------+
   | information_schema |
   | demo               |
   | mysql              |
   | performance_schema |
   | studentSystem      |
   | sys                |
   | test               |
   | test1              |
   | zh                 |
   +--------------------+
   9 rows in set (0.00 sec)
 ```

## 删除数据库

  - DROP DATABASE `databaseName`
  ``` sql
  mysql> DROP DATABASE test;
  Query OK, 0 rows affected (0.05 sec)

  mysql> SHOW DATABASES;
  +--------------------+
  | Database           |
  +--------------------+
  | information_schema |
  | demo               |
  | mysql              |
  | performance_schema |
  | studentSystem      |
  | sys                |
  | test1              |
  | zh                 |
  +--------------------+
  8 rows in set (0.03 sec)
  ```

  - DROP DATABASE IF EXISTS `databaseName`
  ``` sql
  mysql> DROP DATABASE IF EXISTS test1;
  Query OK, 0 rows affected (0.00 sec)

  mysql> SHOW DATABASES;
  +--------------------+
  | Database           |
  +--------------------+
  | information_schema |
  | demo               |
  | mysql              |
  | performance_schema |
  | studentSystem      |
  | sys                |
  | zh                 |
  +--------------------+
  7 rows in set (0.00 sec)
  ```

## 参考链接

 - [Mysql命令drop database：删除数据库](http://c.biancheng.net/cpp/html/1446.html)
 - [mysql create database 指定utf-8编码](http://outofmemory.cn/code-snippet/2533/mysql-create-database-specify-utf-8-coding)
 - [Mysql命令create：创建数据库](http://c.biancheng.net/cpp/html/1444.html)
