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

## 后台总路线（要学的不止这些）
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


# Mysql数据库忘记密码
    mysql bin目录cmd 运行mysqld --skip-grant-tables（确保已经停止mysql.exe服务) 
    再cmd  mysql无需密码登入use mysql;
    select user,host,password from user; 来查看账户信息 
    更改root密码，输入update user set password=password('123456') where user='root' and host='localhost';

# idea中文乱码解决方案
    file->settings->appearence 里面有个Name设置成支持中文的字体
    settings中的Eidtor->File Encodings里面设置字体编码格式，一般都是UTF-8，GBK什么的也行
    找到idea安装目录bin目录下如下图所示两个文件，用编辑器打开
    在文件末尾添加 -Dfile.encoding=UTF-8 ，然后重启idea 
    再打流程图就会发现中文已经可以正常显示了

# idea启动springboot项目报错
    报错信息如下：
    Error running 'AuthApplication': Command line is too long. 
    Shorten command line for AuthApplication or also for Spring Boot default configuration.
    解决办法：在.idea文件夹下面的workspace.xml中的 <component name="PropertiesComponent">标签下面
    添加： <property name="dynamic.classpath" value="true"/> 即可


# Maven项目依赖报错

....



