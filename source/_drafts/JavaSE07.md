---
title: Java SE 基础系列笔记 (7)
article-thumbnail: false
keywords: [JAVA]
top: 100
toc: true
tags: [api]
date: 2020-03-09 21:19:02
thumbnail:
categories: Java
---

常用 JAVA API 学习 （二）
<!-- more -->

## Object类

###  toString 重写

打印对象中的属性值

### equals 重写

比较对象属性值

**注意：**

用对象工具类 objects.equals() 比较更加健壮。

**exp**

```java
package com.demo18;
import com.demo17.Student;
import java.util.Objects;
public class RT {
    public static void main(String[] args) {
        Student stu1 = new Student("lsk",12);
        Student stu2 = new Student("lsk",12);
        System.out.println(stu1.equals(stu2));// 重写 equals

        String a = "aaa";
        String b = null;
//        System.out.println(b.equals(a));//空指针不能调用方法
        System.out.println(Objects.equals(a,b));
    }
}

```

```java
package com.demo17;
import java.util.Objects;
public class Student {
    private String name;
    private  int  age;

    public Student() {
    }

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

// 覆写 toString
    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
// 覆写 equals
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Student student = (Student) o;
        return age == student.age &&
                Objects.equals(name, student.name);
    }
}

```

## Date类

* 使用 System.currentTimeMillis() 获取距离时间原点的毫秒值

* 使用 .getTime() 效果同上

* 使用 Date( 参数l ) 带参数构造使毫秒转为日期

* 使用 toLocalString 根据本地格式转换日期对象

* 空参

  

```java
import java.util.Date;
public class demoDate1 {
    public static void main(String[] args) {
        Date date = new Date();
        System.out.println(date);

        Date d1 = new Date(0l);
        System.out.println(d1);

        Date d2 = new Date();
        System.out.println(d2.getTime());
        System.out.println(System.currentTimeMillis());
    }
}
```



## DateFormat 类

DateFormat 是日期/时间格式化子类的抽象类，不能直接使用，需要其子类   `SimpleDateFormat`  , 这个类需要一个模式（格式）来指定货解析的标准。

构造方法如下：

` public SimpleDateFormat(String pattern)`  

其中 pattern为日期时间的自定义格式。

**格式规则**:

| 标识字母（区分大小写） | 含义 |
| ---------------------- | ---- |
| y                      | 年   |
| M                      | 月   |
| d                      | 日   |
| H                      | 时   |
| m                      | 分   |
| s                      | 秒   |

使用 SimpleDateFormat 的 format 方法按照指定模式，把日期格式化符合模式的字符串。

使用其 parse 方法把符合模式的字符串，解析为 Date 日期。

**exp:**

```java
package com.demo20;
import sun.security.provider.Sun;

import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;

public class demoD {
    public static void main(String[] args) throws ParseException {
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日HH时mm分ss秒");
        Date date = new Date();
        System.out.println(date);
        System.out.println(sdf.format(date));

        Date date1 = sdf.parse("2020年03月08日19时59分42秒");
        System.out.println(date1);
    }
}
//结果如下
/*      Sun Mar 08 20:40:03 CST 2020
        2020年03月08日20时40分03秒
        Sun Mar 08 19:59:42 CST 2020    
 */
```

### 小练习：粗略计算年龄 

```java
package com.demo21;

import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Scanner;
//粗略计算年龄
public class DemoMath {
    public static void main(String[] args) throws ParseException {
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入您的出生日期:（格式为 yyyyMMdd)");
        String receiveDate = sc.next();
        SimpleDateFormat sdf= new SimpleDateFormat("yyyyMMdd");
        Date birthdayDate = sdf.parse(receiveDate);
        long brthdayDateTime = birthdayDate.getTime();
        long todayTime = new Date().getTime();
        System.out.println((todayTime - brthdayDateTime)/1000/60/60/24/365);
    }
}

```

## Calendar

Calendar类为抽象类，提供了很多操作日历字段的方法，使用其静态方法 `getInstance()`返回子类对象。

| 成员方法                  | 作用                             |
| ------------------------- | -------------------------------- |
| int get(int n)            | 获取指定日历字段信息             |
| void set(int n,int value) | 将指定日历字段设置为指定的值     |
| void add(int n,int value) | 将指定日历字段增加或减少指定的值 |
| Date getTime()            | 转换为 Date 对象                           |

## System

- ` public  static long currentTimeMills()`： 返回以毫秒为单位的当前时间。

-  ` public static void arraycopy(Object src,int srcPos,Object dest,int destPos,int length)`: 将数组中指定的数据拷贝到另一个数组中。

  

## StringBuilder（**字符串缓冲区**）



### 构造方法

- **public StringBuilder()**:构造一个空的容器。

- **public StringBuilder(String str)**: 构造一个StringBuilder容器，并将字符串添加进去。



### 成员方法
- **public StringBuilder append()**:   添加容易类型的字符串形式，返回当前对象自身（可链式编程）。

- **public StringBuilder reverse()**:   反转内容。

- **public  String  toString()**:  将当前 StringBuilder 对下转换为 String 对象。

  

## 包装类

### 装箱与拆箱

**装箱：把基本类型的数据包装到包装类中（基本类型的数据- >包装类）**

**拆箱：在包装类中取出基本类型的数据（包装类->基本数据类型）**

**exp:**

```java
public class demoBox {
    public static void main(String[] args) {
        //装箱
        //构造方法
        Integer in1 = new Integer(1);
        System.out.println(in1);
        Integer in2 = new Integer("1");
        System.out.println(in2);

        // 静态方法
        Integer in3 = Integer.valueOf(1);
        System.out.println(in3);
        Integer in4 = Integer.valueOf("1");
        System.out.println(in4);
        
        //拆箱
        int i = in1.intValue();
        System.out.println(i);
    }
}
```

##  自动装箱与自动拆箱（>JDK1.5)

```java
import java.util.ArrayList;

public class demoBoo {
    public static void main(String[] args) {
        //自动装箱
        Integer in = 1;//相当于 Integer in = new Integer(1)
        //自动拆箱
        in = in +2;

        ArrayList<Integer> list = new ArrayList<>();
        list.add(1);  //list.add(new Integer(1)
        int a = list.get(0);//list.get(0).intValue
    }
}
```



## 基本类型与字符串之间的转换

1. 直接 基本数据类型  +  ""（常用）
2. 使用 toString(value)、parseInt等（注意格式）