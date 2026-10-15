---
created: 2026-10-15
tags:
  - note
  - journal
type: "[[Lectures]]"
course: "[[Programming 1]]"
date: 2026-10-15
week: "2"
---

# 2026-10-15 - Control Structures

## Main Idea

Control structures (*krmilni konstrukti*) determine the order in which the statements of a program are executed. Statements are executed strictly in sequence; a [[Conditional Statement|conditional statement]] (`if`) executes a part only when a condition holds, and loops (`while`, `do`, `for`) repeat a part of the program. The condition is always a [[Boolean|logical expression]] of type `boolean`.

## Notes

### Sequence of statements (*zaporedje stavkov*)

Statements in a program are executed strictly one after another.

### Conditional statement (`if`)

A conditional statement (*pogojni stavek*) is executed only if a certain condition is met.

```java
if (pogoj) {
	stavki...
}

// only a single statement may be written without {}
if (pogoj)
	stavek
```

Example:

```java
if (pogoj){ // if true, this inside will be executed
	stavki
}

// if not true, we go straight here
```

### `if` – `else`

```java
if (pogoj){
	stavki1 // if met: here and then out (not into else)
} else{
	stavki2 // if not met, the if part is skipped and only this runs
}

// all of this is just 1 conditional statement
```

### `else if` – chaining conditions

Statements contain sub-statements, which is why we can often delete the `{}`. This turns a nested `if` inside an `else` into `else if`:

```java
if (prvo > drugo){
    System.out.println("Prvo je vecje");
} else if (prvo < drugo){
    System.out.println("Drugo je vecje");
} else{
    System.out.println("Stevili sta enaki");
}
```

`else if` chains conditions (*veriženje pogojev*):

```text
if
else if
else if
else if
...
else
```

In such a chain only one part (block) is ever executed.

Always initialize variables before using them.

### Logical expressions and the `boolean` type

The condition in an `if` statement is a logical expression (*logični izraz*), e.g. `3 < 4` – an expression with its own value: either true or false. The name [[Boolean|boolean]] comes from Boolean algebra (George Boole).

If `true`, the `if` part is executed; if `false`, the `else` part is executed.

```java
boolean b = 4 > 5
b = false

c = !b
c = true
```

Equality:

```java
leva == desna

3 == 3 // true

3 = 3 // error

3 == 3.0 // true, because in operations mixing int and double, the int is converted to double
```

### Logical operators (*logični operatorji*)

```java
p && q // and

p || q // or

!p // not
```

`&&` (and) has precedence over `||` (or).

**[[Short-circuit Evaluation|Short-circuit evaluation]]** (*kratkostično izvajanje*):

```java
p && q // if p is false, the program doesn't even check q

p || q // if p is true, the program doesn't even check q
```

**The compiler only sees types:**

```java
import java.util.Scanner;

public class Vecje {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        boolean a = (3 < 4) || (1 / 0 == 1);
        // boolean a = (3 < 4) || (b == c); // undefined variables, so it wouldn't compile
        System.out.println(a);
    }
}
```

The first line compiles, because the compiler only checks that both sides are of type `boolean`. It also runs without an `ArithmeticException`: `3 < 4` is `true`, so with short-circuit evaluation `1 / 0` is never evaluated. Output: `true`.

The second line does not compile, because `b` and `c` are not declared (and `a` would be declared twice), so it is commented out.

### `while` loop (*dokler*)

While the condition is met, it repeats. `while` means it is a [[While Loop|loop]].

```java
while (pogoj){ // checks like an if statement
	stavki // we don't move on, but return to checking the condition
}
```

If the variable in the condition never changes, we get an [[Infinite Loop|infinite loop]] (*neskončna zanka*). `Ctrl + C` stops an infinite loop.

Conceptually, every variable has its own meaning, so it is better to create a new variable.

### `op=` operators

```text
stevec = stevec + 1
stevec += 1

vsota = vsota + stevilo
vsota += stevilo

in general:
variable op= something
```

### `++` and `--` operators

When increasing by 1:

```text
a = a + 1
a += 1
++a
a++

same for -
```

When it is part of a larger expression:

```text
int a = 5
int b = ++a;  // a is increased by 1, then 6 is copied into b

int x = 5
int y = x++;  // 5 is copied into y, then x is increased by 1
```

Example in [[JShell]]:

```text
jshell> int a = 10;
a ==> 10

jshell> int b = a++;
b ==> 10

jshell> a
a ==> 11

jshell> int c = ++a;
c ==> 12

jshell> a
a ==> 12
```

But:

```text
jshell> int c = a + 1;
c ==> 13

jshell> a
a ==> 12
```

### `do` loop

```java
do {
	stavki
} while (pogoj);
```

In a [[Do-while Loop|`do` loop]] the statements are executed first, then the condition is checked (the loop always runs at least once).

Body → condition (the condition is written at the end).

### `for` loop

```java
for (inicializacija; pogoj; posodobitev){
	stavki
}
```

The [[For Loop|for loop]] is a shorter way of writing a `while` loop tied to a counter (*števec*).

## Code

### Larger of two numbers

Print which of the two numbers read is larger:

```java
import java.util.Scanner;

public class Vecje {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        System.out.print("Vnesi prvo stevilo: ");
        int prvo = sc.nextInt();
        System.out.print("Vnesi drugo stevilo: ");

        int drugo = sc.nextInt();

        if (prvo > drugo){
            System.out.println("Prvo je vecje");
        } else{
            System.out.println("Drugo je vecje");
        }
    }
}
```

If `prvo = 5` and `drugo = 5`, it prints that the second one is larger, because the `if` condition was not met.

Updated version:

```java
import java.util.Scanner;

public class Vecje2 {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        System.out.print("Vnesi prvo stevilo: ");
        int prvo = sc.nextInt();
        System.out.print("Vnesi drugo stevilo: ");

        int drugo = sc.nextInt();

        if (prvo > drugo){
            System.out.println("Prvo je vecje");
        } else{
            // ce pridemo do tod, vemo da velja da je prvo <= drugo
            // se vedno pa je lahko prvo < drugo ali prvo == drugo
            if (prvo < drugo){
                System.out.println("Drugo je vecje");
            } else{
                System.out.println("Stevili sta enaki");
            }
        }
    }
}
```

With `else if` (`Vecje3`) – see the section "`else if` – chaining conditions" above.

### Grade (*ocena*)

```java
import java.util.Scanner;

public class Ocena {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int tocke = sc.nextInt();
        int ocena = 0;

        if (tocke >= 90){
            ocena = 10;
        } else if (tocke >= 80){ // && tocke < 90 ker je to ze v prejsnem pogoju
            ocena = 9;
        } else if (tocke >= 70){
            ocena = 8;
        } else if (tocke >= 60){
            ocena = 7;
        } else if (tocke >= 50){
            ocena = 6;
        } else {
            ocena = 5;
        }
        System.out.println(ocena);
    }
}
```

The grading scale follows the slides: 90+ → 10, 80+ → 9, 70+ → 8, 60+ → 7, 50+ → 6, otherwise 5. (In class the condition `tocke >= 70` was written twice, so grade 7 was never reached.)

System [[Pipe|pipe]]:

```bash
echo 75 | java Ocena
```

Advantage: quicker.

If I enter too many (101) or too few (-5) points, it doesn't work, so we add a check:

```java
import java.util.Scanner;

public class Ocena {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int tocke = sc.nextInt();

        if(tocke > 100 || tocke < 0){
            System.out.println("napaka");
        } else{
            int ocena = 0;

            if (tocke >= 90){
                ocena = 10;
            } else if (tocke >= 80){ // && tocke < 90 ker je to ze v prejsnem pogoju
                ocena = 9;
            } else if (tocke >= 70){
                ocena = 8;
            } else if (tocke >= 60){
                ocena = 7;
            } else if (tocke >= 50){
                ocena = 6;
            } else {
                ocena = 5;
            }
            System.out.println(ocena);
        }
    }
}
```

### Leap year (*prestopno leto*)

A program that prints whether the year read is a leap year:

```java
import java.util.Scanner;

public class PrestopnoLeto {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int leto = sc.nextInt();

        if (leto % 400 == 0 || leto % 4 == 0 && leto % 100 != 0){
            System.out.println("prestopno");
        }
        else {
            System.out.println("ni prestopno");
        }
    }
}
```

### Sequence (*zaporedje*) with `while`

```java
import java.util.Scanner;

public class Zaporedje {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int spMeja = sc.nextInt();
        int zgMeja = sc.nextInt();

        int stevilo = spMeja;

        while (stevilo <= zgMeja) {

            System.out.println(stevilo);
            stevilo = stevilo + 1 ;
        }
    }
}
```

```bash
echo 5 10 | java Zaporedje
```

Infinite loop – because `stevilo` never changes:

```java
while (stevilo <= zgMeja) {

    System.out.println(stevilo);
    // stevilo se ne spreminja
}
```

### Running sum (*sprotno seštevanje*)

Add numbers until the sum exceeds 42:

```java
import java.util.Scanner;

public class Trgovina {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int vsota = 0; // vsota doslej vnesenih stevil

        while (vsota <= 42) {
            System.out.print("vnesi stevilo: ");
            int stevilo = sc.nextInt();
            vsota = vsota + stevilo;

            System.out.println(vsota);
        }
    }
}
```

The program reads 5 numbers:

```java
import java.util.Scanner;

public class Trgovina2 {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int vsota = 0; // vsota doslej vnesenih stevil
        int stVnosov = 0;

        while (stVnosov < 5) {
            System.out.print("vnesi stevilo: ");
            int stevilo = sc.nextInt();

            stVnosov = stVnosov + 1;
            vsota = vsota + stevilo;

            System.out.println(vsota);
        }
    }
}
```

Why is `stVnosov` declared outside the loop? Because otherwise it would be reset on every pass through the loop.

Combining both conditions:

```java
import java.util.Scanner;

public class Trgovina3 {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int vsota = 0; // vsota doslej vnesenih stevil
        int stVnosov = 0;

        // while (stVnosov < 5 || vsota <= 42) {
        while (stVnosov < 5 && vsota <= 42) {

            System.out.print("vnesi stevilo: ");
            int stevilo = sc.nextInt();

            stVnosov = stVnosov + 1;
            vsota = vsota + stevilo;

            System.out.println(vsota);
        }
    }
}
```

### Sum of all input numbers

With an external input file we can read the input even though we don't know how long it is:

```java
import java.util.Scanner;

public class SestejVhod {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int vsota = 0;

        // sc.hasNextInt() vrne true ce je na vhodu se kaksno stevilo
        while (sc.hasNextInt()){
            int stevilo = sc.nextInt();
            vsota = vsota + stevilo;
        }
        System.out.println(vsota);
    }
}
```

### Universe (*vesolje*) with `do`

```java
import java.util.Scanner;

public class Vesolje {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        //while

        // System.out.print("Vnesi odgovor na vprasanje o ...");
        // int odgovor = sc.nextInt();

        // while (odgovor != 42){
        //     System.out.print("Vnesi odgovor na vprasanje o ...");
        //     odgovor = sc.nextInt();
        // }

        // do

        int odgovor;

        do {
            System.out.print("Vnesi odgovor na vprasanje o ...");
            odgovor = sc.nextInt();
        } while (odgovor != 42); // izven bloka zato mormo se enkrat definirat
    }
}
```

### Sequence with `for`

```java
import java.util.Scanner;

public class Zaporedje {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int spMeja = sc.nextInt();
        int zgMeja = sc.nextInt();

        for (int stevilo = spMeja; stevilo <= zgMeja; stevilo++){
            System.out.println(stevilo);
        }
    }
}
```

## Questions

- [ ] 

## Connections

- Course: [[Programming 1]]
- Previous lecture: [[2026-10-08 - Introduction to programming - 1]] – variables, blocks, `Scanner`, compiling
- Logical operators and precedence: [[2026-10-05 - Propositional Logic - 1]], [[2026-10-11 - Boolean Algebra - 1]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/03_krmilniKonstrukti_h.pdf|03 Krmilni konstrukti]] (Luka Fürst)
- Class code: `programming_1/class/2/` (`Vecje*.java`, `Ocena.java`, `PrestopnoLeto.java`, `Zaporedje*.java`, `Trgovina*.java`, `SestejVhod.java`, `Vesolje.java`, `Primer.java`)
