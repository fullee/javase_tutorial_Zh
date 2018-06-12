# 语言基础

## 变量
前面你已经了解到对象存储的状态在它的字段中。然而，在JPL中也使用“变量（variable）”。这一节讨论这种关系，同时介绍变量的命名规则约定,基本数据类型(primitive types, character strings, and arrays),默认值,字面值。

```java
int cadence = 0;
int speed = 0;
int gear = 1;
```
在[什么是对象]()这一节讨论了字段，但是你可能仍然有几个问题，例如：对象的命名规则和约定是什么？除了int类型还有什么类型？字段被声明时是否必须被初始化？如果没有显式的赋值初始化时是否会有默认值?我们将在这一节讨论这些答案，在此之前，你必须首先意识到一些技术上的区别。在JPL中，术语“字段”和“变量”两者都会使用；这在新开发人员中是一个常见的困惑来源，因为两者似乎常常指的是同一件事。

JPL定义了以下类型的变量:
* Instance Variables (Non-Static Fields) Technically speaking, objects store their individual states in "non-static fields", that is, fields declared without the static keyword. Non-static fields are also known as instance variables because their values are unique to each instance of a class (to each object, in other words); the currentSpeed of one bicycle is independent from the currentSpeed of another.
* Class Variables (Static Fields) A class variable is any field declared with the static modifier; this tells the compiler that there is exactly one copy of this variable in existence, regardless of how many times the class has been instantiated. A field defining the number of gears for a particular kind of bicycle could be marked as static since conceptually the same number of gears will apply to all instances. The code static int numGears = 6; would create such a static field. Additionally, the keyword final could be added to indicate that the number of gears will never change.
* Local Variables Similar to how an object stores its state in fields, a method will often store its temporary state in local variables. The syntax for declaring a local variable is similar to declaring a field (for example, int count = 0;). There is no special keyword designating a variable as local; that determination comes entirely from the location in which the variable is declared — which is between the opening and closing braces of a method. As such, local variables are only visible to the methods in which they are declared; they are not accessible from the rest of the class.
* Parameters You've already seen examples of parameters, both in the Bicycle class and in the main method of the "Hello World!" application. Recall that the signature for the main method is public static void main(String[] args). Here, the args variable is the parameter to this method. The important thing to remember is that parameters are always classified as "variables" not "fields". This applies to other parameter-accepting constructs as well (such as constructors and exception handlers) that you'll learn about later in the tutorial.

Having said that, the remainder of this tutorial uses the following general guidelines when discussing fields and variables. If we are talking about "fields in general" (excluding local variables and parameters), we may simply say "fields". If the discussion applies to "all of the above", we may simply say "variables". If the context calls for a distinction, we will use specific terms (static field, local variables, etc.) as appropriate. You may also occasionally see the term "member" used as well. A type's fields, methods, and nested types are collectively called its members.

本教程的剩余部分在讨论字段和变量时使用下面的指导原则。如果我们在讨论“一般的字段”（不包括本地变量和参数），我们会简单的说“字段”。如果在讨论“所有上述”，我们可以简单的说“变量”。如果上下文需要区分，我们酌情使用特定的数据（静态变量，局部变量等）。偶尔可能会看到“成员”这个词。类型的字段，方法，嵌套类型统称为类的成员。

### 命名
Every programming language has its own set of rules and conventions for the kinds of names that you're allowed to use, and the Java programming language is no different. The rules and conventions for naming your variables can be summarized as follows:

每一种编程语言都有自己的一套规则和惯例，适用于允许使用的名称类型。JPL也一样。变量的命名规则和约定如下：
* Variable names are case-sensitive. A variable's name can be any legal identifier — an unlimited-length sequence of Unicode letters and digits, beginning with a letter, the dollar sign "$", or the underscore character "_". The convention, however, is to always begin your variable names with a letter, not "$" or "_". Additionally, the dollar sign character, by convention, is never used at all. You may find some situations where auto-generated names will contain the dollar sign, but your variable names should always avoid using it. A similar convention exists for the underscore character; while it's technically legal to begin your variable's name with "_", this practice is discouraged. White space is not permitted.
* 变量名区分大小写。
* Subsequent characters may be letters, digits, dollar signs, or underscore characters. Conventions (and common sense) apply to this rule as well. When choosing a name for your variables, use full words instead of cryptic abbreviations. Doing so will make your code easier to read and understand. In many cases it will also make your code self-documenting; fields named cadence, speed, and gear, for example, are much more intuitive than abbreviated versions, such as s, c, and g. Also keep in mind that the name you choose must not be [a keyword or reserved word.](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/_keywords.html)
* If the name you choose consists of only one word, spell that word in all lowercase letters. If it consists of more than one word, capitalize the first letter of each subsequent word. The names gearRatio and currentGear are prime examples of this convention. If your variable stores a constant value, such as static final int NUM_GEARS = 6, the convention changes slightly, capitalizing every letter and separating subsequent words with the underscore character. By convention, the underscore character is never used elsewhere.

### 原始数据类型

### 数组


## 操作符
这一节描述JPL的操作符。首先给出给常用的操作符，然后是不常用的操作符。每个讨论都包含了可以被编译和运行的源代码。
## 表达式，段，块
运算符可以被用于构建表达式,计算值。表达式是组成语句的核心组件。语句可以组成代码块。本节使用前面的代码介绍表达式，语句，代码块。
## 控制流段
本节介绍JPL中的控制流程语句。包含判断循环分支语句，它可以是你的程序有条件的执行。