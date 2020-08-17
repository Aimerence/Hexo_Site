---
title: 实习工作中遇到的坑
article-thumbnail: false
keywords: [pit]
toc: true
tags: [bug,problem]
date: 2020-07-03 22:50:48
thumbnail:
categories: Java
---
记录实习工作中写代码遇到的一些问题及解决方法
<!-- more -->

## 后台总路线
- JAVA
- Spring SpringMVC Mybatis
- SpringBoot
- SpringCloud
- Tomcat/Servlet
- MySql/Oracle
- Maven
- Redis
- Nginx
- docker


## 数据库查询表内容显示乱码（cmd中）
    cmd 默认字符编码为 gbk
    chcp 65001 切换为UTF-8
    chcp 936 切换为gbk


## PLSQL 无法查询中文条件
    字符编码问题
    新增环境变量 NLS_LANG；
    变量值：AMERICAN_AMERICA.AL32UTF8



## Mysql 数据库无法输入( 插入）和无法显示中文
    将 Mysql安装目录的 my.ini 文件中 default-character-set=utf8（如果不是）
    再 mysql命令行中运行以下命令（已有可不用设置）：// 通过 show variables like'%char% 查看
    set character_set_database=utf8;
    set character_set_server=utf8;
    set character_set_client=gbk;
    set character_set_connection=gbk; 
    set character_set_results=gbk




