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
- the [[Break Statement|`break`]] and [[Continue Statement|`continue`]] statements, which change the flow of a loop,
- the [[Switch Statement|`switch` statement]] and the [[Variable Scope|scope]] of variables inside it,
- the [[Conditional Operator|conditional (ternary) operator]] `?:`.

The prime-number program is improved step by step: stop at the first divisor, check only odd numbers, and check only up to $\sqrt{k}$.

## Notes

### `do` loop and variable scope

A variable declared inside the body of the `do` loop does not exist in the condition `while (...)`. The body is a [[Block|block]] (*blok*), and the variable is only visible until the end of that block ([[Variable Scope|scope]]). So the variable must be declared **before** the loop (*poskus obstaja samo do `{}`, zato moramo inicializirati*):

```java
int poskus = 0;
do {
    poskus = sc.nextInt();
    ...
} while (izbranoStevilo != poskus);
```

Declaring `int poskus = sc.nextInt();` inside the body would be a compile error (*napaka pri prevajanju*).

### Random numbers (*naključna števila*)

We use the [[Class|class]] `Random` from the package `java.util` and create an [[Object|object]] of it:

```java
import java.util.Random;   // import the class
...
Random random = new Random();   // create a new object (naredimo nov objekt)
int stevilo = random.nextInt(n);   // random number between 0 and n − 1
```

`random.nextInt(n)` returns a number in $[0, n-1]$, so for a number in $[1, M]$ we write `random.nextInt(M) + 1`.

A `for` loop is not suitable for guessing, because there is no counter (*for ni primeren, ker nimamo števca*). We don't know in advance how many guesses there will be.

### `for` vs. `while`/`do`

| `for` | `while` / `do` |
|---|---|
| walking over an interval | repeat until a condition is met |
| number of steps known in advance | number of steps not known in advance |

Use `for` only for walking over an interval ($n$ steps).

**Scope rule:** every variable exists only inside the `{}` in which it is declared. The **only exception** is a variable declared in the `for` header. It does not belong to the enclosing block; it exists only until the end of the loop body:

```java
public static void main(...){
    ...
    for (int i = 0; i <= 10; i++){ // i exists from here …
        ...
    } // … to here
}
```

### Characters in a loop

The characters `'A'` to `'Z'` have consecutive [[ASCII]] codes (`'A' == 65`, `'B' == 66`, …), so a loop can count through them. Three versions were shown (code below, under *Capital letters*):

| Counter | `println(znak)` prints |
|---|---|
| `char znak` | letters `A` … `Z` |
| `int znak` | numbers `65` … `90` |
| `int znak` with a [[Type Casting|cast]] `(char) znak` | letters `A` … `Z` again |

### Finding the maximum (*Kdo je najboljši?*)

Searching for the maximum: first set the maximum to 0, because we know the results are non-negative (*ker vemo, da so števila nenegativna*). Every time we read a result, we compare it with the maximum so far; if it is larger, it becomes the new maximum. We also remember who achieved it (`najAtlet`). Example from the slides:

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

An outer loop goes over the candidates or rows, and an inner loop does the work for each one: counting divisors for primes, or printing one row of the multiplication table (*poštevanka*). In the multiplication table:

- `i` is the row we are in (*v kateri vrstici smo*),
- `j` is the column we are in (*v katerem stolpcu smo*).

The task is to find the best alignment of the numbers (*najdi optimalno poravnavo*); that is what `printf` is for.

### Formatted output: `System.out.printf`

```java
System.out.printf(niz, arg_1, arg_2, ...);
```

Used for formatting: the placeholders ([[Format Specifier|format specifiers]], *oblikovna določila*) are replaced by the values we want to print. `%n` is a new line and `%%` is the `%` character.

Example: the result of *Kdo je najboljši?* as a sentence. The two blanks are filled with `najAtlet` and `najDolzina`:

```java
// Zmagal je ___. atlet. Skocil je ___ cm dalec.
System.out.printf("Zmagal je %d. atlet. Skocil je %d cm dalec.", najAtlet, najDolzina);
```

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

In JShell, `printf` also shows its return value. `printf` returns the `PrintStream` itself, so JShell prints it after the formatted text:

```text
jshell> int a = 123
jshell> System.out.printf("%5d", a);
  123$2 ==> java.io.PrintStream@685f4c2e
```

The `  123` is the output: width 5, so two spaces in front.

### `break`

[[Break Statement|`break`]] **ends the innermost loop it is in** (*prekine najbolj notranjo zanko, v kateri je*), typically when some condition is met. It ends not only the innermost loop but also the innermost `switch`. Execution continues after it (*`break` nas vrže na to mesto*).

We cannot put the main exit condition of the loop into the `break` (*ne moremo glavnega izhodnega pogoja dati na break*).

The same can often be done without `break` by adding a condition to the loop with a [[Propositional Logic|conjunction]] `&&`: `d <= n && stDeljiteljev < 5` (see `PrvihPetDeljiteljev` below).

### `continue`

[[Continue Statement|`continue`]] skips all the remaining statements of the loop body and jumps back to checking the condition (*preskoči vse stavke zanke in skoči nazaj na preverjanje pogoja*). In a `for` loop the update (`i++`) is executed first, then the condition is checked.

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

A number is [[Prime Number|prime]] if it has exactly two divisors. The candidate is tested with a [[Boolean|`boolean`]] flag `prastevilo` (from version 2 on). The versions:

1. **Count all divisors** of each candidate from 1 to the candidate, and print the candidate if the count is 2 (`Prastevila1`).
2. **Stop at the first divisor:** divide by $2, \dots, k-1$. If any division works out, $k$ is not prime, so `break` and go on with $k + 1$ (`Prastevila2`).
3. **Only odd numbers:** apart from 2 all primes are odd, so print 2 first and then check only odd candidates with odd divisors (`kandidat += 2`, `d += 2`) (`Prastevila3`).
4. **Only up to the square root:** it is enough to check divisors up to $\sqrt{k}$, because the divisors are symmetric around the root (*ker so delitelji simetrični okrog korena*) (`Prastevila4`).
5. **[[Sieve of Eratosthenes]]** (*Eratostenovo sito*): announced as version 5 (`Prastevila 5`), but not written yet.

### Command line: counting lines and measuring time

- `wc -l` counts how many lines were printed (*koliko vrstic se je izpisalo*). `wc` alone also counts words and characters.
- `time` measures how long a command takes (*čas prevajanja*).

```bash
echo 1000 | java Prastevila2 | wc -l
time echo 1000 | java Prastevila2
```

Times measured in class for $n = 1000$:

| Version | total |
|---|---|
| `Prastevila2` | 0.064 s |
| `Prastevila3` | 0.066 s |
| `Prastevila4` | 0.066 s |

```bash
% time echo 1000 | java Prastevila2
echo 1000  0.00s user 0.00s system 31% cpu 0.002 total
java Prastevila2  0.07s user 0.02s system 148% cpu 0.064 total
```

### `switch` statement

[[Switch Statement|`switch`]] replaces a chain of [[Conditional Statement|`if`]] – `else if` – … – `else` (*namesto verige if else if*).

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

- The expression must be of type `byte`, `short`, `int`, `char`, `String` or `enum`. It **cannot** be `double`, `boolean` or `long`.
- If `izraz == konstanta_i`, the statements of that `case` are executed; otherwise those of `default`, which plays the role of `else` (*vloga else*). `default` can be left out.
- `break` is needed (*break je nujen*). Without it, execution **falls through** into the next `case`.
- Why does `switch` work this way? Because several different cases can do the same thing (*ker lahko več različnih case-ov dela isto stvar*). For example, months 4, 6, 9 and 11 all have 30 days and can share one block of statements:

```java
switch (mesec) {
    case 2:
        stDni = 28;
        break;
    case 4:
    case 6:
    case 9:
    case 11:
        stDni = 30;
        break;
    default:
        stDni = 31;
        break;
}
```

**Scope in `switch`:** a variable declared in a `case` exists until the end of the whole `switch`, not only until the end of its `case`. So this is an error, because `b` is declared twice in the same block (*ker je 2× inicializiral v istem bloku*):

```java
switch (a) {
    case 1:
        int b = 3;
        System.out.println(a + b);
        break;

    case 2:
        int b = 4;
        System.out.println(a * b);
        break;
}
```

```text
PrimerSwitch.java:16: error: variable b is already defined in method main(String[])
                int b = 4;
                    ^
```

The fix is to put each `case` in its own block `{ }` (see `PrimerSwitch` below).

### [[Conditional Operator|Conditional (ternary) operator]] (*trojiški / pogojni operator*)

```java
pogoj ? izraz_1 : izraz_2
```

If the condition holds, `izraz_1` is computed, otherwise `izraz_2`. The result becomes the value of the whole expression.

Example: absolute value:

```text
jshell> int a = -7
a ==> -7

jshell> int b = (a > 0) ? (a) : (-a);
b ==> 7
```

It is an expression, so it can replace an `if` only where a value is needed. For example, `System.out.println((tocke >= 50) ? "opravil" : "padel");` works, but `(tocke >= 50) ? System.out.println(...) : ...` does not, because `println(...)` has no value (slides, p. 75).

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

How many guesses are needed? If we always guess the middle of the remaining interval, every guess halves it, so for an upper bound of 100 **at most 7 guesses** are enough (we can also be lucky earlier). That is the [[Logarithm|binary logarithm]] (*dvojiški logaritem*), the same halving idea as [[Binary Search|binary search]]: how many times we divide the number by 2 to get to 1 ($\lceil \log_2 100 \rceil = 7$).

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

Output: `A`, `B`, …, `Z`, each on its own line.

With a `char` counter the letters are printed directly:

```java
for (char znak = 'A'; znak <= 'Z'; znak++){
    System.out.println(znak);
}
```

With an `int` counter and no cast, only the numbers are printed:

```java
for (int znak = 'A'; znak <= 'Z'; znak++){
    System.out.println(znak);
}
```

```text
65 66 67 … 90      (one per line)
```

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

### Grade (*ocena*)

Started in class as `Ocena.java`, but the file is still empty. It is probably the `switch` example with school grades from the slides (p. 68).

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

`wc -l` shows the difference: for $n = 1000$, `Prastevila2` prints 168 lines (there are 168 primes up to 1000), but `Prastevila4` prints 178.

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

- [ ] What exactly was meant by "we cannot put the main exit condition of the loop into the `break`" (*ne moremo glavnega izhodnega pogoja dati na break*)?
- [ ] Why are the measured times of `Prastevila2`, `3` and `4` for $n = 1000$ practically the same (0.064–0.066 s), although each version does less work?
- [ ] How does the Sieve of Eratosthenes (`Prastevila 5`) work, and how fast is it compared with version 4?

## Connections

- Course: [[Programming 1]]
- Previous lecture: [[2026-10-15 - Control Structures - 2]]: `if`, `while`, `do`, `for`, `op=`, `++`/`--`
- Exercises on loops from the previous week: [[2026-10-19 - Exercises for Control Structures - 2]]
- [[For Loop]], [[Do-while Loop]], [[While Loop]], [[Switch Statement]], [[Nested Loop]], [[Variable Scope]], [[Break Statement]], [[Continue Statement]], [[Conditional Operator]]
- [[Propositional Logic]]: the conditions `&&`, `||`, `!` of loops (Discrete structures)
- [[Prime Number]]: checking divisors up to $\sqrt{k}$

## Sources

- My lecture notes from class (2026-10-22), including the JShell and `time` outputs
- Slides: [[Sources/programming_1/prosojnice/03_krmilniKonstrukti_h.pdf|03 Krmilni konstrukti]] (Luka Fürst), pp. 33–76
- Class code: `programming_1/class/3/` (`UgibanjeStevila.java`, `VelikeCrke.java`, `KdoJeNajboljsi.java`, `Postevanka.java`, `PrvihPetDeljiteljev*.java`, `Prastevila1–4.java`, `PrimerSwitch`)
