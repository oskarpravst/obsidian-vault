---
created: 2026-10-08
tags:
  - note
  - journal
type: "[[Lectures]]"
course: "[[Programming 1]]"
date:
week: "1"
---

# 2026-10-08 - Introduction to programming

## Main Idea

[[Programming]] is a way of turning a problem into a solution that a computer can understand. We translate problems into computing.

We can simplify the process with:
[[Problem]] -> [[Algorithm]] -> [[Program]]

[[Java]] is a [[Programming Language|programming language]]. Its source code must be compiled before we can execute it. The execution is taken care of by [[JVM]].

## Notes

# Java and computing

Computers can only perform basic operations, so we use a programming language to turn natural language into those operations that the computer then understands.

[[JShell]] provides a way of testing Java code in the terminal.

# Numeric types


The numeric type defines the store of value.
In Java we divide real number types and whole number types:

Whole number types:
1. [[Byte]]
2. [[Short]]
3. [[Int]] - has a limited capacity, the default type
4. [[Long]]
5. [[Char]] - can't go into negative

Real number types:
1. [[Float]]
2. [[Double]]

Real numbers contain a decimal point and are calculated with limited precision. That is why we usually avoid float and double if possible.

Whole numbers on the other hand are represented in a circle and  their calculations are more precise.


Integer devision produces integer result:

```
5 / 3 = 1
```

The remainder can be obtained using the modulo operator (%):

```
17 % 4 = 1 // read as 17 modulo 4 is 1.
```

If more than one type is present, Java promotes the smaller type to a wider type:

```
3 + 4.7 = 7.7

5.0 + 6 = 11.0

5.0 / 3 = 1.6666666666666667
```

Operators are evaluated according to their power and then from left to right:

```
5 / 3 * 6.0 = 6.0 // be careful it is not 10, because 5 / 3 is evaluated first
```

# Variables

A [[Variable]] has a [[Variable type|type]] and stores a [[Value]].

Declaration:

```java
int a;
```
doesn't mean that we assigned it a value.

Initialization:
```java
int a = 3;
```
we give it the first value.

Assignment:

```java
a = 3;
```

Call a variable into another variable:

```java
int b = 6 + a;
a = 5; // a's change doesn't affect b.
b = 6 + a; // b now changes.
```

Recipe for variables:
```java
variable = expression // the expression will be written into the variable.
```

The expression:
```java
a = a + 1;
```

means: calculate a + 1 and assign it to a.
(=) is assignment, not mathematical equality.

# Typecasting

A value can be forced into another type:

```java
(int) 2.7 = 2;
```

Casting from double to int removes the decimal part.

For example:

```java
int x = 5;
int y = 6;
int z = 8;

int average = (x + y + z) / 3; // = 6;
```

Solution:

```java
double average = (double) (x + y + z) / 3; // = 6.33333...

// or

double average = (x + y + z) / 3.0; // = 6.33333...
```

Recipe for typecasting:

```java
(nameOfTheType) variable/expression
```


```
jshell> int c = 3000000000L;
|  Error:
|  incompatible types: possible lossy conversion from long to int
|  int c = 3000000000L;
|          ^---------^
```

# [[Integer Overflow]]

Java's number types have a fixed length which can be exploited.

For example:

```java
1000000000 + 2000000000 = -1294967296;
```

An int is limited to:

```java
Integer.MIN_VALUE = -2147483648;

Integer.MAX_VALUE = 2147483647;
```

Calculations outside of these parameters may overflow.

Solution using long:

```java
1000000000L + 2000000000L = 3000000000;
```

# [[Char]] and [[String]]

A character is represented with whole numbers - ASCII code gives every character its own number:

```java
char c = 'A'; 
```

Characters can be typecasted and transformed:

```java
(int) 'A' = 65;
(char) 65 = 'A';
```

and:

```java
c + 1 = 66;
c * 2 = 130;
```

Characters use ('') while Strings use("")

A String represents text:

```java
String s = "tralala";
String t = "hopsasa";
s + t = tralalahopsasa;
```

Strings can be combined with numbers:
```java
s + 123 = tralala123;
```

# Expressions and statements

An expression produces a value.

Examples:

```java
6 + a;
a + 1;
5 / 3;
```

A statement performs an action.

Examples:

```java
int a = 5;
a = 1;
System.out.println(a);
```

We divide simple and complex statements.

# Blocks and scope

[[Block|Blocks]] give a program a structure and a hierarchy. 
They are defined with { }.

Indentations are for readability only. The compiler ignores them.

Every variable exists only in the block it was defined in. There can be more than one block.

```java
{
	int b = 10;
	System.out.println(b);
}
```

b cannot be used outside this block. This creates a local scope for variables to be used and then be forgotten.

# Compilation and execution

We must compile Java code into a lower order language than Java. This then gets executed by [[JVM]].

Recipe for conversion:

FileName.java -> javac -> bytecode -> JVM -> program execution

Compile:
```
javac FileName.java
```

Run:
```
java FileName
```

A syntax error can be found by the compiler(javac) - an error:

```java
Prvi.java:5: error: ';' expected
```

we can see the line number and the file the error happened on.

A program can also compile and fail during execution - an exception:

```java
int a = 3 / 0;
// Exception in thread "main" java.lang.ArithmeticException: / by zero
```

We always fix only the first error and then recompile!

# Input and output

Input comes from a keyboard/file.
Output comes from the screen/file.

Print:

```java
System.out.println(b); // jumps into the next line
System.out.printb); // doesn't
```

To read user input:

```java
import java.util.Scanner;
Scanner sc = new Scanner(System.in);
```


Program DateOfBirth:

```java
import java.util.Scanner;

public class DateOfBirth{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        System.out.print("Vnesi leto rojstva: ");
        int letoRojstva = sc.nextInt();


        int starost = 2026 - letoRojstva;
        System.out.println("Letos praznujes " + starost + ". rojstni dan.");

    }
}
```

If the user inputs a string we get an exception:

```java
Exception in thread "main" java.util.InputMismatchException
```

# Testing

Programs are tested using test cases.

Expected input -> expected output

Automatic testing checks if the program produced the expected results for the provided test cases.


## Questions
- [ ] Why is there no error with integer overflow? In maths we imagine the numbers in a straight line while in Java the numbers are represented in a circle.
- [ ] Why are the numbers represented in a circle?
- [ ] Which type of number dominates? A long wins over int, so the answer is long type:
```java
1000000000L + 2000000000 = 3000000000; // long
```


- [ ] When is calculation with ASCII useful? When dealing with the alphabet:
```java
'K' - 'A' = 10;
```

## Connections


## Sources
