---
title: Java SE 基础系列笔记 (6)
date: 2020-02-27 21:07:02
categories: Java
tags: api
toc: true
comment: true
---

常用 JAVA API(一) 学习

<!-- more -->

## Scanner

exp:

```java
package com.demo09;
import java.util.Scanner;
public class demoScn {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int num = sc.nextInt();
        String str =  sc.next();
        System.out.println(num+str);
    }
}
```

## 匿名对象

exp:

```java
package com.demo09;

import java.util.Scanner;

public class demoNum {
    public static void main(String[] args) {
        methodParam(new Scanner(System.in));
        
        Scanner sc = methodReturn();
        int num = sc.nextInt();
        System.out.println("hhajfi");

    }

    // 匿名对象作为方法参数
    public static void methodParam(Scanner sc) {
        int num = sc.nextInt();
        System.out.println(num);
    }
    // 匿名对象作为返回值
    public static  Scanner methodReturn(){
        return new Scanner(System.in);
    }
}

```

##  Random

exp:

```java
import java.util.Random;

public class demoRan {
    public static void main(String[] args) {
        Random r = new Random();
        int num  = r.nextInt();
        System.out.println(num);
    }
}
```

**注意：使用 `nextInt(n)` 为左闭右开区间。**

### 猜数字小游戏

```java
package com.demo10;
import java.util.Random;
import java.util.Scanner;

//猜数字游戏

public class demoGame {
    public static void main(String[] args) {
        Random r = new Random();
        int randomNum = r.nextInt(100) + 1;//[1,100]
        Scanner sc = new Scanner(System.in);

        while (true) {
            System.out.println("请输入：");
            int guessNum = sc.nextInt();

            if (guessNum < randomNum) {
                System.out.println("小了");
            } else if (guessNum > randomNum) {
                System.out.println("大了");
            } else {
                System.out.println("中了");
                break;
            }
        }
        System.out.println("Over!!!");
    }
}
```

## ArrayList

**`ArrayList(集合)` 的长度是可以随意变化的。**

**`ArrayList<E>`  其中 E 为泛型，只能是引用类型。**

exp:

```java
import java.util.ArrayList;
public class demoARRM {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        list.add("李白");
        list.add("张飞");
        list.add("伽罗");
        list.add("干将");

        System.out.println(list);
        System.out.println(list.get(1));
        String whoRemoved = list.remove(2);
        System.out.println(whoRemoved);

        int size = list.size(); //获取长度
        System.out.println(size);
    }
}
```

```java
import java.util.ArrayList;
public class ArrayListeach {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        list.add("A");
        list.add("B");
        list.add("C");
        list.add("D");
        for (int i = 0; i < list.size(); i++) {
            System.out.println(list.get(i));
        }
    }
}
```



**存储基本类型：使用包装类（大写）**

**注意：**  `Integer`  `character`

## String

**字符串是常量,效果上相当于 `char[]`字符数组，但是底层原理是`byte[]`字节数组。**

### 三种构造方法以及直接创建

```java
public String()
public String(char[] array)
public String(byte[] array)
String str1 = "hello"
```



exp:

```java
package com.demo14字符串;

public class DemoStr {
    public static void main(String[] args) {
        String str1 = new String();

        char[] charArray = {'a','b','c'};
        String str2 = new String(charArray);

        byte[] byteArray = {97,98,99};
        String str3 = new String(byteArray);

        String str4 = "hello";

        System.out.println(str1 + str2 + str3 + str4);
    }
}

```



**注意：**

- **使用 `==`比较的是对象的地址值，要用 ` a.equals(b)` 比较字符串内容。**

- **最好用 `常量.equals(变量)`，不然会报空指针异常错误**

- **使用 ` equalsIgnoreCase` 忽略大小写。**

  

  ### **`String`  当中与获取相关的常用方法** 

  

| 用法                             |                            含义                            |
| :------------------------------- | :--------------------------------------------------------: |
| public int length()              |        获取字符串当中含有的字符个数，拿到字符串长度        |
| public String concat(String str) |      将当前字符串和参数字符串拼接成为返回值新的字符串      |
| public charAt(int index)         |                 获取指定索引位置的单个字符                 |
| public int indexOf(string str)   | 查找参数字符串在本字符串当中首次出现的索引位置，无返回-1值 |

 ### 字符串截取



| 截取参数                                   |                     效果                      |
| ------------------------------------------ | :-------------------------------------------: |
| public String substring(int begin,int end) | 截取从begin 开始，一直到end结束，中间的字符串 |
| public String substring(int index)         | 截取从参数位置一直到字符串末尾，返回新字符串  |



### 字符串转换



|                             方法                             |                             效果                             |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
|                 public char[] toCharArray()                  |            将当前字符串拆分成为字符数组作为返回值            |
|                   public byte[] getBytes()                   |                 获得当前字符串底层的字节数组                 |
| public String replace(CharSequence oldString,CharSequence newString) | 将所有出现的老字符串替换成为新的字符串，返回替换之后的结果新字符串 |

### 字符串分割

**按照参数规则将字符串分成若干部分：**

`public String split(String regex) `

**注意事项： regex 为正则，要按原文句点 `.` 进行划分，必须写  ` \\.` 。**



## static

**无论是成员变量还是成员方法，如果有了 `static`, 推荐使用类名称进行调用。**

**注意： 静态不能访问非静态**

原因：因为在内存当中是先有静态内容，后有非静态内容。

**注意： 静态方法中不能使用 `this`**

原因： `this` 代表当前对象，通过谁调用的方法，谁就是当前对象。



### 静态代码块 

````java
public class 类名称{
    static {}
}
````

**特点：当第一次用到本类时，静态代码执行唯一的一次，比构造方法先执行。**

## Arrays

| 方法                                | 效果                         |
| ----------------------------------- | ---------------------------- |
| public static String toString(数组) | 将参数数组变成字符串         |
| public static void sort(数组)       | 按照生序对数组的元素进行排序 |

**备注：**

* 如果是数值，sort 默认按照升序从小到大。

* 如果是字符串，sort 默认按照字母升序。

* 如果是自定义的类型，那么这个自定义的类需要有Comparable 或者Comparator 接口的支持（今后学习）

  

## Math



| 方法                                   | 效果       |
| :------------------------------------- | ---------- |
| public static double abs(double num)   | 获取绝对值 |
| public static double ceil(double num)  | 向上取整   |
| public static double floor(double num) | 向下取整   |
| public static double round(double num) | 四舍五入   |

**备注：**

Math.PI 代表近似圆周率 （double)

###  Math 小练习

**要求：**

> 计算 -10.8 到 5.9 之间，绝对值大于 6 或者小于 2.1 的整数有多少个？



**分析：**

1. 既然已经确定了范围，用 for 循环。

2. 起点位置 -10.8 应该转换成为 -10，两种方法：

   2.1 可以使用 Math.ceil 方法，向上（向正方向）取整。

   2.2 强制转换为 int ,自动舍弃所有小数位。

3. 每一个数字都是整数，所以步进表达式应该是 num ++,这样每次都是 +1的。

4. 如何拿到绝对值，用 Math.abs 方法。

5.  一旦发现了应该数字，需要让计数器 ++ 进行统计。

**备注：**

如果使用 Math.ceil 方法， -10.8 可以变成 -10.0 . 注意 double 也是可以进行 ++ 的。

**exp :**

```java
public class DemoMath {
    public static void main(String[] args) {
        int count = 0;
        double min = -10.8;
        double max = 5.9;
        for(int i = (int) min;i<max;i++){
            int abs = Math.abs(i);
            if(abs> 6||abs<2.1){
                System.out.println(i);
                count++;
            }
        }
        System.out.println("All:"+count);
    }
}
```

