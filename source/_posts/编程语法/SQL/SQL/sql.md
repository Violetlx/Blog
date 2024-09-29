---
title: SQL使用教程
tags:
  - [SQL]
categories:
  - [编程语法]
description: SQL使用教程
top_img: 'https://wallpaperaccess.com/full/2138094.jpg'
cover: 'https://wallpaperaccess.com/full/2138094.jpg'
abbrlink: 5d06cb2d
date: 2024-09-20 14:15:27
---

<img src="https://roaringelephant.org/wp-content/uploads/sites/5/2016/03/SQL.jpg" alt="SQL" height="300" />

# SQL 教程

**SQL** ( `Structured Query Language` ，结构化查询语言) 是一种用于管理和操作关系型数据库的标准化编程语言。

在线测试工具：https://www.jyshare.com/front-end/7768/



------



## SQL 简介

**SQL** （ `Structured Query Language` ，结构化查询语言）是用于管理关系数据库管理系统 （**RDBMS**）。

SQL 通过一系列的语句和命令来执行数据定义、数据查询、数据操作和数据控制等功能，包括数据插入、查询、更新和删除，数据库模式创建和修改，以及数据访问控制。



### SQL 是什么？

- SQL 值结构化查询语言，全称是 `Structured Query Language`
- SQL 让你可以访问和处理数据库，包括数据插入、查询、更新和删除
- SQL 语言采用英语关键词，使其易读易写
- SQL 有国际标准化组织 (ISO) 和美国国家标准协会 (ANSI) 标准化
- SQL 提供了丰富的操作数据的功能，从简单的查询到复杂的数据库管理操作



### SQL 能做什么？

- SQL 面向数据库执行查询
- SQL 可以从数据库取回数据
- SQL 可在数据库中插入新的记录
- SQL 可更新数据库中的数据
- SQL 可创建新数据库
- SQL 可在数据库中创建新表
- SQL 可在数据库中创建存储过程
- SQL 可在数据库中创建视图
- SQL 可设置表、存储过程和视图的权限



### SQL 是一种标准-但是 ...

虽然 SQL 是一门 ANSI （American National Standards Institute 美国国家标准化组织）标准的计算机语言，但是任然存在着许多不同版本的 SQL 语言。

然而，为了与 ANSI 标准相兼容，他们必须以相似的方式共同地来支持一些主要的命令 （比如 SELECT、UPDATE、DELETE、INSERT、WHERE 等等）。

> 💡   注释：除了 SQL 标准外，大部分 SQL 数据库都拥有它们自己的专有扩展！



### 在网站中使用 SQL

要创建一个显示数据库中数据的网站：

- RDBMS 数据库程序（比如 MS Access、SQL Server、MySQL）
- 使用服务器端脚本语言，比如 PHP 或 ASP
- 使用 SQL 来获取您想要的数据
- 使用 HTML / CSS



### RDBMS

RDBMS 指关系型数据库管理系统，全称 `Relational Database Management System`。

RDBMS 是 SQL 的基础，同样也是所有现代数据库系统的基础，比如 MS SQL Server、IBM DB2、Oracle、MySQL 以及 Microsoft Access。

RDBMS 中的数据存储在被称为表的数据库对象中。

表是相关的数据项的集合，它由列和行组成。



### SQL 发展历史

以下是 SQL 发展历史的关键节点：

#### 1970s: 起源与早期发展

1. **1970年**：埃德加·科德（Edgar F. Codd）发表了《A Relational Model of Data for Large Shared Data Banks》论文，提出了关系数据库的概念，为 SQL 的发展奠定了理论基础。
2. **1973年-1974年**：IBM 的研究人员 Donald D. Chamberlin 和 Raymond F. Boyce 在科德的理论基础上开发了一种名为 SEQUEL（Structured English Query Language）的语言，用于操作和管理 IBM 的 System R 关系数据库。
3. **1976年**：SEQUEL 更名为 SQL（Structured Query Language）。

#### 1980s: 标准化与商业化

1. **1981年**：IBM 推出了商用关系数据库系统 SQL/DS（Database System）和 DB2（Database 2）。
2. **1986年**：美国国家标准协会（ANSI）发布了第一个 SQL 标准 ANSI SQL-86（SQL-87）。
3. **1987年**：国际标准化组织（ISO）也采纳了 ANSI SQL-86 作为国际标准。

#### 1990s: 扩展与改进

1. **1992年**：发布了 SQL-92（SQL2）标准，显著扩展了 SQL 语言的功能，包括对新数据类型、嵌套查询和连接的支持。
2. **1999年**：发布了 SQL:1999（SQL3）标准，引入了对象关系数据库（ORDBMS）特性、递归查询、触发器和用户定义函数。

#### 2000s: 持续演进与新特性

1. **2003年**：发布了 SQL:2003 标准，引入了 XML 相关特性和窗口函数。
2. **2006年**：发布了 SQL:2006 标准，主要增强了对 XML 的支持。
3. **2008年**：发布了 SQL:2008 标准，进一步改进了语法和性能优化。

#### 2010s: 新功能与大数据支持

1. **2011年**：发布了 SQL:2011 标准，增加了对时间数据类型和时间旅行（temporal data）的支持。
2. **2016年**：发布了 SQL:2016 标准，引入了 JSON 数据类型和相关操作函数，适应了 NoSQL 数据库和大数据处理需求。

#### 2020s: 现代化与标准更新

1. **2023年**：最新的 SQL 标准持续改进，增加了对更现代化的数据库需求和特性的支持。

#### 总结

SQL 从一种基于关系模型的查询语言发展成为现代数据库管理的核心语言，其标准在不断演进和扩展。各大数据库管理系统（如 MySQL、PostgreSQL、SQLite、SQL Server、Oracle 等）在遵循 SQL 标准的基础上，加入了自身的扩展和优化，使 SQL 成为数据操作和管理的强大工具。SQL 的发展不仅体现了技术的进步，也反映了数据管理需求的变化和增长。



------



## SQL 语法

**SQL**（Structured Query Language）是一种用于管理和操作关系数据库的标准语言，包括数据查询、数据插入、数据更新、数据删除、数据库结构创建和修改等功能

![ https://www.runoob.com/wp-content/uploads/2013/09/SQL.png](https://www.runoob.com/wp-content/uploads/2013/09/SQL.png)



### 数据库表

一个数据库通常包含一个或多个表，每个表有一个名字标识（例如:"**Websites**"），表包含带有数据的记录（行）。

在本教程中，我们在 MySQL 的 RUNOOB 数据库中创建了 Websites 表，用于存储网站记录。

我们可以通过以下命令查看 "Websites" 表的数据：

```sql
mysql> use RUNOOB;
Database changed

mysql> set names utf8;
Query OK, 0 rows affected (0.00 sec)

mysql> SELECT * FROM Websites;
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+
5 rows in set (0.01 sec)

```

**解析**

- **use RUNOOB;** 命令用于选择数据库。
- **set names utf8;** 命令用于设置使用的字符集。
- **SELECT \* FROM Websites;** 读取数据表的信息。
- 上面的表包含五条记录（每一条对应一个网站信息）和5个列（id、name、url、alexa 和country）。



### SQL 语句

你需要在数据库上执行的大部分工作都由 SQL 语句完成。

下面的 SQL 语句从 **Websites** 表中选取所有记录：

**实例**

```sql
SELECT * FROM Websites;
```



### 请记住 ...

- SQL 对大小写不敏感：**SELECT** 和 **select** 是相同的



### SQL 语句后面加分号?

某些数据库系统要求在每条 SQL 语句的末端使用分号。

分号是在数据库系统中分隔每条 SQL 语句的标准方法，这样就可以在对服务器的相同请求中执行一条以上的 SQL 语句。



### 一些重要的 SQL 命令

- **SELECT**  - 从数据库中提取数据
- **UPDATE** - 更新数据库中的数据
- **DELETE** - 从数据库中删除数据
- **INSERT INTO** - 向数据库中插入新数据
- **CREATE DATABASE** - 创建新数据库
- **ALTER DATABASE** - 修改数据库
- **DROP TABLE** - 删除表
- **CREATE INDEX** - 创建索引 （搜索值）
- **DROP INDEX** - 删除索引

以下是一些常用的 SQL 语句和语法：

`SELECT`：用于从数据库中查询数据

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
ORDER BY column_name [ASC|DESC]
```

- `column_name(s)` ：要查询的列
- `table_name` ：要查询的表
- `condition` ： 查询调价 （可选）
- `ORDER BY` ：排序方式，**ASC** 表示升序，**DESC** 表示降序

`INSERT INTO` ：用于向数据库插入新数据

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...)
```

- `table_name` ：要插入数据的表
- `(column1, column2, ...)` ：要插入数据的列
- `(value1, value2, ...)` ：对应列的值

`UPDATE` ：用于更新数据库表中的现有数据

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition
```

- `table_name` ：要更新数据的表
- `column1 = value1, column2 = value2, ...` ：要更新的列及其新值
- `condition` ：更新条件

`DELETE` ：用于从数据库表中删除数据

```sql
DELETE FROM table_name
WHERE condition
```

- `table_name` ：要删除数据的表
- `condition` ：删除条件

`CREATE TABLE` ：用于创建新的数据库表

```sql
CREATE TABLE table_name (
    column1 data_type constraint,
    column2 data_type constraint,
    ...
)
```

- `table_name` ：要创建的表明
- `column1,column2, ...` ：表的列
- `data_type` ：列的数据类型 （如 **INT**、**VARCHAR** 等）
- `constraint` ：列的约束 （如 **PRIMARY KEY** 、**NOT NULL** 等）

`ALETER TABLE` ：用于修改现有数据库表的结构

```sql
ALTER TABLE table_name
ADD column_name data_type
```

- `table_name` ：要修改的表
- `column_name` ：要添加的列
- `data_type` ：列的数据类型

或：

```sql
ALTER TABLE table_name
DROP COLUMN column_name
```

- `column_name`：要删除的列

`DROP TABLE` ：用于删除数据库表

```sql
DROP TABLE table_name
```

- `table_name` ：要删除的表

`CREATE INDEX` ：用于创建索引，以加快查询速度

```sql
CREATE INDEX index_name
ON table_name (column_name)
```

- `index_name` ：索引的名称
- `column_name` ：要索引的列

`DROP INDEX` ：用于删除索引

```sql
DROP INDEX index_name
ON table_name
```

- `index_name` ：要删除的索引名称
- `table_name` ：索引所在的表

`WHERE` ：用于指定筛选条件。

```sql
SELECT column_name(s)
FROM table_name
WHERE condition
```

- `condition` ：筛选条件。

`ORDER BY` ：用于对结果集进行排序

```sql
SELECT column_name(s)
FROM table_name
ORDER BY column_name [ASC|DESC]
```

- `column_name` ：用于排序的列
- `ASC` ：升序（默认）
- `DESC` ：降序

`GROUP BY` ：用于将结果集按一列或多列进行分组

```sql
SELECT column_name(s), aggregate_function(column_name)
FROM table_name
WHERE condition
GROUP BY column_name(s)
```

- `aggregate_function(column_name)` ：聚合函数 （如 **COUNT** 、**SUM** 、**AVG** 等）

`HAVING` ：用于对分组后的结果集进行筛选

```sql
SELECT column_name(s), aggregate_function(column_name)
FROM table_name
GROUP BY column_name(s)
HAVING condition
```

- `condition` ：筛选条件

`JOIN` ：用于将两个或多个表的记录结合起来

```sql
SELECT column_name(s)
FROM table_name1
JOIN table_name2
ON table_name1.column_name = table_name2.column_name
```

- `JOIN`: 可以是 INNER JOIN、LEFT JOIN、RIGHT JOIN 或 FULL JOIN。

`DISTINCT` ：用于返回唯一不同的值。

```sql
SELECT DISTINCT column_name(s)
FROM table_name
```

- `column_name(s)`：要查询的列。



------

## SQL SELECT

**SELECT**  语句用于从数据库中选取数据。

结果被存储在一个结果表中，称为结果集。



### SQL SELECT 语法 

```sql
SELECT column1, column2, ...
FROM table_name;
```

与

```sql
SELECT * FROM table_name;
```

参数说明：

- `column1, column2, ...` ：要选择的字段名称，可以为多个字段。如果不指定字段名称，则会选择所有字段。
- `table_name` ：要查询的表名称。
- `*`  ：通配符，表示选择表中的所有列。



### 演示数据库

下面是选自 "**Websites**" 表的数据：

```sql
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+

```



### SELECT Column 实例

下面的 SQL 语句从 Websites 表中选取 name 和 country 列：

实例：

```sql
SELECT name,country FROM Websites;
```

输出结果：

![ https://www.runoob.com/wp-content/uploads/2013/09/98E6B49C-06AF-469B-B907-81C52BBE6BDC.jpg](https://www.runoob.com/wp-content/uploads/2013/09/98E6B49C-06AF-469B-B907-81C52BBE6BDC.jpg)



### SELECT *  实例

下面的 SQL 语句从 Websites 表中选取所有列：

实例：

```sql
SELECT * FROM Websites;
```

输出结果：

![https://www.runoob.com/wp-content/uploads/2013/09/DE979628-6FAF-46BD-920F-18F9565ADD78.jpg](https://www.runoob.com/wp-content/uploads/2013/09/DE979628-6FAF-46BD-920F-18F9565ADD78.jpg)



------



## SQL SELECT DISTINCT

SELECT DISTINCT 语句用于返回唯一不同的值。

在表中，一个列可能包含多个重复值，有时你也许希望仅仅列出不同 （**distinct**）的值。

DISTINCT 关键词用于返回唯一不同的值。



### SQL SELECT DISTINCT 语法

```
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

参数说明：

- `column1, column2, ...` ：要选择的字段名称，可以为多个字段。如果不指定字段名称，则会选择所有字段。
- `table_name` ：要查询的表名称。



### 演示数据库

下面是选自 "**Websites**" 表的数据：

```sql
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+

```



### SELECT DISTINCT 实例

下面的 SQL 语句仅从 Websites 表的 country 列中选取唯一不同的值，也就是去掉 contry 列的重复值：

实例：

```sql
SELECT DISTINCT country FROM Websites;
```

输出结果：

![https://www.runoob.com/wp-content/uploads/2013/09/E3012A35-35DF-4BBB-8657-8A312C5AEAB6.jpg](//www.runoob.com/wp-content/uploads/2013/09/E3012A35-35DF-4BBB-8657-8A312C5AEAB6.jpg)



------

## SQL WHERE

**where** 子句用于过滤记录



### SQL WHERE 子句

**WHERE** 子句用于提取那些满足指定条件的记录。



### SQL WHERE 语法

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

参数说明：

- `column1, column2, ...`：要选择的字段名称，可以为多个字段。如果不指定字段名称，则会选择所有字段。
- `table_name`：要查询的表名称。



### 演示数据库

下面是选自 "**Websites**" 表的数据：

```sql
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+

```



### WHERE 子句实例

下面的 SQL 语句从 "Websites" 表中选取国家为 "CN" 的所有网站：

实例：

```sql
SELECT * FROM Websites WHERE country='CN';
```

输出结果：

![https://www.runoob.com/wp-content/uploads/2013/09/4B7980AC-2566-43F7-843A-256E868B92A4.jpg](https://www.runoob.com/wp-content/uploads/2013/09/4B7980AC-2566-43F7-843A-256E868B92A4.jpg)



### 文本字段 vs. 数值字段

SQL 使用单引号来环绕文本值 （大部分数据库系统也接受双引号）

在上个实例中 'CN' 文本字段使用了单引号。

如果是数值字段，请不要使用引号。

实例：

```sql
SELECT * FROM Websites WHERE id=1;
```

输出结果：

![https://www.runoob.com/wp-content/uploads/2013/09/639D2956-99CE-44E9-B960-EA14D296820E.jpg](https://www.runoob.com/wp-content/uploads/2013/09/639D2956-99CE-44E9-B960-EA14D296820E.jpg)



### WHERE 子句中的运算符

下面的运算符可以在 WHERE 子句中使用：

| 运算符  | 描述                                                       |
| :------ | :--------------------------------------------------------- |
| =       | 等于                                                       |
| <>      | 不等于。**注释：**在 SQL 的一些版本中，该操作符可被写成 != |
| >       | 大于                                                       |
| <       | 小于                                                       |
| >=      | 大于等于                                                   |
| <=      | 小于等于                                                   |
| BETWEEN | 在某个范围内                                               |
| LIKE    | 搜索某种模式                                               |
| IN      | 指定针对某个列的多个可能值                                 |





## SQL AND & OR

AND & OR 运算符用于基于一个以上的条件对记录进行过滤。



### SQL AND & OR 运算符

如果第一个条件和第二个条件都成立，则 AND 运算符显示一条记录。

如果第一个条件和第二个条件只要有一个成立，则 OR 运算符显示一条记录。



### 演示数据库

下面是选自 "**Websites**" 表的数据：

```sql
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+

```



### AND  运算符实例

下面的 SQL 语句从 **Websites** 表中选取国家为 CN 且 alexa 排名大于 50 的所有网站：

实例：

```sql
SELECT * FROM Websites
WHERE country='CN'
AND alexa > 50;
```

输出结果：

![https://www.runoob.com/wp-content/uploads/2013/09/and-or1.jpg](https://www.runoob.com/wp-content/uploads/2013/09/and-or1.jpg)



### OR 运算符实例

下面的 SQL 语句从 Websites 表中选取国家为 USA 或者 CN 的所有客户：

实例：

```sql
SELECT * FROM Websites
WHERE country='USA'
OR country='CN';
```

输出结果：

![https://www.runoob.com/wp-content/uploads/2013/09/and-or2.jpg](https://www.runoob.com/wp-content/uploads/2013/09/and-or2.jpg)



结合 AND & OR

可以把 AND 和 OR 结合起来（使用圆括号来组成复杂的表达式）

下面的 SQL 语句从 Websites 表中选取 alexa 排名大于 15 且国家为 CN 或 USA 的所有网站：

实例：

```sql
SELECT * FROM Websites
WHERE alexa > 15
AND (country = 'CN' OR country = 'USA');
```

输出结果：

![https://www.runoob.com/wp-content/uploads/2013/09/and-or3.jpg](https://www.runoob.com/wp-content/uploads/2013/09/and-or3.jpg)





## SQL ORDER BY

ORDER BY 关键字用于对结果集进行排序。



### SQL ORDER BY 关键字

ORDER BY 关键字用于对于结果集按照一个列或者多个列进行排序。

ORDER BY 关键字默认按照升序对记录进行排序，如果需要按照降序对记录进行排序，你可以使用 **DESC** 关键字。



### SQL ORDER BY 语法

```sql
SELECT column1,column2, ...
FROM table_name
ORDER BY column1,column2, ... ASC|DESC;
```

- `column1,column2, ...` ：要排序的字段名称，可以为多个字段
- `ASC` ：表示按升序排序
- `DESC` ：表示按降序排序



### 演示数据库

下面是选自 "**Websites**" 表的数据：

```sql
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+

```



### ORDER BY 实例

下面的 SQL 语句从 Websites 表中选取所有网站，并按照 alexa 列排序：

实例：

```sql
SELECT * FROM Websites
ORDER BY alexa;
```

输出结果：

![https://www.runoob.com/wp-content/uploads/2013/09/orderby1.jpg](https://www.runoob.com/wp-content/uploads/2013/09/orderby1.jpg)



### ORDER BY DESC 实例

下面的 SQL 语句从 Websites 表中选取所有网站，并按照 alexa 列降序排序：

实例：

```sql
SELECT * FROM Websites
ORDER BY alexa DESC;
```

输出结果：

![https://www.runoob.com/wp-content/uploads/2013/09/orderby2.jpg](https://www.runoob.com/wp-content/uploads/2013/09/orderby2.jpg)



### ORDER BY 多列

下面的 SQL 语句从 Websites 表中选取所有网站，并且按照 country 和 alexa 列排序：

实例：

```sql
SELECT * FROM Websites
ORDER BY country,alexa;
```

输出结果：

![ https://www.runoob.com/wp-content/uploads/2013/09/orderby3.jpg](https://www.runoob.com/wp-content/uploads/2013/09/orderby3.jpg)



## SQL INSERT INTO

INSERT INTO 语句用于向表中插入新记录



### SQL INSERT INTO 语法

INSERT INTO 语句有两种可以编写形式。

第一种形式无需指定要插入数据的列名，值需要提供被插入的值即可：

```sql
INSERT INTO table_name
VALUES (value1,value2,value3,...);
```

第二种形式需要指定列名及被插入的值：

```sql
INSERT INTO table_name (column1,column2,column3,..)
VALUES (value1,value2,value3,...);
```

参数说明：

- `table_name` ：需要插入新纪录的表名
- `column1,column2,column3,..` ：需要插入的字段名
- `value1,value2,value3,...` ：需要插入的字段值。



### 演示数据库

下面是选自 "**Websites**" 表的数据：

```sql
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+

```



INSERT INTO 实例

假设我们要向 Websites 表中插入一个新列

我们可以使用下面的 SQL 语句

实例：

```sql
INSERT INTO Websites (name,url,alexa,country)
VALUES ('百度','https://www.baidu.com/','4','CN');
```

输出结果：

![https://www.runoob.com/wp-content/uploads/2013/09/insert1.jpg](https://www.runoob.com/wp-content/uploads/2013/09/insert1.jpg)



> 💡   你是否注意到，我们没有向 id 字段插入任何数字？
>
> id 列是自动更新的，表中的每条记录都有一个唯一的数字



### 在指定的列插入数据

我们也可以在指定的列插入数据

下面的 SQL 语句将插入一个新行，但只是在 name、url 和 country 列插入数据 (id字段会自动更新)

实例：

```sql
INSERT INTO Websites (name,url,country)
VALUES ('stackoverflow', 'http://stackoverflow.com/', 'IND');
```

输出结果：

![ https://www.runoob.com/wp-content/uploads/2013/09/insert2.jpg](https://www.runoob.com/wp-content/uploads/2013/09/insert2.jpg)





## SQL UPDATE

UPDATE 语句用于更新表中的记录



### SQL UPDATE 语法

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

参数说明：

- `table_name` ：要修改的表的名称
- `column1,column2,...` ：要修改的字段名称，可以为多个字段
- `value1,value2,...` ：要修改的值，可以为多个值
- `condition` ：修改条件，用于指定哪些数据要修改

> 💡   请注意 SQL UPDATE 语句中的 WHERE 子句！
>
> WHERE 子句规定哪条记录或者哪些记录需要更新。如果你省略了 WHERE 子句，所有的记录都将被更新！



### 演示数据库

下面是选自 "**Websites**" 表的数据：

```sql
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+

```



### SQL UPDATE 实例

假设我们要把 菜鸟教程 的 alexa 排名更新为 5000，country 改为 USA

我们使用下面的 SQL 语句

实例：

```sql
UPDATE Websites 
SET alexa='5000', country='USA' 
WHERE name='菜鸟教程';
```

输出结果：

![https://www.runoob.com/wp-content/uploads/2013/09/update1.jpg](https://www.runoob.com/wp-content/uploads/2013/09/update1.jpg)



### UPDATE 警告！

在更新记录时要格外小心！在上面的实例中，如果我们省略了 WHERE 子句，如下所示：

```sql
UPDATE Websites
SET alexa='5000', country='USA'
```

执行以上代码会将 Websites 表中所有数据的 alexa 改为 5000，country 改为 USA

执行没有 WHERE 子句的 UPDATE 要慎重，再慎重。



## SQL DELETE

DELETE 语句用于删除表中的记录



SQL DELETE 语法

```sql
DELETE FROM table_name
WHERE condition;
```

参数说明：

- `table_name` ：要删除的表的名称
- `condition` ：删除条件，用于指定哪些数据要删除

> 💡   请注意 SQL DELETE 语句中的 WHERE 子句！
>
> WHERE 子句规定哪条记录或者哪些记录需要删除，如果你省略了 WHERE 子句，所有的记录都将被删除！



### 演示数据库

下面是选自 "**Websites**" 表的数据：

```sql
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+

```



### SQL DELETE 实例

假设我们要从 Websites 表中删除网站名称为 Facebook 且国家为 USA 的网站

我们使用一下 SQL 语句：

实例：

```sql
DELETE FROM Websites
WHERE name = 'Facebook' AND country = 'USA';
```

输出结果：

![ https://www.runoob.com/wp-content/uploads/2013/09/BD5EFB9A-2A65-4AF8-81F3-022E051811DC.jpg](https://www.runoob.com/wp-content/uploads/2013/09/BD5EFB9A-2A65-4AF8-81F3-022E051811DC.jpg)



### 删除所有数据

你可以在不删除表的情况下，删除表中所有的行。这意味着表结构、属性、索引将保持不变：

```sql
DELETE FROM table_name;
```

> **注释**：在删除记录时要格外小心！因为你不能重来！



------



# SQL 高级教程



## SQL SELECT TOP

SELECT TOP 语句用于在 SQL 中限制返回的结果集中的行数，它通常用于值需要查询前几行数据的情况，尤其在数据集非常大时，可

































































































































































































































