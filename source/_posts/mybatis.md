---
title: Mybatis学习记录总结
article-thumbnail: false
keywords: [mybatis]
toc: true
tags: [mybatis]
date: 2020-07-20 14:17:06
thumbnail:
categories: Java
---
Mybatis 为持久层框架，封装了jdbc操作的很多细节，使用了 ORM 的思想实现结果集的封装。
<!-- more -->

    ORM(Object Relational Mapping 对象关系映射)：把数据库表和实体类及其属性对应起来，操作实体类来达到操作数据库表


## 三层架构
![三层架构](https://cdn.jsdelivr.net/gh/Aimerence/picBed/program/三层架构.png)



## 创建例表 user

```mysql
CREATE TABLE user (
  id int(11) NOT NULL AUTO_INCREMENT,
  username varchar(32) NOT NULL COMMENT '用户名称',
  birthday datetime DEFAULT NULL COMMENT '生日',
  sex char(1) DEFAULT NULL COMMENT '性别',
  address varchar(256) DEFAULT NULL COMMENT '地址',
  PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

## 插入数据
```mysql
 insert into user(id,username,birthday,sex,address) values ('57','张三','2020-07-01 10:25:42','男','法外'):
 insert into user values ('66','AIMER','2020-07-02 10:25:42','女','日本');
//后续我直接用sqlyog可视化软件编辑
```

