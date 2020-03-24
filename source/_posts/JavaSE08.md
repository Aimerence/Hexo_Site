---
title: Java SE 基础系列笔记 (8)
article-thumbnail: false
keywords: [Java,Collection]
top: 100
toc: true
tags: [collection]
date: 2020-03-12 18:07:14
thumbnail:
categories: Java
---
Java 集合（Collection）学习
<!-- more -->

## Collection 概述

Collection 单列集合类的跟接口，用于存储一系列符合某种规则的元素，包括 java.util.List 与 java.util.Set。

其中，list 特点是元素有序、元素可重复、存储有序，而set 特点是元素无序，不可重复，存储无序。

下面前三为 List 接口实现类，后三是 Set 接口实现类。

### Vector

略

### ArrayList （重点）

底层数组实现，查询块、增删慢

### LinkedList 

底层链表实现，查询慢，增删块

###  TreeSet 

底层二叉树实现，一般用于排序

### HashSet （重点）

底层哈希表+（红黑树）实现的，无索引、不可以存储重复元素、存取无序

### LinkedHashSet

底层哈希表+链表实现的，无索引、不可以存储重复元素、可以保存存取顺序

## Collection 常用方法

| 方法                   | 功能             |
| ---------------------- | ---------------- |
| boolean add(E e)       | 添加元素         |
| boolean remove(E e)    | 删除元素         |
| void clear()           | 清空元素         |
| boolean contains(E e)  | 判断是否包含元素 |
| boolean isEmpty()      | 判断是否为空     |
| int size()             | 集合长度         |
| Object [ ] toArray（） | 集合转数组       |

**exp**

```java
package com.demo24;
import java.util.ArrayList;
import java.util.Collection;
public class demo23 {
    public static void main(String[] args) {
        Collection<String> coll = new ArrayList<>();
        coll.add("hello");
        coll.add("hello");
        coll.add("sb");
        coll.add("sb");
        coll.add("sb");
        System.out.println(coll); //[hello, hello, sb, sb, sb]
        coll.remove("sb");
        coll.remove("sb");
        System.out.println(coll);
        boolean result = coll.remove("sb");
        System.out.println(result);
        coll.clear();
        System.out.println(coll);
        coll.add("hero");
        coll.add("hero");
        coll.add("hero");
        System.out.println(coll.contains("her"));
        System.out.println(coll.isEmpty());
        System.out.println(coll.size());
        Object[] arr = coll.toArray();
        for (Object o : arr) { //jdk1.5新特性
            System.out.println(o);
        }
    }
}
//   [hello, hello, sb, sb, sb]
//        [hello, hello, sb]
//        true
//        []
//        false
//        false
//        3
//        hero
//        hero
//        hero


```





## Iterator 迭代器

   - boolean hasNext() 如果仍有元素可以迭代，则返回 true，没有返回 false。

   - E next() 返回迭代的下一个元素。

   - Collection 接口中 iterator()方法返回迭代器的实现类对象。

**exp**

```java
import java.util.ArrayList;
import java.util.Collection;
import java.util.Iterator;
public class demoIterator {
    public static void main(String[] args) {
        Collection<String> coll = new ArrayList<>();
        coll.add("刘亦菲");
        coll.add("刘诗诗");
        coll.add("刘德华");
        coll.add("刘德华");
        coll.add("admin");
        for (String s : coll) {
            System.out.println(s);
        }
        Iterator<String> it = coll.iterator();
        while (it.hasNext()){
            System.out.println(it.next());
        }
        System.out.println("--------");
        for(String s: coll){//增强for循环
            System.out.println(s);
        }
    }
}
/*
刘亦菲
刘诗诗
刘德华
刘德华
admin
刘亦菲
刘诗诗
刘德华
刘德华
admin
--------
刘亦菲
刘诗诗
刘德华
刘德华
admin
*/

```

