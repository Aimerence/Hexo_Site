---
title: Java SE 基础系列笔记 (3)
date: 2020-02-21 22:02:51
tags:  polymorphism
categories: Java
---

JAVA 多态学习

<!-- more -->

## 多态格式

**多态：父类引用指向子类对象**

`父类名称 对象名 = new 子类名称 `

或者：

`接口名称 对象名 = new 实现类名称`



##  成员变量及方法使用

**在多态的代码当中，成员方法的访问规则是： 看 `new`的是谁，就优先用谁，没有就向上找。**

**成员变量，编译看左边，运行还看左边。**

**成员方法，编译看左边，运行看右边。**

## 对象的转型

### 向上转型

向上转型，就是多态写法。向上转型一定是安全的，从小范围转向大范围。

格式： `父类名称 对象名 = new 子类名称`

含义： 右侧创建一个子类对象，把它当做父类来看待使用。

### 向下转型

对象的向下转型，其实是一个还原的动作。

格式：`子类名称 对象名 = (子类名称) 父类对象`

含义： 将父类对象，还原为本来的子类对象。

**注意事项： 向下转型需要 `对象 instanceof 类名称`来判断前面的对象能不能当做后面类型的实例。**



## 笔记本 USB 接口实例

### USB

```java
package com.demo03;

/**
 * @ClassName: USB
 * @Description: USB接口
 * @author: Aimer
 * @date: 2020/2/17  19:54
 * version: 1.0
 */
public interface USB {
    public abstract void open();
    public abstract void close();
}

```

### Computer

```java
package com.demo03;

import java.security.Key;

/**
 * @ClassName: Computer
 * @Description: 计算机类
 * @author: Aimer
 * @date: 2020/2/17  19:56
 * version: 1.0
 */
public class Computer {
    public void powerOn(){
        System.out.println("笔记本开机");
    }
    public  void powerOff(){
        System.out.println("笔记本关机");
    }

    // 使用USB
    public void useDevice(USB usb){
        usb.open();
        if (usb instanceof Mouse){
            Mouse mouse = (Mouse) usb;//向下转型
            mouse.click();
        }else  if(usb instanceof Keyboard){
            Keyboard keyboard = (Keyboard) usb;//向下转型
            keyboard.type();
        }
        usb.close();
    }

}

```

### Mouse

```java
package com.demo03;

/**
 * @ClassName: Mouse
 * @Description: 鼠标
 * @author: Aimer
 * @date: 2020/2/17  20:03
 * version: 1.0
 */

//鼠标就是一个 USB 设备
public class Mouse implements USB {

    @Override
    public void open() {
        System.out.println("打开鼠标");
    }

    @Override
    public void close() {
        System.out.println("关闭鼠标");
    }

    public  void click(){
        System.out.println("鼠标点击");
    }
}

```

### Keyboard

```java
package com.demo03;

/**
 * @ClassName: Keyboard
 * @Description: 键盘
 * @author: Aimer
 * @date: 2020/2/17  20:42
 * version: 1.0
 */
//键盘也是个USB设备
public class Keyboard implements USB{

    @Override
    public void open() {
        System.out.println("打开键盘");
    }

    @Override
    public void close() {
        System.out.println("关闭键盘");
    }

    public  void  type(){
        System.out.println("键盘输入");
    }
}

```

### 实现

```java
package com.demo03;

/**
 * @ClassName: DemoC
 * @Description: 实现
 * @author: Aimer
 * @date: 2020/2/17  20:05
 * version: 1.0
 */
public class DemoC {
    public static void main(String[] args) {
        Computer computer = new Computer();
        computer.powerOn();

        // 多态写法
        USB usbMouse = new Mouse(); // 左父右子
        computer.useDevice(usbMouse);
        // 未使用
        Keyboard keyboard = new Keyboard();
        computer.useDevice(keyboard);
        computer.powerOff();
    }
}

```



