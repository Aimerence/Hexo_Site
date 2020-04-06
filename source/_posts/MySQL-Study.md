---
title: MySQL 学习笔记（1）
article-thumbnail: false
keywords: [MySQL]
top: 100
toc: true
tags: [mysql]
date: 2020-03-23 22:48:58
thumbnail:
categories: MySQL
---

开始学习 MySQL 数据库
<!-- more -->

## 启动/关闭

**管理员权限下运行cmd  :**
`net start mysql`
`net stop mysql`

## 登录/退出

`mysql -uroot -proot`

> `root` 为个人设置的用户名和密码

`mysql -hip -uroot -ppassword`

> `ip`  为远程主机 ip , `password` 为其数据库登入密码

使用 ` exit ` 或 `quit`  退出

## SQL
**SQL (Structured Query Language): 结构化查询语言**

定义了操作所有**关系型**数据库的规则。

### 通用语法

1. 不区分大小写，以分号结尾，关键字建议大写。

2. 注释有三种： 
```sql
单行注释： -- 注释内容   或 # 注释内容 (mysql 特有)
多行注释： /* 注释内容 */
```

###  SQL分类

```sql
DDL(Data Definition Language)数据定义语言:
定义数据库对象：【数据库，表】，列等关键字：create, drop,alter 等

DML(Data Manipulation Language)数据操作语言:
用来对数据库中表的数据进行【增删改】。关键字：insert, delete, update 等

DQL(Data Query Language)数据查询语言:
用来【查询】数据库中表的记录(数据)。关键字：select, where 等

DCL(Data Control Language)数据控制语言(了解):
用来定义数据库的【访问权限和安全级别】，及创建用户。关键字：GRANT， REVOKE 等

```
### DDL ：操作数据库、表

#### 操作数据库：CRUD
- **C(Create) : 创建**
- **R(Retrieve) : 查询**
- **U(Update)：修改**
- **D(Delete): 删除**
- **使用数据库**

---


```mysql
创建数据库： create database 数据库名称
创建数据库，判断不存在，在创建： create database if not exists 数据库名称;
查询所有数据库的名称： show databases;
查询某个数据库的字符集/创建语句： show create database 数据库名称;
创建db4数据库，判断是否存在，并制定字符集为gbk: create database if not exists db4 character set gbk;
修改某个数据库字符集(假设改为gbk)： alter database db1 character set gbk;
删除数据库： drop database db5;
判断是否存在，再删除： drop database if exists db5;
查询当前使用的数据库名称： select database();
使用数据库： use 数据库名称

```
#### 操作数据库表：CRUD
```mysql
查询某个数据库中的所有表名称： show tables;
查询表结构： desc 表名
创建表： create table 表名{
			列名1 数据类型1，
			列名2 数据类型2，
			...
			列名3 数据类型3
		}；
		
		
/*  
   int：整数类型    age int
    double: 小数类型 score double(5,2)
    date: 日期，只包含年月日时分秒 yyyy-MM-dd-HH:mm:ss
    timestamp: 时间错类型 同上 未赋值或null 默认使用系统时间
    varchar:字符串  name varchar(20) 姓名最大20个字符
*/

范例如下：
    create table student(
                    id int,
                    name varchar(32),
                    age int ,
                    score double(4,1),
                    birthday date,
                    insert_time timestamp
                );
                
删除表： drop table 表名；
判断删除表： drop table if exists 表名；
复制表内容到新表： create table 新表名 like 旧表名；
修改表名：alter table 表名 rename to 新表名;
修改表字符集：alter table 表名 character set 字符集名称；
添加一列： alter table 表名 add 列名 数据结构；
修改列名称 类型： alter table 表名 change 列名 新列名 新数据类型;
或者： alter table 表名 modify 列名 新数据类型；
删除列: alter table 表名 drop 列名；
```

```sql
添加数据： insert into 表名（列名1，列名2，..列名n） values(值1，值2，..值n)；
删除数据： delete from 表名 where 条件;
删除数据表： delete from 表名；不推荐
删除数据表： TRUNCATE TABLE 表名; //删除表，创建一张一样的空表
修改数据： update 表名 set 列名1=值1，列名2=值2，... where 条件；

```




