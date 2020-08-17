---
title: Java SE 基础系列笔记 (1)
date: 2020-02-21 21:05:36
tags: basic
toc: true
categories: Java
article-thumbnail: false
---
开启 JAVA 学习之旅
<!-- more -->

## IDEA常用快捷键

| 快捷键         | 功能                                         |
| :------------- | -------------------------------------------- |
| Alt+4          | 打开程序运行窗口                             |
| Alt+Enter      | 导入包，自动修正代码                         |
| Ctrl+Y         | 删除光标所在行                               |
| Ctrl+D         | 复制光标所在行的内容到下一行                 |
| Ctrl+Alt+L     | 格式化代码                                   |
| Ctrl+/         | 单行注释，再按取消注释                       |
| Ctrl+Shift+/   | 选中代码注释，多行注释 ，再按取消注释        |
| Alt+Ins        | 自动生成代码，toString，get，set等方法       |
| Alt+Shift+上下 | 移动当前代码行                               |
| Shift+f6       | 重构-重命名 (包、类、方法、变量、甚至注释等) |

## IDEA代码自动补全

| 代码缩写    | 代码补全                                        |
| ----------- | ----------------------------------------------- |
| psvm        | public static void main(String[] args) {      } |
| 循环数.fori | for (int i = 0; i < 循环数; i++) {      }       |
| sout        | System.out.println();                           |

## 基础语法小记

1. 成员变量是直接定义在类中的，在成员方法外边。
2. 成员方法不要写 static 关键字。
3. 当一个对象作为参数，传递到方法当中时，传递的是对象的地址值。
4. 对于基本类型中的 boolean 值，Getter 方法一定要写成 isXxx 的形式，而 SetXxx 规则不变。
5. 对于 Private 成员变量，通过类成员方法间接访问。
6. 当方法的局部变量和类的成员变量重名的时候，就近优先使用局部变量。如需访问类成员变量，使用 this.成员变量名。
7. 通过堆调用的方法，谁就是 this 。
8. Java Bean （满足四要求）
9. 通过 super.成员变量名/方法  访问父类成员变量/方法。
10. 重写/覆盖/覆写（Override)  与重载（Overload）区别在于参数列表是否一样。
11. 可以通过写 @Override 来安全检测方法是不是有效的正确覆盖重写。
12. Overrid (重写)注意事项：子类方法的返回值必须小于等于父类方法的返回值范围。【Object类是所有类的公共最高父类】子类方法的权限必须大于等于父类方法的权限修饰符。【public > protected > (default) >private】
13. 继承中，子类构造方法默认隐含 “super()"调用，子类对象先调用父类构造，后执行子类构造。子类构造可以通过super关键字调用父类重载构造（必须是子类构造方法的第一个且唯一的语句)。
14. super 和 this 两种构造调用，不能同时使用。
15. 使用抽象类和抽象方法：不能直接创建 new 抽象类对象；必须用一个子类来继承抽象父类；子类必须覆盖重写抽象父类当中的抽象方法（去掉 abstract 关键字，补上方法体大括号）。
16. 在子类 extend 关键字上，通过 alt+ Enter ,实现抽象类方法的覆写。
17. 使用 Alt + Insert 调用方法。【注意：很多电脑F12和Insert是同一个键，所以 Alt+Insert 和 Alt+F12 是冲突的，当我们按下 Alt+Insert 的时候其实触动的是 Alt+F12，大家应该知道想要触动Insert得用到 Fn(功能键)+Insert，所以想要触动 Alt+Insert 就得是 Fn(功能键)+Alt+Insert 才行】