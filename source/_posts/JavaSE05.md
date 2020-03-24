---
title: Java SE 基础系列笔记 (5)
date: 2020-02-21 22:03:04
tags: inner
categories: Java
toc: true	
---

JAVA 内部类学习

<!-- more -->

## 内部类的分类

1. 成员内部类
2. 局部内部类（包含匿名内部类）

## 成员内部类的定义

```java
修饰符 class 外部类名称{
	修饰符 class 内部类名称{
		//...
		}
		//...
		}
```

**注意：内用外，随意访问；外用内，需要内部类对象。**

## 成员内部类的使用

### 间接方式

**通过外部类对象，调用外部类的方法，里面间接使用内部类**`Heart`。

EXP:

```java
package com.demo04内部类;

public class Body {
    private String name = "某某 ";
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }

    public void method(){
        new Heart().beat();// 外部类调用内部类方法
    }

    // 内部类
    public  class Heart{
        public void beat(){
            System.out.println(name+"beat");
        }
    }

}

```



```java
package com.demo04内部类;

public class HeartBody {
    public static void main(String[] args) {
        Body body = new Body();
        body.method();

    }
}

```



### 直接方式

公式：

```java
类名称 对象名 = new 类名称()；
外部类名称.内部类名称 对象名 = new 外部类名称().new 内部类名称;
```

以上面例子使用： ` Body.Heart heart = new Body().new Heart();`

注意：如果内部类要访问外部类的同名变量，格式为 `外部类名称 . this.外部类成员变量名`。

## 局部内部类的定义

如果一个类是定义在一个方法内部的，那么这就是一个局部内部类。

​	格式：

```java
修饰符 class 外部类名称{
    修饰符 返回值类型 外部类方法名称{
        class 内部类名称{
        //...
        }
    }
}
```

**注意：只有当前所属的方法才能使用它。**

*先小节一下类的权限修饰符：*

​	`public` >  `protected` > `default` >  `private`

**定义一个类时，权限修饰符规则：**

- 外部类： `public` / `(default)`

- 成员内部类： `public`/`protected`/`(default)`/`private`

- 局部内部类：**什么都不能写！！！**

  

**注意事项：局部内部类，如果希望访问所在方法的局部变量，那么这个局部变量必须是有效`final`的。**

**备注： 从`Java8+`开始，只要局部变量事实不变，那么`final`关键字可以省略。**

### 匿名内部类

何种情况需要匿名内部类？

如果接口的实现类（或者是父类的子类）只需要使用唯一的一次。

```java
接口名称 对象名 = new 接口名称（）{
  //覆盖重写所有抽象方法
  }；
```

exp:

**一般方法以及匿名内部类方法：**

```java
package com.demo05匿名内部类;

/**
 * @ClassName: Interfaceo
 * @Description: 接口
 * @author: Aimer
 * @date: 2020/2/24  20:21
 * version: 1.0
 */
public interface Interfaceo {
    void print();
}

```



```java
package com.demo05匿名内部类;

/**
 * @ClassName: InterCom
 * @Description: 实现接口方法类
 * @author: Aimer
 * @date: 2020/2/24  20:28
 * version: 1.0
 */
public class InterCom implements Interfaceo{
    @Override
    public void print() {
        System.out.println("类实现接口");
    }
}

```



```java
package com.demo05匿名内部类;

/**
 * @ClassName: InterMy
 * @Description: 两种方法实现接口
 * @author: Aimer
 * @date: 2020/2/24  20:22
 * version: 1.0
 */
public class InterMy {
    public static void main(String[] args) {
        InterCom interCom = new InterCom();
        interCom.print();

        Interfaceo interfaceo = new Interfaceo() {
            @Override
            public void print() {
                System.out.println("匿名内部类实现");
            }
        };
        interfaceo.print();
    }
}

```

### 匿名内部类注意事项

**对格式 ` new 接口名称（）{}`进行解析：**

- `new` 代表创建对象的动作

- 接口名称就是匿名内部类需要实现哪个接口

- `{~}`其中才是匿名内部类的内容

  

还要注意：

* 匿名内部类，在【创建对象】时，只能使用唯一一次。如果希望多次创建对象，而且类的内容一样的话，那么必须使用单独定义的实现类。

* 匿名对象,在【调用方法】的时候，只能调用唯一一次。如果希望同一个对象调用多次方法，那么必须给对象起个名字。

* 匿名内部类是省略了【实现类/子类】,但是匿名对象是省略了【对象名称】。

  

exp：

```java
        new Interfaceo(){
            @Override
            public void print() {
                System.out.println("匿名对象打印");
            }
        }.print();
```

## 其它

- **类、接口可以作为成员变量类型**

  ```java
          hero.setSkill(new Skill() {
              @Override
              public void use() {
                  System.out.println("hhaha");
              }
          });
  ```

  

- **接口可以作为方法的参数或者返回值**