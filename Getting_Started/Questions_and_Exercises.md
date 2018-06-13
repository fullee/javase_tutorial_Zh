# 问题和练习
## 问题：
1. 当你用JPL编译一段程序时，编译器将人类能识别的源文件编译成JVM能理解的代码，这种代码叫啥？
答案：bytecode

2. 哪一种注解时不可用的：
a. /** comment */
b. /* comment */
c. /* comment
d. // comment
答案：c

3. 看到下面的错误你应该首先检查什么？
```
Exception in thread "main" java.lang.NoClassDefFoundError:
HelloWorldApp.java.
```
答案：检查classpath,这个class是否存在。
4. main方法签名是什么？
答案：public static void main(String[] args) or public static void main(String... args)

5.当生命main方法时，public 和static那个参数放在第一个？
答案：可以任意的排序，但是通常`public static`.

6. main方法中定义了那些参数？
main方法定义了一个参数，通常命名为args,类型是一个字符串数组。

## 练习：
1.改变HW程序，使它输出Hola Mundo! 
答案：
```
System.out.println("Hola Mundo!"); //Display the string.
```

Exercise 2: You can find a slightly modified version of HelloWorldApp here: HelloWorldApp2.java

The program has an error. Fix the error so that the program successfully compiles and runs. What was the error?

Answer 2: Here's the error you get when you try to compile the program:

HelloWorldApp2.java:7: unclosed string literal
        System.out.println("Hello World!); //Display the string.
                           ^
HelloWorldApp2.java:7: ')' expected
        System.out.println("Hello World!); //Display the string.
                                                                ^
2 errors
To fix this mistake, you need to close the quotation marks around the string. Here is the correct line of code:

 System.out.println("Hello World!"); //Display the string.
