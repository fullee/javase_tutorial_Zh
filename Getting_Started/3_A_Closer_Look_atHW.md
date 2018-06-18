# HelloWorld详解

现在再看一眼HW程序，你可能想知道它是如何运行的。

```java
/**
 * The HelloWorldApp class implements an application that
 * simply prints "Hello World!" to standard output.
 */
class HelloWorldApp {
    public static void main(String[] args) {
        System.out.println("Hello World!"); // Display the string.
    }
}
```

HW包含三个主要的部分。源码注释，类定义，main方法。这一节依然是简单的介绍，深入理解的只有读完这份教程才会有更深的理解。

### 注释

注释会被编译器忽略，但是会对程序员有帮助。JPL支持下面三种类型的注释：

```
/* text */
编译器将会忽略 /* 和 */之间的内容.
/** documentation */
跟/* text */一样编译器同样会忽略这种类型的注释，但是javadoc命令会使用这种类型的注释自动生成文档。详细了解javadoc,可以查看https://docs.oracle.com/javase/8/docs/technotes/guides/javadoc/index.html
// text
编译器会忽略从`//`开始到行尾的所有内容
```

### HelloWorldApp 类定义

类定义的基本形式如下：
```
class name {
    . . .
}
```

class关键字用于命名这个类。代码在大括号中间。第二章简述，第四章将会讨论类的定义。

### main方法

在JPL中，每一个程序必须含有main方法，签名如下：

```java
public static void main(String[] args)
```

public 和 static 的顺序没有限制 (public static or static public)，但是习惯上还是使用`public static`
关于参数你可以使用任意的名字，但是一些程序员习惯上使用`args`或者`argv`.

main方法类似于C和C++中的main函数，它是应用程序的入口。然后再由它调用其它方法。

main只接受一个字符串数组作为参数。这个字符串数组是程序运行时传递数据的一种机制，如下：

```shell
java MyApp arg1 arg2
```

数组中每一个元素都是命令行中的参数。通过传递命令行参数来改变程序的行为而不需要重新编译程序。例如一个排序程序可以通过用户指定命令行参数使得数据倒序排序。

虽然再HW中忽略了这个参数，但是你应当意识到参数时存在的。

最后一行：

```java
System.out.println("Hello World!");
```

使用核心库提供的`System`向标准输出设备输出“Hello World!”信息，核心库的其它部分将再后面的章节中介绍。



















