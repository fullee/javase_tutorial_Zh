# 可能会遇到的问题

## 编译问题
### Windows操作系统的问题
```
'javac' is not recognized as an internal or external command, operable program or batch file
'javac'不能被识别为内部命令、扩展命令、操作程序或者脚本文件
```
如果你遇到这个问题，说明windows没有找到编译器javac。
这里有个方法可以告诉windows如何找到javac。假如你的JDK安装在`C:\jdk1.8.0`,那么在命令行中输入如下命令：
```
C:\jdk1.8.0\bin\javac HelloWorldApp.java
```
如果你采用这种方式，那么你每次在使用java或javac运行或编译程序的时候必须要添加前缀`C:\jdk1.8.0`。如果想避免这种繁琐的方式,可以参考JDK8的[安装指导](https://docs.oracle.com/javase/8/docs/technotes/guides/install/windows_jdk_install.html#BABGDJFH)

```
Class names, 'HelloWorldApp', are only accepted if annotation processing is explicitly requested
```
如果你得到这样一个错误，在编译程序时你可能忘记了添加`.java`后缀。一定要记住，编译的命令是`javac HelloWorldApp.java`,而不是`javac HelloWorldApp`。

### 在类Unix系统的错误提示
```
javac: Command not found
```
如果得到这个错误,unix没有找到javac编译器。
假设你的JDK安装在`/usr/local/jdk1.8.0`,那个你可以在终端中输入下面的命令：
```
/usr/local/jdk1.8.0/javac HelloWorldApp.java
```
同windows系统一样，为了避免这种冗长的方式，你可以把这个目录添加到PATH变量中，具体到方式取决于你运行的shell。

```
Class names, 'HelloWorldApp', are only accepted if annotation processing is explicitly requested
```
同windows系统一样，在使用`javac`命令编译程序时一定要添加`.java`的后缀。

### 语法错误（所有的平台）
如果你程序输入有错误，编译器可能会包一个语法错误。这个信息通常会显示出错误的类型，发生错误的行号,这一行代码以及错误在这行代码中的位置。
这里这个错误的原因是在这段代码的结尾缺少`;`
```
testing.java:14: `;' expected.
System.out.println("Input has " + count + " chars.")
                                                     ^
1 error
```
有时候编译器无法猜到你的想法，提示一个模糊的错误或者有多处错误信息
