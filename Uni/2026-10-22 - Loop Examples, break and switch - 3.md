---
type: "[[Lectures]]"
course: "[[Programming 1]]"
date: 2026-10-22
week: "3"
---

# 2026-10-22 - Loop Examples, break and switch

## Main Idea

The second part of control structures (*krmilni konstrukti*), mostly through examples:

- a [[Do-while Loop|`do` loop]] with random numbers (guessing a number),
- a [[For Loop|for loop]] over characters,
- finding the maximum,
- [[Nested Loop|nested loops]] (prime numbers, multiplication table) and formatted output with `printf`,
- the `break` and `continue` statements, which change the flow of a loop,
- the [[Switch Statement|`switch` statement]] and the [[Variable Scope|scope]] of variables inside it.

The prime-number program is improved step by step: stop at the first divisor, check only odd numbers, and check only up to $\sqrt{k}$.

## Notes

### `do` loop and variable scope

A variable declared inside the body of the `do` loop does not exist in the condition `while (...)`. The body is a block (*blok*), and the variable is only visible until the end of that block. So the variable must be declared **before** the loop (*poskus obstaja samo do `{}`, zato moramo inicializirati*):

```java
int poskus = 0;
do {
    poskus = sc.nextInt();
    ...
} while (izbranoStevilo != poskus);
```

Declaring `int poskus = sc.nextInt();` inside the body would be a compile error (*napaka pri prevajanju*).

### Random numbers (*naključna števila*)

We use the class `Random` from the package `java.util`:

```java
import java.util.Random;   // import the class
...
Random random = new Random();   // create a new object (naredimo nov objekt)
int stevilo = random.nextInt(n);   // random number between 0 and n − 1
```

For a number in $[1, M]$: `random.nextInt(M) + 1`.

### `for` vs. `while`/`do`

| `for` | `while` / `do` |
|---|---|
| walking over an interval | repeat until a condition is met |
| number of steps known in advance | number of steps not known in advance |

A variable declared in the `for` header exists only until the end of the loop body.

### Characters in a loop

The characters `'A'` to `'Z'` have consecutive ASCII codes (`'A' == 65`, `'B' == 66`, …), so a loop can count through them. In class the counter is an `int`, so it has to be cast back to `char` for printing (`(char) znak`). Without the cast, `println` would print the numbers 65, 66, …

### Finding the maximum (*Kdo je najboljši?*)

Keep the best value so far (`najDolzina`) and who achieved it (`najAtlet`). Whenever the current value is larger, update both (example from the slides):

| `i` | `dolzina` | `najDolzina` | `najAtlet` |
|:-:|:-:|:-:|:-:|
| | | 0 | 0 |
| 1 | 635 | 635 | 1 |
| 2 | 680 | 680 | 2 |
| 3 | 671 | 680 | 2 |
| 4 | 695 | 695 | 4 |
| 5 | 667 | 695 | 4 |

Because the comparison is `>`, for equal results the first athlete stays the best.

### Nested loops (*gnezdene zanke*)

An outer loop goes over the candidates or rows, and an inner loop does the work for each one: counting divisors for primes, or printing one row of the multiplication table (*poštevanka*).

### Formatted output: `System.out.printf`

```java
System.out.printf(niz, arg_1, arg_2, ...);
```

The $i$-th placeholder `%…` in the string is replaced by `arg_i`. `%n` is a line break and `%%` is the `%` character.

| Placeholder | Type |
|---|---|
| `%d` | integer (`byte`, `short`, `int`, `long`) |
| `%f` | real number (`float`, `double`) |
| `%c` | character (`char`) |
| `%s` | string (`String`) |
| `%b` | logical value (`boolean`) |

**Format specifiers** (*oblikovna določila*):

```java
int a = 42;
double b = 3.1415;
String niz = "java";
System.out.printf("[%5d]%n", a);      // [   42]      width 5, right-aligned
System.out.printf("[%10s]%n", niz);   // [      java]
System.out.printf("[%-5d]%n", a);     // [42   ]      left-aligned
System.out.printf("[%05d]%n", a);     // [00042]      leading zeros
System.out.printf("[%.3f]%n", b);     // [3.142]      3 decimals
System.out.printf("[%10.3f]%n", b);   // [     3.142]
```

In the multiplication table `%4d` prints every number right-aligned on 4 places.

### `break`

`break` **ends the loop it is directly in** (the innermost enclosing `for`, `while`, `do` or `switch`). Execution continues after that loop (*`break` nas vrže na to mesto*).

The same can often be done without `break` by adding a condition to the loop: `d <= n && stDeljiteljev < 5` (see `PrvihPetDeljiteljev` below).

### `continue`

`continue` jumps to the next iteration of the loop it is directly in: to the condition check (`while`, `do`) or to the update (`for`).

From the slides:

```java
for (int i = 1; i <= 10; i++) {
    if (i % 3 == 0) {
        continue;
    }
    for (int j = 1; j <= i; j++) {
        System.out.print("*");
    }
    System.out.println();
}
```

This prints the rows of 1, 2, 4, 5, 7, 8 and 10 stars; rows 3, 6 and 9 are skipped.

### Prime numbers (*praštevila*), step by step

A number is prime if it has exactly two divisors. The versions:

1. **Count all divisors** of each candidate from 1 to the candidate, and print the candidate if the count is 2 (`Prastevila1`).
2. **Stop at the first divisor:** divide by $2, \dots, k-1$. If any division works out, $k$ is not prime, so `break` and go on with $k + 1$ (`Prastevila2`).
3. **Only odd numbers:** apart from 2 all primes are odd, so print 2 first and then check only odd candidates with odd divisors (`kandidat += 2`, `d += 2`) (`Prastevila3`).
4. **Only up to the square root:** it is enough to check divisors up to $\sqrt{k}$ (`Prastevila4`).

### `switch` statement

```java
switch (izraz) {
    case konstanta_1:
        stavki_1
        break;
    ...
    default:
        stavki_{n+1}
        break;
}
```

- The expression must be of type `byte`, `short`, `int`, `char`, `String` or `enum`.
- If `izraz == konstanta_i`, the statements of that `case` are executed; otherwise those of `default`, which can be left out.
- Without `break`, execution **falls through** into the next `case`.

**Scope in `switch`:** a variable declared in a `case` exists until the end of the whole `switch`, not only until the end of its `case`. Declaring `int b` in two `case` sections is a compile error. The fix is to put each `case` in its own block `{ }` (see `PrimerSwitch` below).

## Code

### Guessing a number (*ugibanje števila*)

```java
import java.util.Scanner;
import java.util.Random;


public class UgibanjeStevila{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        System.out.print("Zgornja meja: ");
        int zgornjaMeja = sc.nextInt();

        Random random = new Random(); // naredimo nov objekt
        int izbranoStevilo = random.nextInt(zgornjaMeja) + 1;
        int steviloPoskusov = 1;
        int poskus = 0;


        do {
            System.out.print("Tvoj poskus: ");
            poskus = sc.nextInt();

            if (izbranoStevilo > poskus) {
                System.out.println("Moje stevilo je vecje. ");
            } else if (izbranoStevilo < poskus) {
                System.out.println("Moje stevilo je manjse. ");
            }
        } while (izbranoStevilo != poskus); // poskus obstaja samo do {}, zato moramo initializirati

        System.out.println("Cestitke.");

    }
}
```

The output depends on the random number. With upper bound 1 the number is always 1:

```text
$ printf "1\n1\n" | java UgibanjeStevila
Zgornja meja: Tvoj poskus: Cestitke.
```

`steviloPoskusov` is declared but not used yet.

### Capital letters (*velike črke*)

```java
public class VelikeCrke{
    public static void main(String[] args){

        for (int znak = 'A'; znak <= 'Z'; znak++){
            System.out.println((char) znak);
        }
    }
}
```

Output: `A`, `B`, …, `Z`, each on its own line. The slides use `char crka` as the counter directly, so no cast is needed there.

### Who is the best? (*Kdo je najboljši?*)

```java
import java.util.Scanner;

public class KdoJeNajboljsi{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        System.out.print("Stevilo atletov: ");
        int stAtletov = sc.nextInt();

        // maximum 
        int najDolzina = 0;
        int najAtlet = 0;


        for (int i = 1; i <= stAtletov; i++){
            System.out.print("Vnesi rezultat za " + i + ". atleta: ");
            int dolzina = sc.nextInt();

            if (dolzina > najDolzina){
                najDolzina = dolzina;
                najAtlet = i;
            }

        }
        System.out.println(najDolzina + " " + najAtlet);

        }
}
```

```text
$ printf "3\n650 720 700\n" | java KdoJeNajboljsi
Stevilo atletov: Vnesi rezultat za 1. atleta: Vnesi rezultat za 2. atleta: Vnesi rezultat za 3. atleta: 720 2
```

### Multiplication table (*poštevanka*)

```java
import java.util.Scanner;

public class Postevanka{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        for (int i = 1; i <= n; i++){
            for (int j = 1; j <= n; j++){
                int zmnozek = i * j;
                //System.out.print(zmnozek + " ");
                System.out.printf("%4d", zmnozek);
            }
            System.out.println();
        }

        

        }
}
```

```text
$ echo 4 | java Postevanka
   1   2   3   4
   2   4   6   8
   3   6   9  12
   4   8  12  16
```

The commented-out `print(zmnozek + " ")` was the first version; its columns are not aligned once the numbers have two digits.

### First five divisors (*prvih pet deliteljev*)

With `break`:

```java
import java.util.Scanner;

public class PrvihPetDeljiteljev{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int stDeljiteljev = 0;

        for (int d = 1; d <= n; d++){
            if (n % d == 0){
                System.out.println(d);
                stDeljiteljev++;
                if (stDeljiteljev == 5){
                    break;
                }
            } 
        }
        //break nas vrze na to mesto
        System.out.println("Zbogom.");

    }
}
```

Without `break`, using the condition of the loop instead:

```java
import java.util.Scanner;

public class PrvihPetDeljiteljevBrezBreak{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int stDeljiteljev = 0;

        for (int d = 1; d <= n && stDeljiteljev < 5; d++){
            if (n % d == 0){
                System.out.println(d);
                stDeljiteljev++;
            } 
        }
        //break nas vrze na to mesto
        System.out.println("Zbogom.");

    }
}
```

Both give the same output:

```text
$ echo 36 | java PrvihPetDeljiteljev
1
2
3
4
6
Zbogom.
```

### Prime numbers (*praštevila*)

**Version 1: counting divisors**

```java
import java.util.Scanner;

public class Prastevila1{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        for (int kandidat = 2; kandidat <= n; kandidat++){


            for (int d = 1; d < kandidat; d++){
                if (kandidat % d == 0){
                    stDeljiteljev++;
                }
            }

            if (stDeljiteljev == 2){
                System.out.println(kandidat);
            }
        }

        }
}
```

> [!warning] Does not compile in this form
> ```text
> Prastevila1.java:14: error: cannot find symbol
>                     stDeljiteljev++;
>   symbol:   variable stDeljiteljev
> ```
> The counter `stDeljiteljev` is never declared. The slides (p. 50) declare `int stDeliteljev = 0;` at the start of the outer loop and count divisors with `d <= kandidat`.

**Corrected** (as on the slides, p. 50):

```java
        for (int kandidat = 2; kandidat <= n; kandidat++){

            int stDeljiteljev = 0;

            for (int d = 1; d <= kandidat; d++){
                if (kandidat % d == 0){
                    stDeljiteljev++;
                }
            }

            if (stDeljiteljev == 2){
                System.out.println(kandidat);
            }
        }
```

- **The counter starts at 0 for every candidate.** It is declared inside the outer loop, so it does not carry over the divisors of the previous candidate.
- **The candidate counts as its own divisor.** With `d <= kandidat` a prime has exactly 2 divisors (1 and itself). With `d < kandidat` it would have only 1, and `== 2` would find numbers like 4 and 9 instead.

```text
$ echo 30 | java Prastevila1
2 3 5 7 11 13 17 19 23 29      (one per line)
```

**Version 2: stop at the first divisor**

```java
import java.util.Scanner;

public class Prastevila2{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        

        for (int kandidat = 2; kandidat <= n; kandidat++){

            boolean prastevilo = true;

            for (int d = 2; d < kandidat; d++){
                if (kandidat % d == 0){
                    prastevilo = false;
                    break;
                }
            }

            if (prastevilo){
                System.out.println(kandidat);
            }
        }

    }
}
```

**Version 3: only odd candidates and divisors**

```java
import java.util.Scanner;

public class Prastevila3{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        System.out.println(2);
        

        for (int kandidat = 3; kandidat <= n; kandidat+= 2){

            boolean prastevilo = true;

            for (int d = 3; d < kandidat; d+= 2){
                if (kandidat % d == 0){
                    prastevilo = false;
                    break;
                }
            }

            if (prastevilo){
                System.out.println(kandidat);
            }
        }

    }
}
```

Versions 2 and 3 print the same:

```text
$ echo 30 | java Prastevila2
2 3 5 7 11 13 17 19 23 29      (one per line)
```

**Version 4: only up to the square root**

```java
import java.util.Scanner;

public class Prastevila4{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        System.out.println(2);
        

        for (int kandidat = 3; kandidat <= n; kandidat+= 2){

            boolean prastevilo = true;
            
            int koren = (int) Math.round(Math.sqrt(kandidat)); // round vrne long

            for (int d = 3; d < koren; d+= 2){
                if (kandidat % d == 0){
                    prastevilo = false;
                    break;
                }
            }

            if (prastevilo){
                System.out.println(kandidat);
            }
        }

    }
}
```

`Math.round` returns a `long`, so the result is cast to `int`.

```text
$ echo 30 | java Prastevila4
2 3 5 7 9 11 13 17 19 23 25 29      (one per line)
```

> [!warning] 9 and 25 are not prime
> With `d < koren` the divisor $\sqrt{k}$ itself is never checked, so squares of primes (9, 25, 49, …) are printed as primes. The slides (p. 66) use `d <= meja`, which gives the same output as versions 2 and 3.

**Corrected** (as on the slides, p. 66): the inner loop must include the root.

```java
            for (int d = 3; d <= koren; d+= 2){
```

If $k = a \cdot b$ with $a \leq b$, then $a \leq \sqrt{k}$. So it is enough to check divisors up to and **including** $\sqrt{k}$; for $k = 9$ the only divisor to find is $3 = \sqrt{9}$.

```text
$ echo 30 | java Prastevila4
2 3 5 7 11 13 17 19 23 29      (one per line)
```

### `switch` with blocks (*PrimerSwitch*)

```java
import java.util.Scanner;

public class PrimerSwitch{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int a = 1;

        switch (a) {
            case 1: {
                int b = 3;
                System.out.println(a + b);
                break;
            }
            
            case 2:{
                int b = 4;
                System.out.println(a * b);
                break;
            }
        }

    }
}
```

```text
$ java PrimerSwitch
4
```

Each `case` has its own block, so `int b` can be declared in both. Without the braces this would not compile. (The file is saved as `PrimerSwitch` without the `.java` extension; `javac` needs `PrimerSwitch.java`.)

## Questions

- [ ] 

## Connections

- Course: [[Programming 1]]
- Previous lecture: [[2026-10-15 - Control Structures - 2]]: `if`, `while`, `do`, `for`, `op=`, `++`/`--`
- [[For Loop]], [[Do-while Loop]], [[While Loop]], [[Switch Statement]], [[Nested Loop]], [[Variable Scope]]
- [[Prime Number]]: checking divisors up to $\sqrt{k}$

## Sources

- Slides: [[Sources/programming_1/prosojnice/03_krmilniKonstrukti_h.pdf|03 Krmilni konstrukti]] (Luka Fürst), pp. 33–73
- Class code: `programming_1/class/3/` (`UgibanjeStevila.java`, `VelikeCrke.java`, `KdoJeNajboljsi.java`, `Postevanka.java`, `PrvihPetDeljiteljev*.java`, `Prastevila1–4.java`, `PrimerSwitch`)
