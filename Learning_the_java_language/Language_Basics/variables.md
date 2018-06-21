# 变量

```java
int cadence = 0;
int speed = 0;
int gear = 1;
```

在[什么是对象]()这一节讨论了字段，但是你可能仍然有几个问题，例如：对象的命名规则和约定是什么？除了int类型还有什么类型？字段被声明时是否必须被初始化？如果没有显式的赋值初始化时是否会有默认值?我们将在这一节讨论这些答案，在此之前，你必须首先意识到一些技术上的区别。在JPL中，术语“字段”和“变量”两者都会使用；这在新开发人员中是一个常见的困惑来源，因为两者似乎常常指的是同一件事。

JPL定义了以下类型的变量:

* 实例变量 Instance Variables (Non-Static Fields) Technically speaking, objects store their individual states in "non-static fields", that is, fields declared without the static keyword. Non-static fields are also known as instance variables because their values are unique to each instance of a class (to each object, in other words); the currentSpeed of one bicycle is independent from the currentSpeed of another.
* 类变量 Class Variables (Static Fields) A class variable is any field declared with the static modifier; this tells the compiler that there is exactly one copy of this variable in existence, regardless of how many times the class has been instantiated. A field defining the number of gears for a particular kind of bicycle could be marked as static since conceptually the same number of gears will apply to all instances. The code static int numGears = 6; would create such a static field. Additionally, the keyword final could be added to indicate that the number of gears will never change.
* 本地变量 Local Variables Similar to how an object stores its state in fields, a method will often store its temporary state in local variables. The syntax for declaring a local variable is similar to declaring a field (for example, int count = 0;). There is no special keyword designating a variable as local; that determination comes entirely from the location in which the variable is declared — which is between the opening and closing braces of a method. As such, local variables are only visible to the methods in which they are declared; they are not accessible from the rest of the class.
* 参数 Parameters You've already seen examples of parameters, both in the Bicycle class and in the main method of the "Hello World!" application. Recall that the signature for the main method is public static void main(String[] args). Here, the args variable is the parameter to this method. The important thing to remember is that parameters are always classified as "variables" not "fields". This applies to other parameter-accepting constructs as well (such as constructors and exception handlers) that you'll learn about later in the tutorial.

Having said that, the remainder of this tutorial uses the following general guidelines when discussing fields and variables. If we are talking about "fields in general" (excluding local variables and parameters), we may simply say "fields". If the discussion applies to "all of the above", we may simply say "variables". If the context calls for a distinction, we will use specific terms (static field, local variables, etc.) as appropriate. You may also occasionally see the term "member" used as well. A type's fields, methods, and nested types are collectively called its members.

本教程的剩余部分在讨论字段和变量时使用下面的指导原则。如果我们在讨论“一般的字段”（不包括本地变量和参数），我们会简单的说“字段”。如果在讨论“所有上述”，我们可以简单的说“变量”。如果上下文需要区分，我们酌情使用特定的数据（静态变量，局部变量等）。偶尔可能会看到“成员”这个词。类型的字段，方法，嵌套类型统称为类的成员。

## 命名

Every programming language has its own set of rules and conventions for the kinds of names that you're allowed to use, and the Java programming language is no different. The rules and conventions for naming your variables can be summarized as follows:

每一种编程语言都有自己的一套规则和惯例，适用于允许使用的名称类型。JPL也一样。变量的命名规则和约定如下：

* Variable names are case-sensitive. A variable's name can be any legal identifier — an unlimited-length sequence of Unicode letters and digits, beginning with a letter, the dollar sign "$", or the underscore character "_". The convention, however, is to always begin your variable names with a letter, not "$" or "_". Additionally, the dollar sign character, by convention, is never used at all. You may find some situations where auto-generated names will contain the dollar sign, but your variable names should always avoid using it. A similar convention exists for the underscore character; while it's technically legal to begin your variable's name with "_", this practice is discouraged. White space is not permitted.
* 变量名区分大小写。可以使用任意的合法标识符（unicode字符和数字，并且不限制长度），必须以字母，`$`,`_`开始。通常会使用字母，而不建议使用`_`开始。此外，按照惯例，美元符号根本不使用。您可能会发现一些情况，自动生成的名称将包含美元符号，但是变量名应该避免使用它。对于下划线字符也有类似的约定;虽然从技术上讲，以`_`开头的变量名是合法的。空格是不允许的。
* Subsequent characters may be letters, digits, dollar signs, or underscore characters. Conventions (and common sense) apply to this rule as well. When choosing a name for your variables, use full words instead of cryptic abbreviations. Doing so will make your code easier to read and understand. In many cases it will also make your code self-documenting; fields named cadence, speed, and gear, for example, are much more intuitive than abbreviated versions, such as s, c, and g. Also keep in mind that the name you choose must not be [a keyword or reserved word.](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/_keywords.html)
* 后面的字符可以使用字母，数字，$ _.此外，尽量使用全称而不是简称。这样做将使您的代码更易于阅读和理解。很多请情况下，会根据代码生成文档，使用cadence，speed，gear要比s,c,g直观。还要记住，您选择的名称不能是关键字或保留词。
* If the name you choose consists of only one word, spell that word in all lowercase letters. If it consists of more than one word, capitalize the first letter of each subsequent word. The names gearRatio and currentGear are prime examples of this convention. If your variable stores a constant value, such as static final int NUM_GEARS = 6, the convention changes slightly, capitalizing every letter and separating subsequent words with the underscore character. By convention, the underscore character is never used elsewhere.
* 如果你选择的名字只有一个词，这个单词需要全部使用小写，如果超过一个单词，后面的每个单词的首字母都要以大写开始。例如：gearRatio和currentGear。如果你的变量存储的是常量值，例如：`static final int NUM_GEARS= 6`,每个字母都要大写并且使用下划线链接。除此之外，下划线尽量不要在其他地方使用。

### 基本数据类型

JPL是静态类型的，所有的变量必须先声明后使用。正如你见到的，声明包含了类型和名称：

```java
int gear = 1;
```

这样做会告诉程序一个名为“gear”的字段存在,并且是一个数字类型的，初始值是“1”。变量的数据类型可以确定它可能包含的值，以及可能对它执行的操作。除了int，JPL还有7中基本数据类型。基本类型由语言定义，名字是保留字。原始类型不能于其他的原始类型共享状态。JPL支持的8中原始类型如下：

* byte: The byte data type is an 8-bit signed two's complement integer. It has a minimum value of -128 and a maximum value of 127 (inclusive). The byte data type can be useful for saving memory in large arrays, where the memory savings actually matters. They can also be used in place of int where their limits help to clarify your code; the fact that a variable's range is limited can serve as a form of documentation.
* 字节数据类型是一个8位有符号二进制补码整数。最小值是`-128`,最大值`127`。
* short: The short data type is a 16-bit signed two's complement integer. It has a minimum value of -32,768 and a maximum value of 32,767 (inclusive). As with byte, the same guidelines apply: you can use a short to save memory in large arrays, in situations where the memory savings actually matters.

* int: By default, the int data type is a 32-bit signed two's complement integer, which has a minimum value of -231 and a maximum value of 231-1. In Java SE 8 and later, you can use the int data type to represent an unsigned 32-bit integer, which has a minimum value of 0 and a maximum value of 232-1. Use the Integer class to use int data type as an unsigned integer. See the section The Number Classes for more information. Static methods like compareUnsigned, divideUnsigned etc have been added to the Integer class to support the arithmetic operations for unsigned integers.

* long: The long data type is a 64-bit two's complement integer. The signed long has a minimum value of -263 and a maximum value of 263-1. In Java SE 8 and later, you can use the long data type to represent an unsigned 64-bit long, which has a minimum value of 0 and a maximum value of 264-1. Use this data type when you need a range of values wider than those provided by int. The Long class also contains methods like compareUnsigned, divideUnsigned etc to support arithmetic operations for unsigned long.

* float: The float data type is a single-precision 32-bit IEEE 754 floating point. Its range of values is beyond the scope of this discussion, but is specified in the Floating-Point Types, Formats, and Values section of the Java Language Specification. As with the recommendations for byte and short, use a float (instead of double) if you need to save memory in large arrays of floating point numbers. This data type should never be used for precise values, such as currency. For that, you will need to use the java.math.BigDecimal class instead. Numbers and Strings covers BigDecimal and other useful classes provided by the Java platform.

* double: The double data type is a double-precision 64-bit IEEE 754 floating point. Its range of values is beyond the scope of this discussion, but is specified in the Floating-Point Types, Formats, and Values section of the Java Language Specification. For decimal values, this data type is generally the default choice. As mentioned above, this data type should never be used for precise values, such as currency.

* boolean: The boolean data type has only two possible values: true and false. Use this data type for simple flags that track true/false conditions. This data type represents one bit of information, but its "size" isn't something that's precisely defined.
* boolean类型有且仅有两个值：true和false。使用这个类型作为简单的标志条件。
* char: The char data type is a single 16-bit Unicode character. It has a minimum value of '\u0000' (or 0) and a maximum value of '\uffff' (or 65,535 inclusive).
* char： char类型表示单个的16位unicode字符。它的最小值`\u0000`(or 0)最大值`\uffff`(or 65535)。

除了上面列出的8中基本数据类型，JPL还提供了移动特殊的字符序列类型叫`java.lang.String`的类。将字符串括在双引号内将自动创建一个新的字符串对象;例如：`String s = "this is a string";`.字符串对象是不可变的，意思是它被创建一次后其值将不能被改变。String类技术上来说不是基本类型，但是考虑到JPL给它特殊的支持，你也可以认为它是基本类型。可以在[Simple Data Objects](https://docs.oracle.com/javase/tutorial/java/data/index.html)学习更多关于String的知识。

#### 默认值

在字段声明式并不总是需要显示赋值。声明但没有初始化时编译器会默认赋一个合理的值。通常来说，默认值将是`0` 或者是`null`,具体取决于数据类型。依赖这种默认值是一种不好的编程风格。
下面的表总结了重要数据类型的默认值：
| 数据类型 | 默认值|
|---|---|
byte|0|
short|0
int|0
long|0L
float|0.0f
double|0.0d
char|'\u0000'
String (or any object)| null
|boolean|false|

本地变量（Local variables）略有不同；编译器不会为没有初始化的本地变量赋初始值。如果在声明时你没有初始化本地变量。在使用本地变量前，请确保为它附一个值，否则在访问这个本地变量时将会抛一个编译时（compile-time）错误。

#### 字面值

你可能注意到在初始化基本类型的变量时没有使用`new`关键字。基本类型时JPL内置的特殊的数据类型；它们不是从class中创建的对象。字面值在源码中是一个固定值，不需要计算。如下所示，为基本类型附一个字面值：

```java
boolean result = true;
char capitalC = 'C';
byte b = 100;
short s = 10000;
int i = 100000;
```

##### 整形字面值

`long`类型字面值结尾要加`L`或者`l`，否则就是int类型。建议使用大写L，因为小写l很像数字1.
整形字面值由下面的数值系统表达：

* 十进制
* 十六进制
* 二进制 (you can create binary literals in Java SE 7 and later)

通常来说，你可能只使用十进制数字系统。然而，如果你是用其他的数字系统，语法如下面，前缀0x表示16进制，0b表示二进制。

```java
int decVal=26;
int hexVal=0x1a;
int binVal=0b11010;
```

##### 浮点型字面值

##### 字符和字符串字面值

char和String可以包含任意的Unicode（UTF-16）字符。如果你的编辑器和文件系统允许的话，你可以直接使用这些字符编辑。如果不行，你可以使用“Unicode 逃逸字符”例如`\u0108`(大写字母Ĉ)， or "S\u00ED Se\u00F1or" (Sí Señor in Spanish)，所有的char字面值使用`'`包裹，String字面值使用`"`包裹。Unicode转义序列可以在程序的其他地方使用(例如在字段名中)，而不只是在字符或字符串中使用。JPL为char和String还支持几个特殊的逃逸字符： \b (空格), \t (tab), \n (行尾), \f (换页), \r (回车), \" (双引号), \' (单引号), and \\ (反斜杠).
还有 一个特殊的字面值null，它可以赋值给任何引用类型的变量，除了基本类型变量。除了对null值的存在进行测试之外，几乎没有什么可以做的。因此，在程序中常常使用null作为标记来表示某个对象不可用。

最后，还有一种特殊的字面值叫做class字面值，它是由一个类型名加上`.class`组成的;例如,String.class。这指的是表示类型本身的对象(类型类)。

##### 在数字字面值中使用下划线字符

### 数组

array是一种容器，用于保存单一类型且固定个数的对象。数组的长度在创建是已经被确定。这一节会更加详细的讨论数组。

![数组](../images/2_1.jpg)

数组中每一项叫做一个元素（element），每个元素可以通过它的索引号访问。如上图所示，索引从0开始，第9个元素的索引是8.

如ArrayDemo，创建一个整形数组，放入一些元素到数组中，打印每个值到标准输出。

```java
class ArrayDemo{
public static void main(String[] args) {
        // declares an array of integers
        int[] anArray;

        // allocates memory for 10 integers
        anArray = new int[10];

        // initialize first element
        anArray[0] = 100;
        // initialize second element
        anArray[1] = 200;
        // and so forth
        anArray[2] = 300;
        anArray[3] = 400;
        anArray[4] = 500;
        anArray[5] = 600;
        anArray[6] = 700;
        anArray[7] = 800;
        anArray[8] = 900;
        anArray[9] = 1000;

        System.out.println("Element at index 0: " + anArray[0]);
        System.out.println("Element at index 1: " + anArray[1]);
        System.out.println("Element at index 2: " + anArray[2]);
        System.out.println("Element at index 3: "+ anArray[3]);
        System.out.println("Element at index 4: "+ anArray[4]);
        System.out.println("Element at index 5: "+ anArray[5]);
        System.out.println("Element at index 6: "+ anArray[6]);
        System.out.println("Element at index 7: "+ anArray[7]);
        System.out.println("Element at index 8: "+ anArray[8]);
        System.out.println("Element at index 9: "+ anArray[9]);
    }
}

程序输出内容：
Element at index 0: 100
Element at index 1: 200
Element at index 2: 300
Element at index 3: 400
Element at index 4: 500
Element at index 5: 600
Element at index 6: 700
Element at index 7: 800
Element at index 8: 900
Element at index 9: 1000
```

在真实的编程场景中，您可能会使用一个受支持的循环结构来遍历数组的每个元素，而不是像前面的示例那样逐个编写每一行。然而，这个例子清楚地说明了数组语法。您将在[控制流](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/flow.html)部分了解各种循环结构(for、while和do-while)。

#### 声明引用数组的变量

前面的程序声明了一个数组代码如下：

```java
int[] anArray;
```

与声明其它类型的变量相同，声明一个数组需要两个组件：数组的类型和数组的名字。数组的类型写法type[],type是包含的元素的数据类型，括号是表示该变量是一个数组。数组的大小不是其类型的一部分(这就是方括号为空的原因)。数组的名字可以起任意的，只要遵循前面变量的[命名](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/variables.html#naming)约定。同其它类型的变量，声明实际上不会创建一个数组，它只是告诉编译器这个变量将指向一个特定类型的数组。
类似的，你可以声明其他类型的数组：

```java
byte[] anArrayOfBytes;
short[] anArrayOfShorts;
long[] anArrayOfLongs;
float[] anArrayOfFloats;
double[] anArrayOfDoubles;
boolean[] anArrayOfBooleans;
char[] anArrayOfChars;
String[] anArrayOfStrings;
```

还可以将括号放在数组名之后:

```java
float anArrayOfFloats[];
```

然而，公约不鼓励这种形式;方括号标识数组类型，应该与类型指定一起出现。

#### 创建，初始化，访问一个数组

使用new关键字可以创建一个数组。下面的语句摘自`ArrayDemo`程序，分配了足够存放十个整形元素的内存并指向`anArray`变量。

```java
anArray = new int[10];
```

如果这一段丢失了，那么编译器将会打印如下错误，并且编译失败：

```java
ArrayDemo.java:4: Variable anArray may not have been initialized.
```

下面几行是为为这个数组的元素赋值：

```java
anArray[0] = 100; // initialize first element
anArray[1] = 200; // initialize second element
anArray[2] = 300; // and so forth
```

通过索引访问数组中的元素：

```java
System.out.println("Element 1 at index 0: " + anArray[0]);
System.out.println("Element 2 at index 1: " + anArray[1]);
System.out.println("Element 3 at index 2: " + anArray[2]);
```

还可以使用如下的方法创建和初始化数组：

```java
int[] anArray = {
    100, 200, 300,
    400, 500, 600,
    700, 800, 900, 1000
};
```

这里数组的长度是由元素的个数决定的。

You can also declare an array of arrays (also known as a multidimensional array) by using two or more sets of brackets, such as String[][] names. Each element, therefore, must be accessed by a corresponding number of index values.
你可以使用两个或更多的括号声明一个数组的数组（多维数组），例如`String[][] names`。因此，每个元素必须通过相应数量的索引值进行访问。
In the Java programming language, a multidimensional array is an array whose components are themselves arrays. This is unlike arrays in C or Fortran. A consequence of this is that the rows are allowed to vary in length, as shown in the following MultiDimArrayDemo program:

在JPL中，多维数组是其组件本身就是数组的数组。这与C或Fortran中的数组不同。 这样做的结果是允许行的长度变化，如下面的MultiDimArrayDemo程序所示：

```java
class MultiDimArrayDemo {
    public static void main(String[] args) {
        String[][] names = {
            {"Mr. ", "Mrs. ", "Ms. "},
            {"Smith", "Jones"}
        };
        // Mr. Smith
        System.out.println(names[0][0] + names[1][0]);
        // Ms. Jones
        System.out.println(names[0][2] + names[1][1]);
    }
}
```

The output from this program is:

```java
Mr. Smith
Ms. Jones
```

Finally, you can use the built-in length property to determine the size of any array. The following code prints the array's size to standard output:
最后，你可以使用内置的`length`属性确定任意数组的大小。下面的代码将数组的大小打印到标准输出：

```java
 System.out.println(anArray.length);
```

#### Copying Arrays

The System class has an arraycopy method that you can use to efficiently copy data from one array into another:
在`java.lang.System`类中有一个arraycopy方法可以高效的完成数组的拷贝：

```java
public static native void arraycopy(Object src, int srcPos,Object dest, int destPos, int length)
```

The two Object arguments specify the array to copy from and the array to copy to. The three int arguments specify the starting position in the source array, the starting position in the destination array, and the number of array elements to copy.
两个Object参数指定要从中复制的数组和要复制到的数组。 三个int参数指定源数组中的起始位置，目标数组中的起始位置以及要复制的数组元素的数量。
The following program, ArrayCopyDemo, declares an array of char elements, spelling the word "decaffeinated." It uses the System.arraycopy method to copy a subsequence of array components into a second array:

```java
class ArrayCopyDemo {
    public static void main(String[] args) {
        char[] copyFrom = { 'd', 'e', 'c', 'a', 'f', 'f', 'e', 'i', 'n', 'a', 't', 'e', 'd' };
        char[] copyTo = new char[7];

        System.arraycopy(copyFrom, 2, copyTo, 0, 7);
        System.out.println(new String(copyTo));
    }
}
```

The output from this program is:

```java
caffein
```

#### Array Manipulations

Arrays are a powerful and useful concept used in programming. Java SE provides methods to perform some of the most common manipulations related to arrays. For instance, the ArrayCopyDemo example uses the arraycopy method of the System class instead of manually iterating through the elements of the source array and placing each one into the destination array. This is performed behind the scenes, enabling the developer to use just one line of code to call the method.

For your convenience, Java SE provides several methods for performing array manipulations (common tasks, such as copying, sorting and searching arrays) in the `java.util.Arrays` class. For instance, the previous example can be modified to use the copyOfRange method of the java.util.Arrays class, as you can see in the ArrayCopyOfDemo example. The difference is that using the copyOfRange method does not require you to create the destination array before calling the method, because the destination array is returned by the method:

```java
class ArrayCopyOfDemo {
    public static void main(String[] args) {

        char[] copyFrom = {'d', 'e', 'c', 'a', 'f', 'f', 'e',
            'i', 'n', 'a', 't', 'e', 'd'};

        char[] copyTo = java.util.Arrays.copyOfRange(copyFrom, 2, 9);

        System.out.println(new String(copyTo));
    }
}
```

As you can see, the output from this program is the same (caffein), although it requires fewer lines of code. Note that the second parameter of the copyOfRange method is the initial index of the range to be copied, inclusively, while the third parameter is the final index of the range to be copied, exclusively. In this example, the range to be copied does not include the array element at index 9 (which contains the character a).

Some other useful operations provided by methods in the java.util.Arrays class, are:

* 搜索Searching an array for a specific value to get the index at which it is placed (the binarySearch method).
* 比较Comparing two arrays to determine if they are equal or not (the equals method).
* 填充Filling an array to place a specific value at each index (the fill method).
* 排序Sorting an array into ascending order. This can be done either sequentially, using the sort method, or concurrently, using the parallelSort method introduced in Java SE 8. Parallel sorting of large arrays on multiprocessor systems is faster than sequential array sorting.

### 变量总结

The Java programming language uses both "fields" and "variables" as part of its terminology. Instance variables (non-static fields) are unique to each instance of a class. Class variables (static fields) are fields declared with the static modifier; there is exactly one copy of a class variable, regardless of how many times the class has been instantiated. Local variables store temporary state inside a method. Parameters are variables that provide extra information to a method; both local variables and parameters are always classified as "variables" (not "fields"). When naming your fields or variables, there are rules and conventions that you should (or must) follow.

The eight primitive data types are: byte, short, int, long, float, double, boolean, and char. The java.lang.String class represents character strings. The compiler will assign a reasonable default value for fields of the above types; for local variables, a default value is never assigned. A literal is the source code representation of a fixed value. An array is a container object that holds a fixed number of values of a single type. The length of an array is established when the array is created. After creation, its length is fixed.

八种原始数据类型：byte, short, int, long, float, double, boolean, and char. `java.lang.String`表示一个字符序列。编译器将为上述字段附一个合理的默认值；本地变量不会赋默认值。字面值是源码中固定的值。数组是一个包含相同类型固定个数的对象容器。数组的长度在创建时就已经确定。创建后，其长度是固定的。

#### 问题与练习：变量

* 问题的答案

The term "instance variable" is another name for non-static field.
The term "class variable" is another name for static field.
A local variable stores temporary state; it is declared inside a method.
A variable declared within the opening and closing parenthesis of a method is called a parameter.
What are the eight primitive data types supported by the Java programming language? byte, short, int, long, float, double, boolean, char
Character strings are represented by the class java.lang.String.
An array is a container object that holds a fixed number of values of a single type.

* 练习的答案

Create a small program that defines some fields. Try creating some illegal field names and see what kind of error the compiler produces. Use the naming rules and conventions as a guide.
There is no single correct answer here. Your results will vary depending on your code.

In the program you created in Exercise 1, try leaving the fields uninitialized and print out their values. Try the same with a local variable and see what kind of compiler errors you can produce. Becoming familiar with common compiler errors will make it easier to recognize bugs in your code.
Again, there is no single correct answer for this exercise. Your results will vary depending on your code.
