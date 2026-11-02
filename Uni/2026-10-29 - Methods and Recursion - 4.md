---
type: "[[Lectures]]"
course: "[[Programming 1]]"
date: 2026-10-29
week: "4"
---

# 2026-10-29 - Methods and Recursion

## Main Idea

The lecture started with a detail about the assignment operators (`=`, `+=`, …): an assignment is also an expression with a value, and operators have a [[Operator Precedence|precedence]] (*prioriteta*) and an [[Associativity|associativity]] (*asociativnost*).

The main topic were [[Method|methods]] (*metode*): we take a piece of code, give it a name, and run it by calling that name. The examples:

- a cross pattern of `+` (*Plus*), first with repeated code, then with methods, [[Parameter|parameters]] (*parametri*) and a method with several parameters,
- the perimeter of a rectangle (*Obseg*) as a method that returns a value with [[Return Statement|`return`]],
- prime numbers (*praštevila*) with a method `jePrastevilo`,
- amicable numbers (*prijateljska števila*),
- the [[Fibonacci Sequence|Fibonacci sequence]] with [[Recursion|recursion]] (*rekurzija*).

## Notes

### Assignment as an expression (*zanimivost: operator `=`*)

The assignment operators (`=`, `+=`, …) appear in statements (*nastopajo v stavkih*):

```java
int a = 7;
a = 10;
a += 20;
```

They can also appear as part of an expression (*lahko nastopajo tudi kot del izraza*), because the equals sign can be part of an expression:

```java
int b = 0;
b = (a = 3) + 9;   // a = 3, b = 12

a = b = 10;
a = (b = 10);      // the same: right associativity (desna asociativnost)
```

- The **effect** (*učinek*) of the expression `a = 3` is that `a` gets the value 3.
- The **value** (*vrednost*) of the expression is the new value of the left side.

The book covers the bitwise operators (*bitni operatorji*): very useful, read them on your own.

### Precedence (*prioriteta*)

Some operators bind more strongly than others (*nekateri operatorji so močnejši od drugih*), e.g. `*` before `+`. Which of these is `2 << 3 - 1`?

```java
(2 << 3) - 1
// or
2 << (3 - 1)
```

### Associativity (*asociativnost*)

Associativity tells how operators on the same precedence level are grouped:

```java
a op b op c
(a op b) op c   // left associative (levo asociativno)
a op (b op c)   // right associative (desno asociativno) – the assignment operators
```

### Methods (*metode*)

We take a piece of code and give it a name; then we call the name and the code is executed. This is how we make a [[Method|method]] (a function, *funkcija*). A method is a piece of code that has its own name and can be reused many times.

`main` is also a method, the main method (*glavna metoda*):

```java
public static void main // the main method (glavna metoda)
```

The first *Plus* program (under Code) repeats the same loop twice; with a method `navpicniKrak` that part is written only once.

### Parameters and arguments (*parametri in argumenti*)

Arguments go into the parameters (*argumenti gredo v parametre*):

```java
public static void metoda(T1 p1, T2 p2, ..., Tn pn) { // type and parameter
    ...
}

public static void ...(...) {
    metoda(a1, a2, ..., an); // arguments
}
```

- The name of a parameter can be the same as the name of the argument, because they are separate variables (*ker sta ločeni spremenljivki*).
- The types must be assignable (*tipi morajo biti priredljivi*):

```java
public static void narisi(int n) {
    ...
}

int a = 3;
narisi(a);   // 3 is copied into n

long b = 7;
narisi(b);   // this would be an error: a long cannot be copied into an int
```

Because the parameter is only a copy, changing it in the method does not change the argument:

```java
public static void main(String[] args) {
    int a = 42;
    metoda(a);
    System.out.println(a);
}

public static void metoda(int a) {
    a++;
    System.out.println(a);
}
```

This prints `43` and then `42`.

### `return`

Methods can return values: the caller (*klicatelj*) gets the result of the computation.

```java
return 14; // leave the method (end its execution); the method call is replaced by the returned value
```

Instead of `void`, the method header contains the type `T` of the returned value. The value in `return izraz;` must be assignable (*priredljiv*) to `T`, and the result can be stored in a variable whose type `T` is assignable to (e.g. `int o = obseg(3, 4);`).

In a `void` method we can leave with:

```java
return;   // this works

break;    // this only works in a loop
```

### Recursion (*rekurzija*)

Methods can call themselves: a recursive call (*rekurzivni klic*). Some problems are easier to solve with [[Recursion|recursion]].

Example: the [[Fibonacci Sequence|Fibonacci sequence]] (*Fibonaccijevo zaporedje*):

```text
0 1 1 2 3 5 8 13 21 ...
```

A recurrence relation (*rekurenčna enačba*) can be translated into recursion in a program:

$$
F_n =
\begin{cases}
0 & n = 0 \\
1 & n = 1 \\
F_{n-2} + F_{n-1} & \text{otherwise}
\end{cases}
$$

The recursive program (`Fibonacci`, under Code) is very inefficient (*zelo neučinkovit*), but there are tricks that make it much faster.

## Code

### Cross pattern (*Plus*)

A program that prints a pattern. First without methods:

```java
public class Plus {
    public static void main(String[] args) {

        for (int i = 1; i <= 4; i ++) {
            for (int j = 1; j <= 4; j++) {
                System.out.print(" ");
            }
            System.out.println("+");
        }
        for (int i = 1; i <= 9; i++) {
            System.out.print("+");
        }
        System.out.println();
        for (int i = 1; i <= 4; i ++) {
            for (int j = 1; j <= 4; j++) {
                System.out.print(" ");
            }
            System.out.println("+");
        }
    }
}
```

```text
    +
    +
    +
    +
+++++++++
    +
    +
    +
    +
```

This code is repetitive: the vertical arm is repeated twice, so it is better to use a method.

**With a method:**

```java
public class Plus {
    public static void main(String[] args) {

        navpicniKrak();
        for (int i = 1; i <= 9; i++) {
            System.out.print("+");
        }
        System.out.println();

        navpicniKrak(); 
    }
    public static void navpicniKrak() {
        for (int i = 1; i <= 4; i ++) {
            for (int j = 1; j <= 4; j++) {
                System.out.print(" ");
            }
            System.out.println("+");
        }

    }
}
```

**With a parameter**, for an arm of length `n`:

```java
import java.util.Scanner;

public class Plus {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        navpicniKrak(n);
        for (int i = 1; i <= 2 * n + 1; i++) {
            System.out.print("+");
        }
        System.out.println();

        navpicniKrak(n); 
    }
    public static void navpicniKrak(int visina) {
        for (int i = 1; i <= visina; i ++) {
            for (int j = 1; j <= visina; j++) {
                System.out.print(" ");
            }
            System.out.println("+");
        }

    }
}
```

```text
$ echo 2 | java Plus
  +
  +
+++++
  +
  +
```

**More compact code**, with a method `znaki` that prints a character `n` times and optionally a line break (*prelom*):

```java
import java.util.Scanner;

public class Plus1 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        navpicniKrak(n);
        
        sredinskiDel(n);

        navpicniKrak(n); 
    }
    public static void navpicniKrak(int visina) {
        for (int i = 1; i <= visina; i ++) {
            znaki(visina, ' ', false);
            System.out.println("+");
        }

    }
    public static void sredinskiDel(int n) {
        znaki (2 * n + 1, '+', true);

    }
    public static void znaki(int n, char znak, boolean prelom) {
        for (int i = 1; i<= n; i++) {
            System.out.print(znak);
        }
        if (prelom) {
            System.out.println();
        }
    }
}
```

`echo 2 | java Plus1` prints the same cross as `Plus`.

### Perimeter (*Obseg*): example of `return`

```java
public class Obseg {
    public static void main(String[] args) {
        // obseg(3, 4);

        int o = obseg(3, 4);
        System.out.println(o);
    }

    // public static void obseg(int a, int b) {
    //     System.out.println(2 * (a + b)); // tega obsega ne moremo uporabiti
    // }
    public static int obseg(int a, int b) {
        return 2 * (a + b);
    }
}
```

```text
$ java Obseg
14
```

The commented-out `void` version only prints the perimeter; its result cannot be used any further (*tega obsega ne moremo uporabiti*).

### Prime numbers with methods (*praštevila z metodami*)

Checking whether a candidate is prime is a subproblem (*podproblem*), so it gets its own method:

```java
import java.util.Scanner;

public class Prastevila5{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        System.out.println(2);
        

        for (int kandidat = 3; kandidat <= n; kandidat+= 2){

            if (jePrastevilo(kandidat)) {
                System.out.println(kandidat);
            }
        }
    }

    public static boolean jePrastevilo(int stevilo){
        
        int koren = (int) Math.round(Math.sqrt(stevilo)); // round vrne long

        for (int d = 3; d < koren; d+= 2){
            if (stevilo % d == 0){
                return false;
            }
            // napaka da bi dali
            // else {
            //     return true; 
            // }
        }

        // if (prastevilo){
        //     return true;
        // } else {
        //     return false;
        // }
        return true;
    }

} 
```

- `return false` ends the method at the first divisor, so the `boolean` flag and `break` from [[2026-10-22 - Loop Examples, break and switch - 3|lecture 3]] are no longer needed.
- It would be a mistake (*napaka*) to put `else { return true; }` inside the loop: the method would then return after checking only the first divisor.
- The commented-out `if (prastevilo) return true; else return false;` is replaced by a single `return true;` at the end.

```text
$ echo 30 | java Prastevila5
2 3 5 7 9 11 13 17 19 23 25 29      (one per line)
```

> [!warning] 9 and 25 are not prime
> The same mistake as in `Prastevila4`: with `d < koren` the divisor $\sqrt{k}$ itself is never checked, so squares of primes (9, 25, 49, …) are printed as primes. For $n = 1000$ the program prints 178 lines instead of 168. The slides (p. 21) use `d <= meja`.

**Corrected** (as on the slides, p. 21): the loop must include the root.

```java
        for (int d = 3; d <= koren; d+= 2){
```

```text
$ echo 30 | java Prastevila5
2 3 5 7 11 13 17 19 23 29      (one per line)
```

### Amicable numbers (*prijateljska števila*)

```text
220: 1 2 4 5 10 11 20 22 44 55 110 = 284

284: 1 2 4 71 142 = 220
```

Sum of divisors (*vsota deliteljev*), from combinatorics (*iz kombinatorike*):

```java
import java.util.Scanner;


public class PrijateljskaStevila {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int stevilo = sc.nextInt();

        // System.out.println(imaPrijatelja(stevilo));

        if (imaPrijatelja(stevilo)) {
            // System.out.println(kandidat); ne gre
            System.out.println(vsotaDeljitevljev(stevilo));
        } else {
            System.out.println("Nima");
        }

    }

    public static boolean imaPrijatelja(int stevilo) {
        int kandidat = vsotaDeljitevljev(stevilo);

        return kandidat != stevilo && vsotaDeljitevljev(kandidat) == stevilo;
    }

    public static int vsotaDeljitevljev(int n) {
        int vsota = 0;
        for (int d = 1; d < n; d++) {
            if (n % d == 0) {
                vsota += d;
            }
        }
        return vsota;
    }
}
```

- `System.out.println(kandidat)` in `main` does not work (*ne gre*): `kandidat` is a local variable of `imaPrijatelja` and does not exist in `main` ([[Variable Scope|scope]]). So `main` computes the sum of divisors again.
- `imaPrijatelja` returns the value of a [[Boolean|boolean]] expression directly instead of using `if`.

```text
$ echo 220 | java PrijateljskaStevila
284
$ echo 284 | java PrijateljskaStevila
220
$ echo 6 | java PrijateljskaStevila
Nima
```

### Fibonacci

```java
import java.util.Scanner;

public class Fibonacci {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        System.out.println(f(n));
    }

    public static int f(int n) {
        if (n <= 1) {
            return n;
        }
        int pp = f(n - 2);
        int p = f(n - 1);
        return pp + p;
    }
}
```

```text
$ echo 10 | java Fibonacci
55
```

This program is very inefficient (but there are tricks that make it much faster).

## Questions

- [ ] What do bitwise operators do, and why are they so useful? (read in the book)
- [ ] What are the tricks that make the recursive Fibonacci program much faster?

## Connections

- Course: [[Programming 1]]
- Previous lecture: [[2026-10-22 - Loop Examples, break and switch - 3]]: prime numbers versions 1–4, `break`, scope
- Exercises: [[2026-11-02 - Exercises for Methods and Recursion - 4]]
- [[Method]], [[Parameter]], [[Return Statement]], [[Recursion]], [[Fibonacci Sequence]], [[Operator Precedence]], [[Associativity]], [[Variable Scope]], [[Prime Number]]
- [[Mathematical Induction]]: the recurrence relation $F_n = F_{n-2} + F_{n-1}$ (Discrete structures)

## Sources

- My lecture notes from class (2026-10-29)
- Slides: [[Sources/programming_1/prosojnice/04_metode_h.pdf|04 Metode]] (Luka Fürst); the assignment-as-expression part and precedence/associativity: [[Sources/programming_1/prosojnice/03_krmilniKonstrukti_h.pdf|03 Krmilni konstrukti]], pp. 77–78
- Class code: `programming_1/class/4/` (`Plus.java`, `Plus1.java`, `Obseg.java`, `Prastevila5.java`, `PrijateljskaStevila.java`, `Fibonacci.java`)
