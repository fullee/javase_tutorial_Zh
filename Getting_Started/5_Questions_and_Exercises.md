# 问题和练习

## 问题：

1.当你用JPL编译一段程序时，编译器把人类能识别的源文件编译成JVM能理解的代码，这种代码叫啥？

答案：bytecode 字节码

2.哪一种注解时不可用的：

a. /** comment */

b. /* comment */

c. /* comment

d. // comment

答案：c

3.看到下面的错误你应该首先检查什么？

```java
Exception in thread "main" java.lang.NoClassDefFoundError:
HelloWorldApp.java.
```

答案：检查classpath,这个class是否存在。

4.main方法签名是什么？

答案：`public static void main(String[] args)` or `public static void main`(String... args)

5.当生命main方法时，public 和static那个参数放在第一个？

答案：可以任意的排序，但是通常`public static`.

6.main方法中定义了那些参数？

答案：main方法定义了一个参数，通常命名为args,类型是一个字符串数组。

## 练习：

1.改变HW程序，使它输出Hola Mundo! 

答案：

```java
System.out.println("Hola Mundo!"); //Display the string.
```

2.下面的程序有一个错误。修复这个错误使其成功运行。这个错误是什么？
```java
/*
 * Copyright (c) 1995, 2008, Oracle and/or its affiliates. All rights reserved.
 *
 * Redistribution and use in source and binary forms, with or without
 * modification, are permitted provided that the following conditions
 * are met:
 *
 *   - Redistributions of source code must retain the above copyright
 *     notice, this list of conditions and the following disclaimer.
 *
 *   - Redistributions in binary form must reproduce the above copyright
 *     notice, this list of conditions and the following disclaimer in the
 *     documentation and/or other materials provided with the distribution.
 *
 *   - Neither the name of Oracle or the names of its
 *     contributors may be used to endorse or promote products derived
 *     from this software without specific prior written permission.
 *
 * THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS
 * IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO,
 * THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR
 * PURPOSE ARE DISCLAIMED.  IN NO EVENT SHALL THE COPYRIGHT OWNER OR
 * CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL,
 * EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
 * PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR
 * PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF
 * LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING
 * NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
 * SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
 */ 

// INTENTIONALLY UNCOMPILABLE!

/** 
 * The HelloWorldApp class implements an application that
 * simply prints "Hello World!" to standard output.
 */
class HelloWorldApp2 {
    public static void main(String[] args) {
        System.out.println("Hello World!); // Display the string.
    }
}
```

答案：编译器提示如下错误：

```java
HelloWorldApp2.java:7: unclosed string literal
        System.out.println("Hello World!); //Display the string.
                           ^
HelloWorldApp2.java:7: ')' expected
        System.out.println("Hello World!); //Display the string.
                                                                ^
2 errors
```

把双引号闭合，修复如下：

```java
 System.out.println("Hello World!"); //Display the string.
```