---
title: Java SE 基础系列笔记 (4)
date: 2020-02-21 22:02:59
tags: interface
categories: Java
---

JAVA 接口学习

<!-- more -->

## 接口方法定义

```java
package com.demo02;
// 接口是多个类的公共规范
// Java7 中接口中可包含常量、抽象方法
// Java8 中额外可包含默认方法、静态方法
// Java9 中额外可包含私有方法
// 私有方法包括普通私有方法和静态私有方法
// 前者解决多个默认方法之间重复代码问题(接口中关键字为 private )
// 后者解决多个静态方法之间重复代码问题(接口中关键字为 private  static)
// 接口中的共有方法不应该让实现类使用（Java8 无法展示，代码略）
// 接口中的常量要使用大写，用下划线分隔且必须赋值关键字

public interface MyInterface {
    //常量
    public  static final  String  NUM_OF_CLASS = "接口常量执行";//public static final 可以省略

    // 抽象方法
    public abstract void AbsMethod01();// public abstract 可不写
    void AbsMethod02();
    
    // 默认方法
    public default void DefalutMethod01(){
        System.out.println("默认方法01执行");
    }
    public default void DefalutMethod02(){
        System.out.println("默认方法02执行");
    }

    // 静态方法
    public static  void StaticMethod(){
        System.out.println("静态方法不能通过实现类调用");
    }
}
```



## 接口方法实现

```java
package com.demo02;

// 接口的实现类

// 接口不能直接使用，必须有一个实现类来实现该接口
// 接口的实现类必须覆盖重写（实现）接口中所有的抽象方法

// 注意事项：如果实现类并没有覆盖重写接口中所有的抽象方法，那么这个实现类自己就必须定义为抽象类（Abstract)
// 注意事项：不能通过接口实现类的对象来调用接口当中的静态方法，只能通过接口名称调用

public class InterfaceImp implements MyInterface {
    @Override
    public void AbsMethod01() {
        System.out.println("接口的第一个方法执行");
    }
    @Override
    public void AbsMethod02() {
        System.out.println("接口的第二个方法执行");
    }
    //默认方法01覆写，02未覆写
    @Override
    public void DefalutMethod01() {
        System.out.println("覆写了接口01的默认方法");
    }
}

```



```java
package com.demo02;

/**
 * @ClassName: InterfaceUse
 * @Description: 接口实现
 * @author: Aimer
 * @date: 2020/2/16  15:02
 * version: 1.0
 */
public class InterfaceUse {
    public static void main(String[] args) {
        InterfaceImp IImp = new InterfaceImp();
        IImp.AbsMethod01();
        IImp.AbsMethod02();
        System.out.println("==========");

        //如果接口实现类没有覆写接口的默认方法，将使用接口的默认方法
        IImp.DefalutMethod01();
        IImp.DefalutMethod02();

        // 接口静态方法调用
        MyInterface.StaticMethod(); //只能用接口名.方法调用

        //常量调用
        System.out.println(MyInterface.NUM_OF_CLASS);
    }
}
```

## 接口方法运行

![Interface.png](https://i.loli.net/2020/02/16/ypJ54SgKMXdezVN.png)

## 接口内容小结

**1.成员变量其实是常量，格式：** 

`[public] [static] [final] 数据类型 常量名称 = 数据值;`

**注意：常量必须进行赋值，而且一旦赋值不能改变。常量名称完全大写，用下划线进行分隔**

**2.接口中最重要的就是抽象方法，格式：** 

`[public] [abstract] 返回值类型 方法名称(参数列表);`

**注意：实现类必须覆盖重写接口所有的抽象方法，除非实现类是抽象类。**
　

**3.从Java 8开始，接口里允许定义默认方法，格式：**

`[public] default 返回值类型 方法名称(参数列表) { 方法体 }`

**注意：默认方法也可以被覆盖重写**。
　

**4.从Java 8开始，接口里允许定义静态方法，格式：**

`[public] static 返回值类型 方法名称(参数列表) { 方法体 }`

**注意：应该通过接口名称进行调用，不能通过实现类对象调用接口静态方法**。
　
**5.从Java 9开始，接口里允许定义私有方法，格式：**

**普通私有方法**：`private 返回值类型 方法名称(参数列表) { 方法体 }`

**静态私有方法**：`private static 返回值类型 方法名称(参数列表) { 方法体 }`

**注意：private的方法只有接口自己才能调用，不能被实现类或别人使用。**

## 实现多个接口


`public class MyInterfaceImpl implements MyInterfaceA, MyInterfaceB{}`

```java
一个类可以同时实现多个接口，但直接父类是唯一的
接口没有静态代码块后者构造方法
如果实现类所实现的多个接口当中，存在重复的抽象方法，那么只需要覆盖重写一次即可
如果实现类没有覆盖重写所有接口当中的所有抽象方法，那么实现类就必须是一个抽象类
如果实现类所实现的多个接口当中，存在重复的默认方法，那么实现类一定要对冲突的默认方法进行覆盖重写
一个类如果直接父类当中的方法，和接口当中的默认方法产生了冲突，优先用父类当中的方法
接口与接口之间是多继承的
多个父接口当中的默认方法如果重复，那么子接口必须进行默认方法的覆盖重写，【而且带着default关键字】
```

