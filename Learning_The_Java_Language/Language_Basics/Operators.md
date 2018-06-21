现在你已经学习了如何声明和初始化变量。你可能会想用它们来做些什么，学习JPL中的操作符将是一个很好的开始。运算符是在一个、两个或三个操作数上执行特定操作的特殊符号，然后返回结果。

As we explore the operators of the Java programming language, it may be helpful for you to know ahead of time which operators have the highest precedence. The operators in the following table are listed according to precedence order. The closer to the top of the table an operator appears, the higher its precedence. Operators with higher precedence are evaluated before operators with relatively lower precedence. Operators on the same line have equal precedence. When operators of equal precedence appear in the same expression, a rule must govern which is evaluated first. All binary operators except for the assignment operators are evaluated from left to right; assignment operators are evaluated right to left.

接下来看一下JPL中的运算符，运算符有优先级。下表按照优先级列出，自上而下优先级越来越低。当具有相同优先级的运算符出现在相同的表达式中时，必须有一个规则来决定首先计算哪个运算符。除赋值操作符外，所有二进制操作符都从左到右进行计算;赋值操作符从右到左进行计算。

Operators| Precedence
----|----
postfix| expr++ expr--
unary| ++expr --expr +expr -expr ~ !
multiplicative| * / %
additive|+ -
shift(移位)|<< >> >>>
relational|< > <= >= instanceof
equality(判等)|== !=
bitwise AND|&
bitwise exclusive OR|^
bitwise inclusive OR|`|`
logical AND|&&
logical OR|`||`
ternary(三元)|? :
assignment|= += -= *= /= %= &= ^= |= <<= >>= >>>=

通常, certain operators tend to appear more frequently than others; for example, the assignment operator "=" is far more common than the unsigned right shift operator ">>>". With that in mind, the following discussion focuses first on the operators that you're most likely to use on a regular basis, and ends focusing on those that are less common. Each discussion is accompanied by sample code that you can compile and run. Studying its output will help reinforce what you've just learned.

### 赋值、算数、一元运算

#### 一个简单的赋值运算

最常用的运算符就是简单的赋值运算符即“=”，等号的右边是值，左边是操作数。

```java
 int cadence = 0;
 int speed = 0;
 int gear = 1;
```

#### 算数操作符

JPL中提供的算数操作包括：加减乘除。于数学中的运算是一致的。对你来说新的唯一符号是“%”，它将一个操作数除以另一个操作数，并将余数作为结果返回。

Operator| Description
----|----
+| Additive operator (also used for String concatenation)
-| Subtraction operator
*| Multiplication operator
/| Division operator
%| Remainder operator

ArithmeticDemo类测试算数操作符：

```java
class ArithmeticDemo {

    public static void main (String[] args) {

        int result = 1 + 2;
        // result is now 3
        System.out.println("1 + 2 = " + result);
        int original_result = result;

        result = result - 1;
        // result is now 2
        System.out.println(original_result + " - 1 = " + result);
        original_result = result;

        result = result * 2;
        // result is now 4
        System.out.println(original_result + " * 2 = " + result);
        original_result = result;

        result = result / 2;
        // result is now 2
        System.out.println(original_result + " / 2 = " + result);
        original_result = result;

        result = result + 8;
        // result is now 10
        System.out.println(original_result + " + 8 = " + result);
        original_result = result;

        result = result % 7;
        // result is now 3
        System.out.println(original_result + " % 7 = " + result);
    }
}
```

输出：

```java
1 + 2 = 3
3 - 1 = 2
2 * 2 = 4
4 / 2 = 2
2 + 8 = 10
10 % 7 = 3
```