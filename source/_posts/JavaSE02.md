---
title: Java SE 基础系列笔记 (2)
date: 2020-02-21 21:49:32
tags: inherit
categories: Java
---
## 描述

继承相关练习： 发红包案例

<!-- more -->

## 要求

群主发普通红包。某群有多名成员，群主给成员发普通红包。普通红包的规则：

1. 群主的一笔金额，从群主余额中扣除，平均分成n等份，让成员领取。
2. 成员领取红包后，保存到成员余额中。

请根据描述，完成案例中所有类的定义以及指定类之间的继承关系，并完成发红包的操作。

## 实现

```java
package com.demo01;

/**
 * @ClassName: User
 * @Description: ToDo
 * @author: Aimer
 * @date: 2020/2/15  21:36
 * version: 1.0
 */
public class User {
    private String name;
    private  int money;

    public User() {
    }

    public User(String name, int money) {
        this.name = name;
        this.money = money;
    }

    public void show(){
        System.out.println("我是"+ name + ",我有多少钱："+ money);
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getMoney() {
        return money;
    }

    public void setMoney(int money) {
        this.money = money;
    }
}


```

```java
package com.demo01;

import java.util.ArrayList;

/**
 * @ClassName: Manager
 * @Description: 群主类
 * @author: Aimer
 * @date: 2020/2/15  21:39
 * version: 1.0
 */
public class Manager extends User {
    public Manager(){
    }

    public Manager(String name, int money) {
        super(name, money);
    }

    //totalMoney 总共发的红包 count 为份数
    public ArrayList<Integer> send(int totalMoney, int count){
        //首先需要一个集合，用来存储若干个红包的金额
        ArrayList<Integer> redList = new ArrayList<>();

        //看下群主自己的钱够不够
        int leftMoney = super.getMoney();//群主当前余额
        if (totalMoney>leftMoney){
            System.out.println("余额不足");
            return  redList;//空集合
        }

        //扣钱（包括将最后除不尽余下的钱加到集合最后一个里）
        super.setMoney(leftMoney-totalMoney);
        int avg = totalMoney/count;
        int mod =totalMoney%count;
        for (int i = 0; i < count-1; i++) {
            redList.add(avg);
        }
        int last = avg+mod;//最后一个红包
        redList.add(last);
        return  redList;
    }
}

```

```java
package com.demo01;
import java.util.ArrayList;
import java.util.Random;

/**
 * @ClassName: Member
 * @Description: 成员类
 * @author: Aimer
 * @date: 2020/2/15  21:42
 * version: 1.0
 */
public class Member extends User {
    public Member() {
    }

    public Member(String name, int money) {
        super(name, money);
    }

    public  void receive(ArrayList<Integer> list){
        //从多个红包中随便取一个红包（一个集合中的索引值）
        int index = new Random().nextInt(list.size());
        //根据索引从集合中删除，得到红包
        int delta = list.remove(index);
        //当前成员自己本来有多少钱
        int money = super.getMoney();
        super.setMoney(money+delta);
    }
}
```

```java
package com.demo01;

import java.util.ArrayList;

/**
 * @ClassName: LucyRed
 * @Description: 实现发红包案例
 * @author: Aimer
 * @date: 2020/2/15  21:44
 * version: 1.0
 */
public class LucyRed {
    public static void main(String[] args) {
        Manager manager = new Manager("群主",100);
        Member one = new Member("成员A",0);
        Member two = new Member("成员B",0);
        Member three = new Member("成员C",0);
// 打印初始红包金额
        manager.show();
        one.show();
        two.show();
        three.show();
        System.out.println("================");

        //群主发红包啦
        ArrayList<Integer> redList = manager.send(20,3);
        //成员收红包
        one.receive(redList);
        two.receive(redList);
        three.receive(redList);

        manager.show();
        one.show();
        two.show();
        three.show();
    }
}

```

## 运行

![demo01luckred.png](https://i.loli.net/2020/02/16/ojdO5aGtEnYuNHI.png)

