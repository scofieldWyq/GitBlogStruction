title: Mysql 建立表和删除表
date: 2016-03-16 12:05:59
tags:
- Mysql
- table

---

## 创建表
  - CREATE TABLE `tableName`
  ``` sql
    mysql> CREATE TABLE person (
                number INT(11),
                name VARCHAR(255),
                birthday DATE
                );
  ```

  - CREATE TABLE IF NOT EXISTS `tableName`
  ``` sql
    mysql> CREATE TABLE IF NOT EXISTS person (
                    number INT(11),
                    name VARCHAR(255),
                    birthday DATE
                    );
  ```

## 删除表
  - DROP TABLE `tableName`
  ``` sql
  mysql> DROP TABLE  tbl_name;

  ```

  - DROP TABLE IF EXISTS `tableName`
  ``` sql
  mysql> DROP TABLE IF EXISTS tbl_name;
  
  ```

## 参考链接
- [mysql创建和删除表](http://www.cnblogs.com/ggjucheng/archive/2012/11/03/2752082.html)
