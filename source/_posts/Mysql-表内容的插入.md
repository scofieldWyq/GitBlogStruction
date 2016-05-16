title: Mysql 表内容的插入
date: 2016-03-16 17:07:00
tags:
- Mysql
- INSERT

---

## INSERT

  表插入的语法：
  ``` sql
    INSERT [LOW_PRIORITY | DELAYED | HIGH_PRIORITY] [IGNORE]
      [INTO] tbl_name [(col_name,...)]
      VALUES ({expr | DEFAULT},...),(...),...
      [ ON DUPLICATE KEY UPDATE col_name=expr, ... ]
    或：
    INSERT [LOW_PRIORITY | DELAYED | HIGH_PRIORITY] [IGNORE]
      [INTO] tbl_name
      SET col_name={expr | DEFAULT}, ...
      [ ON DUPLICATE KEY UPDATE col_name=expr, ... ]
    或：
  INSERT [LOW_PRIORITY | HIGH_PRIORITY] [IGNORE]
      [INTO] tbl_name [(col_name,...)]
      SELECT ...
      [ ON DUPLICATE KEY UPDATE col_name=expr, ... ]
  ```

## 实验证明

- 如果列清单和VALUES清单均为空清单，则INSERT会创建一个行，每个列都被设置为默认值：

 ``` sql
 INSERT INTO tbl_name () VALUES();
 ```
- 假设worker表只有name和email,插入一条数据

 ``` sql
 INSERT INTO worker VALUES(“tom”,”tom@yahoo.com”);
 ```
- 批量插入多条数据
 ``` sql
 INSERT INTO worker VALUES(‘tom','tom@yahoo.com'),(‘paul','paul@yahoo.com');
 ```

- 给出要赋值的那个列，然后再列出值的插入数据
 ``` sql
 insert into worker (name) values ('tom');
 ```

## 参考链接
- [mysql insert语句操作实例讲解](http://www.jb51.net/article/58087.htm)
