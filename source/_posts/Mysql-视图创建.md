title: Mysql 视图创建
date: 2016-03-16 15:15:50
tags:
- Mysql
- VIEW
- 视图

---

## 关于视图 - 简单看看([如果不想知道视图用来干嘛的，那就跳过咯](#create))

  `SQL` 中，视图时基于SQL语句的结果集的可视化的表

  `视图`包含行和列，就像一个真实的表一样。

  `视图`中的字段来自于一个或者多个数据库中的表的字段。

  结果就是感觉就是单一的一张表，也可以说是间接的表啦。

  使用`视图`，主要是为在操作数据库的时候，不在需要频繁多次去读取和处理不同字段，再进行第二次的处理形成我们所需要的数据。在这一步上面，我们可以提高效率，得到我们所需要的内容哦。

  这样，我们可以把多张表合并成一张表，经过过滤之后的一张表哦。

  `视图`是一种虚拟的表。`视图`从数据库中的一个或多个表导出来的表。`视图`还可以从已经存在的视图的基础上定义。数据库中只存放了视图的定义，而并没有存放视图中的数据。这些数据存放在原来的表中。使用视图查询数据时，数据库系统会从原来的表中取出对应的数据。因此，视图中的数据是依赖于原来的表中的数据的。一旦表中的数据发生改变，显示在视图中的数据也会发生改变。

  `视图`是在原有的表或者视图的基础上重新定义的虚拟表，这可以从原有的表上选取对用户有用的信息。那些对用户没有用，或者用户没有权限了解的信息，都可以直接屏蔽掉。这样做既使应用简单化，也保证了系统的安全。视图起着类似于筛选的作用。视图的作用归纳为如下几点：
    1．使操作简单化
    2．增加数据的安全性
    3．提高表的逻辑独立性

  [`注释`：数据库的设计和结构不会受到视图中的函数、where 或 join 语句的影响。]


  **OK,实际上。意思就是把多张表经过处理后的到一张整理过的，有需要的一张表，但是这个表的操作不会影响到原表的完整性，读它就可以啦。**

## <span id="create">创建视图</span>

**语法：**
``` sql
  CREATE VIEW viewName AS
  SELECT column_name(s)
  FROM table_name
  WHERE condition
```
[`注释`：视图总是显示最近的数据。每当用户查询视图时，数据库引擎通过使用 SQL 语句来重建数据。]


## 实践检验问题

   **可以从某个查询内部、某个存储过程内部，或者从另一个视图内部来使用视图。通过向视图添加函数、join 等等，我们可以向用户精确地提交我们希望提交的数据。**

   需要[准备数据文件](https://raw.githubusercontent.com/scofieldWyq/wyqBlog/master/code/mysql_create_view_database_prepare.sql)来做好操作的准备,里面是关于教师和学生的一个数据库表。

### 走起
 **创建视图**
  ``` sql
    mysql> CREATE VIEW student_teacher AS
        -> SELECT sname, tname
        -> FROM student, teacher
        -> WHERE student.tno=teacher.tno;

    Query OK, 0 rows affected (0.13 sec)

    mysql> select * from student_teacher;
    +-------+-------+
    | sname | tname |
    +-------+-------+
    | sa    | wa    |
    | sb    | wa    |
    | sc    | wa    |
    | sd    | wa    |
    | se    | wa    |
    | sf    | wa    |
    | sg    | wa    |
    | sh    | wa    |
    | si    | wa    |
    | sj    | wa    |
    | sk    | wa    |
    | sl    | wa    |
    | sm    | wa    |
    | sn    | wa    |
    +-------+-------+
    14 rows in set (0.06 sec)

  ```

  这样，我们就可以得到了关于教师和学生的一个列表，但是我们并不知道这个是来自于两个表哦。

 **更新视图**
 ``` sql
 SQL CREATE OR REPLACE VIEW Syntax

  CREATE OR REPLACE VIEW view_name AS
  SELECT column_name(s)
  FROM table_name
  WHERE condition

  ------------------------
 ```

  这个是一个简单的例子。

 **撤销视图**
 ``` sql
   SQL DROP VIEW Syntax
   DROP VIEW view_name

   ------------------------
   mysql> DROP VIEW student_teacher;
   Query OK, 0 rows affected (0.30 sec)

 ```
## 参考链接
- [MySQL 视图的创建，修改与删除](http://www.360doc.com/content/13/1117/22/7669533_330092770.shtml)
- [MySQL视图表创建与修改](http://www.linuxidc.com/Linux/2012-02/53842.htm)
- [mysql的视图操作](http://zhangzhenyihi.blog.163.com/blog/static/13548809420141104122391/)
- [mysql中create view创建、更新和删除视图](http://www.php186.com/content/article/mysql/22726.html)
- [MySQL中INSERT的一般用法](http://www.blogjava.net/midnightPigMan/archive/2014/12/15/421406.html)
- [Mysql命令insert into：向表中插入数据（记录）](http://c.biancheng.net/cpp/html/1452.html)
- [insert 出错](http://jingyan.baidu.com/article/9f7e7ec05c5ad76f281554ab.html)
- [Mysql列约束,字段属性](http://wenku.baidu.com/link?url=SJeXJhp0ZgeTQnFfJhc4WUQL5Ov_34l57QKeUcW6nkcY0-GJO5ImFQHUuZpDeB-jTJ6buU87_AAJ2ix8ZWX0J0fwKIcqmWei7HKQd1RMopy)
