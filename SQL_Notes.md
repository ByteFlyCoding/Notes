---
title: "SQL"
date: 2021-04-09T20:13:52+08:00
draft: false
tags: ["SQL", "DB"]
categories: ["DataBaseSystem"]
---

# SQL_Notes

## 当今的数据处理可以分为两大类：

* OLTP(On-Line transaction processing):联机事务处理：OLTP 是传统关系型数据库的主要应用
用来执行一些基本的、日常的事务处理
比如数据库记录的增、删、改、查等等
* OLAP(On-Line Analytical Processing):联机分析处理

## SQL语言按照功能划分为以下的4个部分

1. DDL(Data Definition Language)
2. DML(Data Manipulation Language)
3. DCL(Data Control Language)
4. DQL(Data Query Language)

## SQL大小写问题：

* 表名、表别名、字段名、字段别名等都要小写
* SQL保留字、函数名、绑定变量等都要大写
* 此外在数据表的字段名推荐采用下划线命名

## DB DBS DBMS的区别是什么

* DBMS = 多个数据库（DB） + 管理程序
* DB是存储数据的集合，你可以把它理解为多个数据表
* DBS包括了数据库、数据库管理系统以及数据库管理人员 DBA

## DDL(Data Definition Language)

1. 对数据库进行定义

   ```sql
   CREATE DATABASE <DataBaseName>;
   DROP DATABASE <DataBaseName>;
   ```

2. 对数据表进行定义

   ```sql
   CREATE TABLE <Table_Name>;
   ```

3. 创建表结构

   ```sql
   -- eg.
   CREATE TABLE player  (
     player_id int(11) NOT NULL AUTO_INCREMENT,
     player_name varchar(255) NOT NULL
   );
   -- 类型中 int(11) 代表整数类型，显示长度为 11 位，括号中的参数 11 代表的是最大有效显示长度，与类型包含的数值范围大小无关。
   -- NOT NULL表明整个字段不能是空值，是一种数据约束。AUTO_INCREMENT代表主键自动增长。
   ```

4. 导出表结构

   ```sql
   DROP TABLE IF EXISTS `player`;
   CREATE TABLE `player`  (
     `player_id` int(11) NOT NULL AUTO_INCREMENT,
     `team_id` int(11) NOT NULL,
     `player_name` varchar(255) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL,
     `height` float(3, 2) NULL DEFAULT 0.00,
     PRIMARY KEY (`player_id`) USING BTREE,
     UNIQUE INDEX `player_name`(`player_name`) USING BTREE
   ) ENGINE = InnoDB CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;
   -- 里面的数据表和字段都使用了反引号，这是为了避免它们的名称与 MySQL 保留字段相同，对数据表和字段名称都加上了反引号
   -- 字符集是 utf8，排序规则是utf8_general_ci，代表对大小写不敏感，如果设置为utf8_bin，代表对大小写敏感
   ```

5. 修改表结构

   * 添加字段

   ```sql
   ALTER TABLE player ADD (age int(11));
   ```

   * 修改字段名

   ```sql
   ALTER TABLE player RENAME COLUMN age to player_age
   ```

   * 修改字段的数据类型

   ```sql
   ALTER TABLE player MODIFY (player_age float(3,1));
   ```

   * 删除字段

   ```sql
   ALTER TABLE player DROP COLUMN player_age;
   ```

6. 数据表常见约束

   * 主键约束：主键起的作用是唯一标识一条记录，不能重复，不能为空，即 UNIQUE+NOT NULL。一个数据表的主键只能有一个。主键可以是一个字段，也可以由多个字段复合组成。
   * 外键约束：外键确保了表与表之间引用的完整性。一个表中的外键对应另一张表的主键。外键可以是重复的，也可以为空。
   * 唯一性约束
   * NOT NULL 约束：对字段定义了 NOT NULL，即表明该字段不应为空，必须有取值。
   * DEFAULT约束：表明了字段的默认值。如果在插入数据的时候，这个字段没有取值，就设置为默认值。
   * CHECK 约束：用来检查特定字段取值范围的有效性，CHECK 约束的结果不能为 FALSE

7. 数据库设计原则
我们在设计数据表的时候，经常会考虑到各种问题，比如：
* 用户都需要什么数据？

* 需要在数据表中保存哪些数据？

* 哪些数据是经常访问的数据？

* 如何提升检索效率？

* 如何保证数据表中数据的正确性，当插入、删除、更新的时候该进行怎样的约束检查？

* 如何降低数据表的数据冗余度，保证数据表不会因为用户量的增长而迅速扩张？

* 如何让负责数据库维护的人员更方便地使用数据库？

  除此以外，我们使用数据库的应用场景也各不相同，可以说针对不同的情况，设计出来的数据表可能千差万别。我们可以遵守以下原则------“**三少一多**”原则：
  1. 数据表的个数越少越好：RDBMS 的核心在于对实体和联系的定义，也就是 E-R 图（Entity Relationship Diagram），数据表越少，证明实体和联系设计得越简洁，既方便理解又方便操作。
  2. 数据表中的字段个数越少越好：字段个数越多，数据冗余的可能性越大。设置字段个数少的前提是各个字段相互独立，而不是某个字段的取值可以由其他字段计算出来。当然字段个数少是相对的，我们通常会在数据冗余和检索效率中进行平衡。
  3. 数据表中联合主键的字段个数越少越好：设置主键是为了确定唯一性，当一个字段无法确定唯一性的时候，就需要采用联合主键的方式（也就是用多个字段来定义一个主键）。联合主键中的字段越多，占用的索引空间越大，不仅会加大理解难度，还会增加运行时间和索引空间，因此联合主键的字段个数越少越好。
  4. 使用主键和外键越多越好：数据库的设计实际上就是定义各种表，以及各种字段之间的关系。这些关系越多，证明这些实体之间的冗余度越低，利用度越高。这样做的好处在于不仅保证了数据表之间的独立性，还能提升相互之间的关联使用率。

  “三少一多”原则的核心就是简单可复用。简单指的是用更少的表、更少的字段、更少的联合主键字段来完成数据表的设计。可复用则是通过主键、外键的使用来增强数据表之间的复用率。因为一个主键可以理解是一张表的代表。键设计得越多，证明它们之间的利用率越高。



















参考：

[《SQL必知必会》]()

[《MySQL实战45讲》]()