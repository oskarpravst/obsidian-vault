---
type: "[[Lectures]]"
course: "[[Programming 1]]"
date: 2026-11-05
week: "5"
---

# 2026-11-05 - Arrays, Searching and Sorting

## Main Idea

The topic were [[Array|arrays]] (*tabele*): a sequence of variables of the same type, reached through indices. We saw:

- how to create an array, its length, the valid indices and the default values,
- two ways of walking through an array: the ordinary `for` loop with an index and the [[Enhanced For Loop|for-each loop]] (where we are not interested in the indices),
- array examples: printing, the index of the minimum, copying the input into an array (*PrepisElementov*), grade frequencies (*FrekvenceOcen*),
- searching: [[Linear Search|linear search]] (*navadno iskanje*), searching in a sorted array, and [[Binary Search|binary search]] (*dvojiško iskanje, bisekcija*),
- sorting (*urejanje*) with [[Insertion Sort|insertion sort]] (*urejanje z navadnim vstavljanjem*),
- the last version of the prime numbers program, the [[Sieve of Eratosthenes|sieve of Eratosthenes]] (*Eratostenovo sito/rešeto*),
- the [[Fibonacci Sequence|Fibonacci sequence]] again, this time with [[Memoization|memoization]]: an array remembers the results that were already computed.

## Notes

### Arrays (*tabele*)

An array is a sequence of variables of THE SAME TYPE (*zaporedje spremenljivk istega tipa*); each one is independent of the others, and they are reached through **indices** (*indeksi*). The variables are the **cells / elements** of the array (*celice / elementi tabele*).

```text
t = | 25 | 42 | 17 | 54 | 20 | 36 |
      0    1    2    3    4    5      ← indices
```

```java
t[3] = 5
```

- The **length** (*dolžina*) is the number of elements: `t.length`.
- The valid indices go from `0` to length − 1 (*veljavni indeksi … dolžina − 1*).

### Creating an array (*ustvarjanje tabele*)

`int[]` is the type of the array (*tip tabele*).

```java
int[] t = new int[]{25, 42, 17, 54, 20, 36}; // 1. creates an array with concrete elements
int[] t = new int[10];                       // 2. creates an array of 10 zeros

int[] t = {25, 42, 17, 54, 20, 36};
t = new int[]{-10, 7, -6};
```

The length of an array is **fixed** (*dolžina tabele je fiksna*): we cannot add elements to it like in Python. An array cannot simply be extended (*to je minus jave*).

**Default values** (*privzete vrednosti*) of the elements in `new T[n]`:

| type | default value |
| --- | --- |
| `int` (and other integer types) | `0` |
| `char` | `'\0'` |
| `boolean` | `false` |
| reference type (*referenčni tip*) | `null` |

So a new array of booleans would contain only `false`.

In [[JShell]]:

```text
jshell> int[] t = new int[3];
t ==> int[3] { 0, 0, 0 }

jshell> t.length
$2 ==> 3

jshell> t[t.length - 1] = 30;
$3 ==> 30

jshell> System.out.println(t[t.length]);
|  Exception java.lang.ArrayIndexOutOfBoundsException: Index 3 out of bounds for length 3
|        at (#4:1)
```

`t[t.length]` is one past the last element, so it throws an `ArrayIndexOutOfBoundsException` at runtime.

### Walking through an array

With an index (the `izpis` method in *Primer*, under Code), or with the **for-each loop**, another way of walking through an array, used when we are not interested in the indices (*tukaj nas ne zanimajo indeksi*):

```java
int[] t = {...};

for (int element: t) {
	System.out.println(element);
}
```

In the for-each loop `element` is a **copy** of the array element, so changing it does not change the original (*ta element je kopija, torej ne vplivamo na original*). This does not work:

```java
public static void povecajZa1(int[] t) {
        for (int element: t) { // ta element je kopija torej ne vplivamo na original
            element++;
        }
    }
```

To change the array we need the index: `t[i]++` (`povecajZa1Dela` under Code).

### Grade frequencies (*frekvence ocen*)

Count how many times each grade 1–5 appears. Two ways:

1. with 5 counters (*s pomočjo 5 števcev*) — quite ugly (*precej grda*),
2. with an array of counters: `frekvence[ocena - 1]++` (*FrekvenceOcen* under Code).

### Searching (*iskanje*)

**Linear search** (`poisci`): go through the array until we find `x`; return its index, or `-1` if it is not there.

**In a sorted array** (*če imamo urejeno tabelo*) we can stop earlier: at the first element that is greater than or equal to `x`.

```text
7 10 15 21 27 30 31 34 37 39 42 50 58 61 75
                                 ?
```

If we did not find 45 until `?`, we can stop at the first element that is greater or equal (*lahko končamo pri prvem elementu, ki je večji ali enak*).

```java
public static int poisciVUrejeni(int[]t , int x) {
        int i = 0;
        while (i < t.length && t[i] < x) {
            i++;
        }
        return(i < t.length && t[i] == x) ? (i) : (-1);
    }
```

This is not optimal: on average the element is in the middle, so we need about half as many steps as the length of the array (*v povprečju je element na sredini in rabi polovico operacij dolžine*).

#### Binary search (*bisekcija, dvojiško iskanje*)

We cut the (sorted) array in half (*na pol presekamo*). We keep a left bound and a right bound (*leva meja, desna meja*):

```java
lm = 0;
dm = 14;
sredina = (lm + dm) / 2;
```

We compare `x` with the element in the middle:

- if `x` is larger: `lm = sredina + 1`,
- if `x` is smaller: `dm = sredina - 1`,

… until the left bound becomes greater than the right one (*dokler leva meja ne postane večja od desne*), i.e. the loop runs while `lm <= dm`: when `lm == dm` there is still one element left to check.

The larger the array, the bigger the difference (*večja kot je tabela, večja je razlika*). Binary search on 100 elements: $\log_2(100) = 7$ steps. So it always pays off to keep lists sorted (*torej se vedno splača imeti urejene sezname*).

### Sorting (*urejanje*)

Ascending / descending (*naraščajoče / padajoče*); there are many sorting algorithms.

**Insertion sort** (*algoritem navadno vstavljanje*, `uredi` under Code): for each element from index 1 on, shift the larger elements before it one place to the right and insert it into the gap.

It is **stable** (*stabilno*): it does not swap equal elements among themselves (*med seboj ne zamenjuje enakih elementov*).

`Arrays.toString()` returns the array as a string (*vrne tabelo v obliki niza*); it needs `import java.util.Arrays;`.

### Prime numbers, last version: sieve of Eratosthenes (*Eratostenovo sito / rešeto*)

- We stop at the square root (*pri korenu se ustavim*).
- A `boolean` array marks which numbers are crossed out (*prečrtana*) and which are not; it is as long as the upper bound (*dolga je toliko kot je zgornja meja*).

The code is under Code.

### Fibonacci with memoization (*Fibonacci z memoizacijo*)

In the recursive solution from [[2026-10-29 - Methods and Recursion - 4|lecture 4]] the whole subtree repeats (*celo poddrevo se nam ponavlja*). We remember the results in an array that stores the values already computed (*zapomnimo si s tabelo, ki hrani že izračunane rezultate*) — **memoization** (*FibonacciMemo* under Code). The method is still recursive, but each value is computed only once.

## Code

### Printing, minimum, for-each (*Primer*)

```java
public class Primer {
    public static void main(String[] args) {
        int[] t = {20, 17, 11, 14, 25, 8, 9};

        izpis(t);
        System.out.println(t[indeksMinimuma(t)]);
        izpis2(t);
        povecajZa1(t);
        povecajZa1Dela(t);
        System.out.println(t);



    }
    public static void izpis(int[] t) {
        for (int i = 0; i < t.length; i++) {
            System.out.printf("Element na indeksu %d je %d%n", i, t[i]);
        }
    }

    public static void izpis2(int[] t) {
        for (int element: t) {
            System.out.println(element);
        }
    }
    public static void povecajZa1(int[] t) {
        for (int element: t) { // ta element je kopija torej ne vplivamo na original
            element++;
        }
    }

    public static void povecajZa1Dela(int[] t){
        for (int i = 0; i < t.length; i++) { // tukaj pa spreminjamo original
            t[i]++;
        }
    }
    


    public static int indeksMinimuma(int[] t) {
        int iMin = 0; // indeks minimuma

        for (int i = 1; i < t.length; i++) {
            if (t[i] < t[iMin]) {
                iMin = i;
            }
        }
        return iMin;

    }
}
```

Output:

```text
Element na indeksu 0 je 20
Element na indeksu 1 je 17
Element na indeksu 2 je 11
Element na indeksu 3 je 14
Element na indeksu 4 je 25
Element na indeksu 5 je 8
Element na indeksu 6 je 9
8
20
17
11
14
25
8
9
[I@6d06d69c
```

- `indeksMinimuma` starts with index 0 as the current minimum and compares from index 1 on; the minimum is `8`.
- `System.out.println(t)` does not print the elements, only the type and a hash code (`[I@…`, the part after `@` differs on every run). To print the elements use `Arrays.toString(t)`.

### Copying the input into an array (*PrepisElementov*)

Read `n` and then `n` numbers, and print them in the same order. Without an array this could not be done, because we would need a variable number of variables.

```java
import java.util.Scanner;
public class PrepisElementov {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        int[] tabela = new int[n];

        for (int i = 0; i < n; i++) {
            System.out.printf("Vnesi %d stevilo: ", i + 1);
            tabela[i] = sc.nextInt();
        }

        for (int element: tabela) {
            System.out.println(element);
        }

    }
}
```

### Grade frequencies (*FrekvenceOcen*)

```java
import java.util.Scanner;
public class FrekvenceOcen {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();


        int[] frekvence = new int[5];

        for (int i = 1; i <= n; i++) {
            int ocena = sc.nextInt();

            frekvence[ocena - 1]++;
        }

        for (int element: frekvence) {
            System.out.println(element);
        }

    }
}
```

Grade `ocena` is counted in `frekvence[ocena - 1]` (grades 1–5 → indices 0–4).

```text
$ printf '6\n5 3 5 1 4 5\n' | java FrekvenceOcen
1
0
1
1
3
```

### Searching (*Poisci*)

```java
import java.util.Scanner;
public class Poisci {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int x = sc.nextInt();
        int[] t = {2, 6, 8, 21, 9, 10};
        System.out.println(poisci(t, x));
        int[] urejena = {7, 10, 15, 21, 27, 30, 31, 34, 37, 39, 42, 50, 58, 61, 75};

        System.out.println(poisciVUrejeni(urejena, 7));
        System.out.println(poisciVUrejeni(urejena, 75));
        System.out.println(poisciVUrejeni(urejena, 27));

        System.out.println(dvojiskoIskanje(urejena, 7));
        System.out.println(dvojiskoIskanje(urejena, 75));
        System.out.println(dvojiskoIskanje(urejena, 27));





        
    }

    public static int poisci(int[] t, int x) {
        for (int i = 0; i < t.length; i++) {
            if (t[i] == x) {
                return i;
            }
        }
        return -1;
    }

    public static int poisciVUrejeni(int[]t , int x) {
        int i = 0;
        while (i < t.length && t[i] < x) {
            i++;
        }
        return(i < t.length && t[i] == x) ? (i) : (-1);
    }

    public static int dvojiskoIskanje(int[] t, int x) {
        int lm = 0;
        int dm = t.length - 1;

        while (lm <= dm) {
            int s = (lm + dm) / 2;
            if (t[s] == x) {
                return s;
            }
            if (x > t[s]) {
                lm = s + 1;
            } else {
                dm = s - 1;
            }
        }
        return -1;
    }
}
```

```text
$ echo 2 | java Poisci
0
0
14
4
0
14
4
```

- `poisci` returns the index of the first occurrence, or `-1`.
- In `poisciVUrejeni` the order of the conditions in `i < t.length && t[i] < x` matters: thanks to short-circuit evaluation, `t[i]` is never read when `i == t.length`.
- `dvojiskoIskanje` loops while `lm <= dm`; when `lm == dm` there is still one element left to check.

### Insertion sort (*Urejanje*)

```java
import java.util.Arrays;

public class Urejanje {
    public static void main(String[] args) {
        int[] tabela = {80, 50, 75, 30, 45, 60, 95, 20};
        uredi(tabela);

        System.out.println(Arrays.toString(tabela));

    }

    public static void uredi(int[] t) {
        for (int i = 1; i < t.length; i++) {
            int element = t[i];

            int j = i - 1;
            while (j >= 0 && t[j] > element) {
                t[j + 1] = t[j];
                j--;
            }

            t[j + 1] = element;
        }
    }
}
```

```text
[20, 30, 45, 50, 60, 75, 80, 95]
```

The condition `t[j] > element` (strictly greater) is what makes the sort stable: an equal element is never moved past another equal one.

### Sieve of Eratosthenes (*PrastevilaZadnja*)

```java
import java.util.Scanner;

public class PrastevilaZadnja {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int zgornjaMeja = sc.nextInt();

        boolean[] sestavljeno = new boolean[zgornjaMeja + 1];
        int p = 2;
        int koren = (int) Math.round(Math.sqrt(zgornjaMeja));

        while (p <= koren) {
            for (int i = 2 * p; i <= zgornjaMeja; i += p) {
                sestavljeno[i] = true;
            }

            do {
                p++;
            } while (p <= koren && sestavljeno[p] == true);
        }

        for (int i = 2; i <= zgornjaMeja; i++) {
            if (!sestavljeno[i]) {
                System.out.println(i);
            }
        }
    }
}
```

```text
$ echo 30 | java PrastevilaZadnja
2 3 5 7 11 13 17 19 23 29        (one per line)
```

- `sestavljeno[i] == true` means that `i` is composite (*sestavljeno*); a new `boolean` array is all `false`, so at the start no number is crossed out.
- The `for` loop crosses out all multiples of `p` from `2p` on; the `do`–`while` moves `p` to the next number that is not crossed out.

### Fibonacci with memoization (*FibonacciMemo*)

```java
import java.util.Scanner;

public class FibonacciMemo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        int[] memo = new int[n + 1];

        System.out.println(fib(n, memo));
    }

    public static int fib(int n, int[] memo) {
        if (n <= 1) {
            return n;
        }
        if (memo[n] > 0) {
            return memo[n];
        }
        int vrednost = fib(n- 2, memo) + fib(n - 1, memo);
        memo[n] = vrednost;
        return vrednost;
    }
}
```

```text
$ echo 40 | java FibonacciMemo
102334155
```

`memo` starts as all zeros. Before computing `fib(n)` we check whether `memo[n] > 0`; if so, the value was already computed and we just return it, otherwise we compute it and store it in `memo[n]`.

## Questions

- [ ] Why do indices start at 0? (*razlog, zakaj se indeks začne z 0?*)
- [ ] In the first example, does `t[3] = 5` mean assigning 5 to the element at index 3 (which is 54 in the drawing)?

## Connections

- Course: [[Programming 1]]
- Exercises: [[2026-11-09 - Exercises for Arrays, Searching and Sorting - 5]]
- Previous lecture: [[2026-10-29 - Methods and Recursion - 4]]: methods, recursive Fibonacci (now with memoization), prime numbers with methods
- [[2026-10-22 - Loop Examples, break and switch - 3]]: earlier versions of the prime numbers program
- [[Array]], [[Enhanced For Loop]], [[Linear Search]], [[Binary Search]], [[Insertion Sort]], [[Sieve of Eratosthenes]], [[Memoization]], [[Fibonacci Sequence]], [[Recursion]], [[Method]], [[JShell]]
- [[Big O Notation]]: linear search needs up to $n$ steps, binary search about $\log_2 n$ ([[2026-10-28 - Limits of Sequences - 4]], Calculus)

## Sources

- My lecture notes from class (2026-11-05)
- Slides: [[Sources/programming_1/prosojnice/05_tabele_h.pdf|05 Tabele]] (Luka Fürst): arrays pp. 3–7, searching pp. 19–26, insertion sort pp. 27–34, sieve of Eratosthenes pp. 35–37, Fibonacci with memoization pp. 38–42
- Class code: `programming_1/class/5/` (`Primer.java`, `PrepisElementov.java`, `FrekvenceOcen.java`, `Poisci.java`, `Urejanje.java`, `PrastevilaZadnja.java`, `FibonacciMemo.java`)
