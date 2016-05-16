title: Mysql 数据类型的属性
date: 2016-03-13 16:00:16
tags:
- Mysql
- 数据类型
- 属性
- database
- 数据库

---

## AUTO_INCREMENT
auto_increment能为新插入的行赋一个唯一的整数标识符。为列赋此属性将为每个新插入的行赋值为上一次插入的ID+1。
MySQL要求将auto_increment属性用于作为主键的列。此外，每个表只允许有一个auto_increment列。例如：

``` SQL
id smallint not null auto_increment primary key
```

---

## BINARY
binary属性只用于char和varchar值。当为列指定了该属性时，将以区分大小写的方式排序。与之相反，忽略binary
属性时，将使用不区分大小写的方式排序。例如：

``` SQL
hostname char(25) binary not null
```

---

## DEFAULT
default属性确保在没有任何值可用的情况下，赋予某个常量值，这个值必须是常量，因为MySQL不允许插入函数或表达式值。
此外，此属性无法用于BLOB或TEXT列。如果已经为此列指定了NULL属性，没有指定默认值时默认值将为NULL，否则默认值将
依赖于字段的数据类型。例如：

``` SQL
subscribed enum('0', '1') not null default '0'
```

---

## INDEX
如果所有其他因素都相同，要加速数据库查询，使用索引通常是最重要的一个步骤。索引一个列会为该列创建一个有序的键数
组，每个键指向其相应的表行。以后针对输入条件可以搜索这个有序的键数组，与搜索整个未索引的表相比，这将在性能方面
得到极大的提升。

``` SQL
create table employees
(
    id varchar(9) not null,
    firstname varchar(15) not null,
    lastname varchar(25) not null,
    email varchar(45) not null,
    phone varchar(10) not null,
    index lastname(lastname),
    primary key(id)
);
```

---

## NOT NULL
如果将一个列定义为not null，将不允许向该列插入null值。建议在重要情况下始终使用not null属性，因为它提供了
一个基本验证，确保已经向查询传递了所有必要的值。

---

## NULL
为列指定null属性时，该列可以保持为空，而不论行中其它列是否已经被填充。记住，null精确的说法是“无”，而不是空字符串或0。

---

## PRIMARY KEY
primary key属性用于确保指定行的唯一性。指定为主键的列中，值不能重复，也不能为空。为指定为主键的列赋予auto_increment属性
是很常见的，因为此列不必与行数据有任何关系，而只是作为一个唯一标识符。主键又分为以下两种：

(1)单字段主键
如果输入到数据库中的每行都已经有不可修改的唯一标识符，一般会使用单字段主键。注意，此主键一旦设置就不能再修改。
(2)多字段主键
如果记录中任何一个字段都不可能保证唯一性，就可以使用多字段主键。这时，多个字段联合起来确保唯一性。如果出现这种情况，指定一
个auto_increment整数作为主键是更好的办法。

---

## UNIQUE
被赋予unique属性的列将确保所有值都有不同的值，只是null值可以重复。一般会指定一个列为unique，以确保该列的所有值都不同。例如：

``` SQL
email varchar(45) unique
```

---

## ZEROFILL
zerofill属性可用于任何数值类型，用0填充所有剩余字段空间。例如，无符号int的默认宽度是10；因此，当“零填充”的int值为4时，将
表示它为0000000004。例如：

``` SQL
orderid int unsigned zerofill not null
```

---

## 引用参考

 - [MySQL数据类型和属性](http://www.jellythink.com/archives/642)
