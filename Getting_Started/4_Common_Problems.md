# 可能会遇到的问题

> 这是java_tutorial提供的一个问题列表，初学者遇到的大部分问题都能从中找打答案，如果还有问题，请到issue中提问。

## 1. 编译问题

### Windows操作系统中的问题

```shell
'javac' is not recognized as an internal or external command, operable program or batch file（'javac'不能被识别为内部命令、扩展命令、操作程序或脚本文件）
```

如果你遇到这个问题，说明windows没有找到编译器`javac`。
这里有个方法可以告诉windows如何找到javac。假如你的JDK安装在`C:\jdk1.8.0`,那么在命令行中输入如下命令：

```shell
C:\jdk1.8.0\bin\javac HelloWorldApp.java
```

如果你采用这种方式，那么你每次在使用java或javac运行或编译程序的时候必须要添加前缀`C:\jdk1.8.0`。如果想避免这种繁琐的方式,可以参考JDK8的[安装指导](https://docs.oracle.com/javase/8/docs/technotes/guides/install/windows_jdk_install.html#BABGDJFH)

```shell
Class names, 'HelloWorldApp', are only accepted if annotation processing is explicitly requested
```

如果你得到这样一个错误，在编译程序时你可能忘记了添加`.java`后缀。一定要记住，编译的命令是`javac HelloWorldApp.java`,而不是`javac HelloWorldApp`。

### 在类Unix系统的中错误提示

```
javac: Command not found
```

如果得到这个错误,说明unix没有找到`javac`编译器。
假设你的JDK安装在`/usr/local/jdk1.8.0`,那个你可以在终端中输入下面的命令：

```shell
/usr/local/jdk1.8.0/javac HelloWorldApp.java
```

同windows操作系统一样，为了避免这种冗长的方式，你可以把这个目录添加到PATH变量中，具体到方式取决于你运行的shell。

```
Class names, 'HelloWorldApp', are only accepted if annotation processing is explicitly requested
```

同windows系统一样，在使用`javac`命令编译程序时一定要添加`.java`的文件名后缀。


### 语法错误（针对所有的平台）

If you mistype part of a program, the compiler may issue a syntax error. The message usually displays the type of the error, the line number where the error was detected, the code on that line, and the position of the error within the code. Here's an error caused by omitting a semicolon (;) at the end of a statement:

testing.java:14: `;' expected.
System.out.println("Input has " + count + " chars.")
                                                     ^
1 error
Sometimes the compiler can't guess your intent and prints a confusing error message or multiple error messages if the error cascades over several lines. For example, the following code snippet omits a semicolon (;) from the bold line:

while (System.in.read() != -1)
    count++
System.out.println("Input has " + count + " chars."); 
When processing this code, the compiler issues two error messages:

testing.java:13: Invalid type expression.
        count++
                 ^
testing.java:14: Invalid declaration.
    System.out.println("Input has " + count + " chars.");
                      ^
2 errors
The compiler issues two error messages because after it processes count++, the compiler's state indicates that it's in the middle of an expression. Without the semicolon, the compiler has no way of knowing that the statement is complete.

If you see any compiler errors, then your program did not successfully compile, and the compiler did not create a .class file. Carefully verify the program, fix any errors that you detect, and try again.

如果你程序源码有错误，编译器可能会提示一个语法错误。这个信息通常会显示出错误的类型，发生错误的行号,以及错误在这行代码中的位置。
这段代码错误的原因是在这段代码的结尾缺少分号`;`：

```java
testing.java:14: `;' expected.
System.out.println("Input has " + count + " chars.")
                                                     ^
1 error
```
有时候编译器无法猜到你的想法，提示一个很迷惑的错误信息或者有多处错误信息。例如，下面第二行代码缺少了一个分号：

```java
while (System.in.read() != -1)
    count++
System.out.println("Input has " + count + " chars."); 
When processing this code, the compiler issues two error messages:

testing.java:13: Invalid type expression.
        count++
                 ^
testing.java:14: Invalid declaration.
    System.out.println("Input has " + count + " chars.");
                      ^
2 errors
```

这时，编译器提示了两处错误，因为在它处理count ++之后，编译器的状态指示它位于表达式的中间。 没有分号，编译器无法知道该语句是否完整。

当你发现有错误，你的程序没有被成功的编译，也没生成`.class`文件。这时要仔细检查你的程序，修复错误后重新尝试一次。

### 语义错误（Semantic Errors）

In addition to verifying that your program is syntactically correct, the compiler checks for other basic correctness. For example, the compiler warns you each time you use a variable that has not been initialized:

testing.java:13: Variable count may not have been initialized.
        count++
        ^
testing.java:14: Variable count may not have been initialized.
    System.out.println("Input has " + count + " chars.");
                                       ^
2 errors
Again, your program did not successfully compile, and the compiler did not create a .class file. Fix the error and try again.

编译器除了验证程序语法的正确性，还检查一些基本的语义是否正确。例如，编译器提示你使用的一个变量没有被初始化：

```java
testing.java:13: Variable count may not have been initialized.
        count++
        ^
testing.java:14: Variable count may not have been initialized.
    System.out.println("Input has " + count + " chars.");
                                       ^
2 errors
```

同样，你的程序编译失败，也没有生成`.class`文件。修复这个错误然后再试一次。

## 2.运行时问题（Runtime Problems）

### windows操作系统中的错误提示（Error Messages on Microsoft Windows Systems）

```java
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorldApp
```

If you receive this error, java cannot find your bytecode file, HelloWorldApp.class.

One of the places java tries to find your .class file is your current directory. So if your .class file is in C:\java, you should change your current directory to that. To change your directory, type the following command at the prompt and press Enter:

cd c:\java
The prompt should change to C:\java>. If you enter dir at the prompt, you should see your .java and .class files. Now enter java HelloWorldApp again.

If you still have problems, you might have to change your CLASSPATH variable. To see if this is necessary, try clobbering the classpath with the following command.

Now enter java HelloWorldApp again. If the program works now, you'll have to change your CLASSPATH variable. To set this variable, consult the Updating the PATH variable section in the JDK 8 installation instructions. The CLASSPATH variable is set in the same manner.

```java
Could not find or load main class HelloWorldApp.class
```

A common mistake made by beginner programmers is to try and run the java launcher on the .class file that was created by the compiler. For example, you'll get this error if you try to run your program with java HelloWorldApp.class instead of java HelloWorldApp. Remember, the argument is the name of the class that you want to use, not the filename.

The Java VM requires that the class you execute with it have a main method at which to begin execution of your application. A Closer Look at the "Hello World!" Application discusses the main method in detail.

```java
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorldApp
```

如果你得到这个错误提示，说明`java`没有找到你的字节码文件`HelloWorldApp.class`。

`java`尝试在当前目录查找`.class`文件，假设你的`.class`文件在`C:\java`目录夏，你应当将当前目录切换到`C:\java`。切换目录的命令如下：

```shell
cd c:\java
```

这时提示符变成`C:\java`,你应当能看到`.java`和`.class`文件，现在再次运行`java HelloWorldApp`。

如果依然存在这个问题，你需要改变你的`CLASSPATH`变量。想验证是否有必要设置这个变量，尝试下面的命令：

```shell
set CLASSPATH=
```

再次输入`java HelloWorldApp`。如果你的程序可以正常运行了，那么你需要设置这个变量。要设置这个变量请参考JDK8安装介绍中的[更新PATH变量](https://docs.oracle.com/javase/8/docs/technotes/guides/install/windows_jdk_install.html#BABGDJFH)。

```java
Could not find or load main class HelloWorldApp.class
```

初学者通常会尝试运行编译器生成的`.class`文件。如果你使用`java HelloWorldApp.class`来尝试运行你的程序，那么你会得到这个错误提示。请记住，这个参数是类名而不是文件名，即运行`java HelloWorldApp`是正确的。

```java
Exception in thread "main" java.lang.NoSuchMethodError: main
```

JVM要求要执行的类必须具有main方法。 在前面的[HelloWorld详解](3_A_Closer_Look_atHW.md)有详细说明。

### UNIX操作系统中的错误提示（Error Messages on UNIX Systems）

Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorldApp

If you receive this error, java cannot find your bytecode file, HelloWorldApp.class.

One of the places java tries to find your bytecode file is your current directory. So, for example, if your bytecode file is in /home/jdoe/java, you should change your current directory to that. To change your directory, type the following command at the prompt and press Return:

cd /home/jdoe/java
If you enter pwd at the prompt, you should see /home/jdoe/java. If you enter ls at the prompt, you should see your .java and .class files. Now enter java HelloWorldApp again.

If you still have problems, you might have to change your CLASSPATH environment variable. To see if this is necessary, try clobbering the classpath with the following command.

unset CLASSPATH
Now enter java HelloWorldApp again. If the program works now, you'll have to change your CLASSPATH variable in the same manner as the PATH variable above.

Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorldApp/class

A common mistake made by beginner programmers is to try and run the java launcher on the .class file that was created by the compiler. For example, you'll get this error if you try to run your program with java HelloWorldApp.class instead of java HelloWorldApp. Remember, the argument is the name of the class that you want to use, not the filename.

Exception in thread "main" java.lang.NoSuchMethodError: main

The Java VM requires that the class you execute with it have a main method at which to begin execution of your application. A Closer Look at the "Hello World!" Application discusses the main method in detail.

### Applet或者JavaWebStart应用使被阻塞的（Applet or Java Web Start Application Is Blocked）

If you are running an application through a browser and get security warnings that say the application is blocked, check the following items:

Verify that the attributes in the JAR file manifest are set correctly for the environment in which the application is running. The Permissions attribute is required. In a NetBeans project, you can open the manifest file from the Files tab of the NetBeans IDE by expanding the project folder and double-clicking manifest.mf.

Verify that the application is signed by a valid certificate and that the certificate is located in the Signer CA keystore.

If you are running a local applet, set up a web server to use for testing. You can also add your application to the exception site list, which is managed in the Security tab of the Java Control Panel.
