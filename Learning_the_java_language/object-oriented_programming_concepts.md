# 面向对象编程概念

如果你以前没有使用过面向对象编程语言，在开始编程之前你需要学习几个基本的概念。这一章将会介绍objects, classes, inheritance, interfaces, and packages。每一节的重点是如何将这些概念同现实世界联系起来，同时熟悉JPL的语法。

## 1.什么是对象？

> 对象包含相关状态和行为，软件对象也是模拟真实世界中的对象。这一节解释了状态和行为如何在对象中表示，介绍了数据封装的概念，并说明用这种方式设计软件的好处。

Objects是理解面向对象的关键，环顾四周，你会发现现实中有很多对象的例子：你的狗，桌子，电视。。。
现实中的对象有两个特征：他们都有状体和行为。例如，狗的状态（name，color，breed，hungry）和行为（狂吠，摆尾）。自行车也有状态（车轮，踏板，车速）和行为（改变车轮，更换踏板，刹车）。对比现实世界中的对象，是学习面向对象编程的一种极好的方式。

现在花几分钟看一下你的周围，你看到每一个对象都想两个问题“这个对象可能处于什么状态？”和“这个对象将有怎样的行为？”。把你观察的写下来。你会发现现实中的对象复杂度是不同的。你桌上的台灯可能只有两个状态（开和关）两种行为（打开和关闭），而你桌上的收音机除了这些状态可能还有音量、频道和更多的行为调大音量，减小音量，扫描...,你还会发现一些对象可能包含了另一些对象。

![一个软件对象](../images/2_1/concepts-object.gif)

软件对象同现实中对象类似，也包含状态和行为。状态存储在对象的字段（fields）中，行为对应方法（methods）。方法操作对象内部的状态，用于对象和对象之间进行通信。数据封装是面向对象的基本原则之一，具体就是隐藏对象内部的状态，暴漏需要交互的方法。

以一辆自行车为例：

![自行车模型](../images/2_1/concepts-bicycleObject.gif)

通过属性状态（当前速度，当前踏板节奏和当前档位）和改变该状态的方法，对象决定了外界如何使用它。 例如，如果自行车只有6个档位，则更换档位的方法可以拒绝任何小于1或大于6的值。

将代码映射为对象由下面几个好处：

1. 模块化: 对象的源代码可以独立于其他对象的源代码编写和维护。 一旦创建，一个对象可以很容易地在系统内传递。
2. 信息隐藏: 通过对象的方法交互, 对象的内部实现对外是隐藏的。
3. 代码复用: 如果对象已经存在 (假设是其他的开发者编写), 你可以将这个对象应用到你的代码中。 可以由特定领域的专业人员实现/测试/调试复杂的特定任务的对象，然后您可以信任它们在自己的代码中运行。例如，jdk中的java.lang.Math类实现一下复杂的数学运算。
4. 易于调试和插件化: 如果个别对象出现问题，你可以在你的应用中将其删除，然后添加一个不同的对象来取代它。类似于现实中的机械问题，如果螺栓损坏，就更换它，而不是整台机器。

## 2.什么是类？

> 类是对象创建的蓝图或者是原型。本节定义了一个模型，该模型是对真实世界对象的状态和行为进行建模。这个类故意使用最基础的知识，展示一个简单的类如何能够干净的建模态和行为。

在现实世界中，你会经常发现很多单独的物体都属于同一类。 可能有成千上万的自行车都相同的品牌和型号。 每辆自行车都由同一套模板构成，因此包含相同的部件。 在面向对象的术语中，我们说你的自行车是一类称为自行车的物体的一个实例。 类是创建对象的蓝图。

下面的自行车课是一种可能的自行车实施方式：

```java
class Bicycle {

    int cadence = 0;
    int speed = 0;
    int gear = 1;

    void changeCadence(int newValue) {
         cadence = newValue;
    }

    void changeGear(int newValue) {
         gear = newValue;
    }

    void speedUp(int increment) {
         speed = speed + increment;
    }

    void applyBrakes(int decrement) {
         speed = speed - decrement;
    }

    void printStates() {
         System.out.println("cadence:" +
             cadence + " speed:" +
             speed + " gear:" + gear);
    }
}
```

Java编程语言的语法对你来说看起来很新，但这个类的设计是基于前面对自行车对象的讨论。 字段cadence, speed, 以及 gear表示对象的状态，方法（changeCadence，changeGear，speedUp等）与外部的交互。

您可能已经注意到Bicycle类不包含main方法。 那是因为它不是一个完整的应用程序; 它可能只是应用程序的自行车模型。创建和使用新的Bicycle对象的属于应用程序中的其他类。

这里的BicycleDemo创建了两个不同的对象，分别调用它们的方法:

```java
class BicycleDemo {
    public static void main(String[] args) {

        // Create two different
        // Bicycle objects
        Bicycle bike1 = new Bicycle();
        Bicycle bike2 = new Bicycle();

        // Invoke methods on
        // those objects
        bike1.changeCadence(50);
        bike1.speedUp(10);
        bike1.changeGear(2);
        bike1.printStates();

        bike2.changeCadence(50);
        bike2.speedUp(10);
        bike2.changeGear(2);
        bike2.changeCadence(40);
        bike2.speedUp(10);
        bike2.changeGear(3);
        bike2.printStates();
    }
}
```

打印两个自行车实例的状态：

```shell
cadence:50 speed:10 gear:2
cadence:40 speed:20 gear:3
```

## 3.什么是继承？

> 继承为你的软件提供了一种强大并且自然的组织结构。本节解释了一个类如何从其父类中继承状态和行为。

不同种类的物体通常具有一定的共同点。 例如，山地自行车，公路自行车和双人自行车都具有自行车的特征（当前速度，当前踏板节奏，当前档位）。 然而每一种自行车也有不同的特征：双人自行车有两个座位和两组把手; 公路自行车有把手; 一些山地自行车有一个额外的链环，给他们一个较低的传动比。

面向对象编程允许把一些通用的状态和行为继承自其它的类。在这个例子中，Bicycle将变成MountainBike, RoadBike以及 TandemBike的父类。在JPL中每个类只允许有一个直接父类。

![A hierarchy of bicycle classes](../images/2_1/concepts-bikeHierarchy.gif)

创建子类的语法很简单。在声明类时使用`extends`关键字，后面跟上要继承的类的名字：

```java
class MountainBike extends Bicycle {

    // new fields and methods defining
    // a mountain bike would go here

}
```

MountainBike将会拥有与Bicycle的领域和方法，同时MountainBike还拥有独特的功能。 这使得您的子类的代码更加易读。 但是，必须注意正确记录每个超类定义的状态和行为，因为该代码不会出现在每个子类的源文件中。

## 4.什么是接口

> 接口是类和外部世界之间的契约。当一个类实现一个接口时，它就承诺提供那个接口发布的行为。本节定义一个简单的接口，并解释要实现它的类所作的必要的修改。

你现在已经了解，对象通过方法与外界的交互。方法就是对象与外界的接口; 例如，电视机前面的按钮就是您和电视机内部之间的接口。 您按下“电源”按钮打开和关闭电视机。

In its most common form, an interface is a group of related methods with empty bodies. A bicycle's behavior, if specified as an interface, might appear as follows:

接口是一组没有方法体的方法,自行车接口如下：

```java
interface Bicycle {

    //  wheel revolutions per minute
    void changeCadence(int newValue);

    void changeGear(int newValue);

    void speedUp(int increment);

    void applyBrakes(int decrement);
}
```

为了实现这个接口，你的类的名字会改变（例如，一个特定品牌的自行车，例如ACMEBicycle），你可以在类声明中使用`implements`关键字:

```java
class ACMEBicycle implements Bicycle {

    int cadence = 0;
    int speed = 0;
    int gear = 1;

   // The compiler will now require that methods
   // changeCadence, changeGear, speedUp, and applyBrakes
   // all be implemented. Compilation will fail if those
   // methods are missing from this class.

    void changeCadence(int newValue) {
         cadence = newValue;
    }

    void changeGear(int newValue) {
         gear = newValue;
    }

    void speedUp(int increment) {
         speed = speed + increment;
    }

    void applyBrakes(int decrement) {
         speed = speed - decrement;
    }

    void printStates() {
         System.out.println("cadence:" +
             cadence + " speed:" +
             speed + " gear:" + gear);
    }
}
```

Implementing an interface allows a class to become more formal about the behavior it promises to provide. Interfaces form a contract between the class and the outside world, and this contract is enforced at build time by the compiler. If your class claims to implement an interface, all methods defined by that interface must appear in its source code before the class will successfully compile.

 接口是类和外界之间的契约，实现接口的类对它承诺提供的方法变得更加正式。这个契约在编译时执行。 如果您的类声明实现了一个接口，那么在该类编译之前，必须实现该接口定义的全部方法。

> 备注：To actually compile the ACMEBicycle class, you'll need to add the public keyword to the beginning of the implemented interface methods. You'll learn the reasons for this later in the lessons on Classes and Objects and Interfaces and Inheritance.
要实际编译ACMEBicycle类，您需要将public关键字添加到实现的接口方法的开头。 稍后您将在[类和对象](https://docs.oracle.com/javase/tutorial/java/javaOO/index.html)以及[接口和继承](https://docs.oracle.com/javase/tutorial/java/IandI/index.html)的课程中了解其原因。

## 5.什么是包？

> 包是一种组织类和继承的逻辑方式。将代码放到包中可以使大型软件项目易于管理。本节解释这为什么有用，同时介绍Java平台提供的API。

包是一个命名空间，它组织一组相关的类和接口。您可以将软件包等同于文件夹。您可以将HTML页面保存在一个文件夹中，另一个文件中包含图像，另一个文件夹中包含脚本或应用程序。因为使用JPL编写的软件可能由数千个类构成, 因此使用包来组织和管理类和接口非常有意义。

Java平台提供了一个强大的类库（包的集合）用于你的应用。这个库就是众所周知的“API（Application Programming Interface）”。Java API提供了通用的编程接口。例如，String对象包含的状态和行为是为了处理字符串，File对象使开发者更容易在文件系统上创建、删除、查看、合并、修改文件。Socket对象允许创建和使用socket;GUI对象控制按钮和复选框以及与图形用户界面相关的其它内容。 有几千个类可供选择。 这使得开发者可以专注于特定应用程序的设计，而不是使其工作所需的基础架构。

这份[Java API规范](https://docs.oracle.com/javase/8/docs/api/index.html)列出了JavaSE全部的包，接口，类字段以及方法。作为Java开发者，这将是你最常用的文档之一。

## 6.问题·练习

> 利用这些问题和练习测试你对objects，classes，inheritance，interfaces和包的理解。

Questions
Real-world objects contain ___ and ___.
A software object's state is stored in ___.
A software object's behavior is exposed through ___.
Hiding internal data from the outside world, and accessing it only through publicly exposed methods is known as data ___.
A blueprint for a software object is called a ___.
Common behavior can be defined in a ___ and inherited into a ___ using the ___ keyword.
A collection of methods with no implementation is called an ___.
A namespace that organizes classes and interfaces by functionality is called a ___.
The term API stands for ___?
Exercises
Create new classes for each real-world object that you observed at the beginning of this trail. Refer to the Bicycle class if you forget the required syntax.
For each new class that you've created above, create an interface that defines its behavior, then require your class to implement it. Omit one or two methods and try compiling. What does the error look like?

Answers to Questions
Real-world objects contain state and behavior.
A software object's state is stored in fields.
A software object's behavior is exposed through methods.
Hiding internal data from the outside world, and accessing it only through publicly exposed methods is known as data encapsulation.
A blueprint for a software object is called a class.
Common behavior can be defined in a superclass and inherited into a subclass using the extends keyword.
A collection of methods with no implementation is called an interface.
A namespace that organizes classes and interfaces by functionality is called a package.
The term API stands for Application Programming Interface.
Answers to Exercises
Your answers will vary depending on the real-world objects that you are modeling.
Your answers will vary here as well, but the error message will specifically list the required methods that have not been implemented.