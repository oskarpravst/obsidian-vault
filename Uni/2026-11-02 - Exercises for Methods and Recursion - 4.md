---
type: "[[Lectures]]"
course: "[[Programming 1]]"
date: 2026-11-02
week: "4"
---

# 2026-11-02 - Exercises for Methods and Recursion

## Main Idea

Lab exercises (*vaje*) for week 4, *Methods* (*Metode*). Both tasks split the problem into a [[Method|method]] that solves a subproblem and a `main` that calls it: Collatzovo zaporedje uses a method that returns the length of one Collatz sequence (*Collatzovo zaporedje*) and a [[For Loop|`for` loop]] in `main` that looks for the longest one; Največji skupni delitelj uses a [[Recursion|recursive]] method for the greatest common divisor (*največji skupni delitelj*, [[Greatest Common Divisor|gcd]]) and two nested loops over the candidate pairs. The assistant also showed Smreka (a spruce drawn from pyramids with small helper methods), Spruce (the same, built as a `String`, with random lights), Beri (a method that reads from a `Scanner` passed as a parameter) and a skeleton for Berač. The assistant's solutions are the reference solutions below.

## Tasks

**Collatzovo zaporedje** — the Collatz sequence starts with a given number $n$ and repeats the following until it reaches 1: if the current number is even, divide it by 2; otherwise multiply it by 3 and add 1. By the still unproven [[Collatz Conjecture|Collatz conjecture]], this reaches 1 for every positive integer. Read $a \in [1, 10^3]$ and $b \in [a, 10^3]$ and print which number between $a$ and $b$ (inclusive) has the longest Collatz sequence, and how long it is. The sequence includes the starting number, all intermediate members and the final 1. If several numbers have the longest sequence, print the smallest. All members of the sequences are smaller than $10^9$ and all lengths smaller than $10^6$.

```text
$ echo 10 20 | java Collatz
18
21
```

18 has 21 members: 18, 9, 28, 14, 7, 22, 11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1.

**Največji skupni delitelj** — read $n \in [1, 10^9]$ and $g \in [1, n]$ and print all pairs of numbers from $[1, n]$ whose greatest common divisor is $g$. Each pair is printed once as `(p, q)` with $p \le q$, in lexicographic order (ascending $p$, then ascending $q$). No test has more than $10^4$ pairs. The gcd can be computed with

$$
\gcd(a, b) =
\begin{cases}
a & b = 0 \\
\gcd(b, a \bmod b) & \text{otherwise}
\end{cases}
$$

which translates directly into a recursive method (given on the sheet):

```java
public static int gcd(int a, int b) {
    if (b == 0) {
        return a;
    }
    return gcd(b, a % b);
}
```

```text
$ echo 12 3 | java NajvecjiSkupniDelitelj
(3, 3)
(3, 6)
(3, 9)
(3, 12)
(6, 9)
(9, 12)
```

## Notes

### From my lab notes (`zapiski.txt`)

- We put `random` into the same initial state with a seed (*seme*): the same seed gives the same sequence of "random" numbers.
- Can we use internal information about the problem (*notranje informacije problema*)?
- `xdg-open .` — opens the current directory in the file explorer (Linux).

### Collatzovo zaporedje

- `dolzinaZaporedja` computes one sequence and returns its length with `return`; `main` only loops over $a … b$ and keeps the best number and length so far.
- The length starts at 1 because the final 1 belongs to the sequence; every step of the `while (stevilo > 1)` loop adds one member.
- The comparison is strict (`dolzina > najDolzina`): a later number with the same length does not replace the earlier one, so the smallest such number is printed.
- The members stay below $10^9$, so `3 * stevilo + 1` still fits into an `int`.

### Največji skupni delitelj

- `gcd` is the sheet's formula written as a [[Recursion|recursive]] method; the commented version computes the same with a `while` loop (the [[Euclidean Algorithm|Euclidean algorithm]]).
- Both numbers of a pair must be multiples of $g$ (otherwise $g$ cannot divide them), so the loops start at $g$ and step by $g$ (`i += ciljniGCD`) instead of trying every number up to $n$ — with $n$ up to $10^9$ trying everything would be far too slow.
- The inner loop starts at `j = i`, which gives $p \le q$, prints every pair once, and keeps the lexicographic order.
- Being a multiple of $g$ is not enough: e.g. $\gcd(6, 12) = 6 \ne 3$, so the pair is still checked with `gcd(i, j) == ciljniGCD`.

### Smreka and Spruce

- `znaki(n, znak)` prints a character $n$ times; `piramida(n, zamik)` prints a pyramid of height $n$ shifted by `zamik` dots; `smreka` stacks pyramids of height $1, 2, …, k$, each shifted by `stPiramid - i - 1`, so all of them are centred.
- Spruce has the same structure, but every method returns a `String` instead of printing. Then `main` can still change the whole tree: `replace('.', ' ')` turns the dots into spaces, and `postaviLucke` tries 20 random positions (`Math.random()`) and changes `*` into `#` (the lights, *lučke*) with a `StringBuilder`. The output is different on every run.

### Beri

- The `Scanner` is created once in `main` and passed to `preberiPriimekIme` as a parameter (the commented line shows the alternative of creating a new `Scanner` inside the method). `String.format` builds the result string instead of printing it.

## Code

### Collatzovo zaporedje (assistant's solution)

```java
import java.util.Scanner;

public class Collatz {
	
	/**
	 * Vrne dolzino Collatzovega zapopredja, ki izhaja iz 
	 * podanega stevila.
	 */

	private static int dolzinaZaporedja(int stevilo) {
		int dolzina = 1;
		while (stevilo > 1) {
			if (stevilo % 2 == 0)
				stevilo /= 2;
			else
				stevilo = 3 * stevilo + 1;
			dolzina++;
		}
		return dolzina;
	}

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int spMeja = sc.nextInt();
		int zgMeja = sc.nextInt();
		
		int najDolzina = 0;
		int najZacetek = 0;
		
		for (int stevilo = spMeja; stevilo <= zgMeja; stevilo++) {
			int dolzina = dolzinaZaporedja(stevilo);
			
			if (dolzina > najDolzina) {
				najDolzina = dolzina;
				najZacetek = stevilo;
			}
		}
		System.out.println(najZacetek);
		System.out.println(najDolzina);
		
	}
}
```

My lab solution `CollatzovoZaporedje.java` is the same idea (also passes all tests). The method starts counting at 0, loops `while (stevilo != 1)` and adds the final 1 after the loop, and `main` prints both lines with one `printf`:

```java
public static int SestejSteviloClenov(int stevilo) {
    int dolzina = 0;
    
    while (stevilo != 1) {
        dolzina++;
        if (stevilo % 2 == 0) {
            stevilo = stevilo / 2;
        } else {
            stevilo = stevilo * 3 + 1;
        }
    }
    dolzina++;
    return dolzina;
}
```

### Največji skupni delitelj (assistant's solution)

```java
import java.util.*;

public class NajvecjiSkupniDelitelj {
	
	/**
	 * Vrne najvecji skupni delitelj stevil.
	 * @param a prvo stevilo
	 * @param b drugo stevilo
	 */
	
	private static int gcd(int a, int b) {
		if (b == 0)
			return a;
		return gcd(b, a % b);
	}
	
	/*
	private static int gcd(int a, int b) {
		while (b > 0) {
			int t = a;
			a = b;
			b = t % b;
		}
		return a;
	}
	*/
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int n = sc.nextInt();
		int ciljniGCD = sc.nextInt();	
		
		for (int i = ciljniGCD; i <= n; i += ciljniGCD) {
			for (int j = i; j <= n; j += ciljniGCD) {
				if (gcd(i, j) == ciljniGCD)
					System.out.printf("(%d, %d)%n", i, j);
			}
		}
		
		
	}
}
```

My lab solution is the same (same loops, the sheet's `gcd` with `{}`, variables named `a` and `b`); it also passes all tests.

### Extra: Smreka (assistant's solution)

```java
import java.util.Scanner;

public class Smreka {
	
	/**
	 * Izpise <stevilo> znakov znaka <znak>.
	 */

	private static void znaki(int stevilo, char znak) {
		for (int i = 0; i < stevilo; i++)
			System.out.print(znak);
	}

	/**
	 * Izpise piramido, zamaknjeno za odmik od leve.
	 *
	 * @param stevilo 	visina piramide
	 * @param zamik 	odmik od levega roba
	 */
	
	private static void piramida(int n, int zamik) {
		for (int i = 0; i < n; i++) {
			// izpis zamikov
			znaki(zamik, '.');
			// izpis presledkov 
			znaki(n - i - 1, ' ');
			// izpis zvezdic
			znaki(2 * i + 1, '*');
			// skok v NV
			System.out.println();
		}
	}

	/**
	 * Izrise smreko, ki ima 'stPiramid' vej.
	 *
	 * @param stPiramid 	stevilo piramid
	 */	
	
	private static void smreka(int stPiramid) {
		for (int i = 0; i < stPiramid; i++)
			piramida(i + 1, stPiramid - i - 1);
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int visina = sc.nextInt();
		
		smreka(visina);
	}
}
```

```text
$ echo 4 | java Smreka
...*
.. *
..***
.  *
. ***
.*****
   *
  ***
 *****
*******
```

My lab solution prints the same tree. Instead of a `znaki` helper it has three inner `for` loops in `Piramida`, and `main` keeps the shift in a variable `zamik` that decreases after every pyramid:

```java
int zamik = n - 1;

for (int i = 1 ; i <= n; i++) {
    Piramida(i, zamik);
    zamik--;
}
```

### Extra: Spruce (assistant's solution)

```java
import java.util.Scanner;

public class Spruce {
	
	/**
	 * Izpise <stevilo> znakov znaka <znak>.
	 */

	private static String znaki(int stevilo, char znak) {
		String niz = "";
		for (int i = 0; i < stevilo; i++)
			niz += znak;
		return niz;
	}

	/**
	 * Izpise piramido, zamaknjeno za odmik od leve.
	 *
	 * @param stevilo 	visina piramide
	 * @param zamik 	odmik od levega roba
	 */
	
	private static String piramida(int n, int zamik) {
		String trikotnik = "";
		for (int i = 0; i < n; i++) {
			// izpis zamikov
			trikotnik += znaki(zamik, '.');
			// izpis presledkov 
			trikotnik += znaki(n - i - 1, ' ');
			// izpis zvezdic
			trikotnik += znaki(2 * i + 1, '*');
			// skok v NV
			trikotnik = String.format("%s%n", trikotnik);
		}
		return trikotnik;
	}

	/**
	 * Izrise smreko, ki ima 'stPiramid' vej.
	 *
	 * @param stPiramid 	stevilo piramid
	 */	
	
	private static String smreka(int stPiramid) {
		String spruce = "";
		for (int i = 0; i < stPiramid; i++)
			spruce = spruce + piramida(i + 1, stPiramid - i - 1);
		return spruce;
	}
	
	private static String postaviLucke(String spruce) {
		StringBuilder smreka = new StringBuilder(spruce);
		for (int i = 0; i < 20; i++) {
			int pos = (int) (Math.random() * smreka.length());
			if (smreka.charAt(pos) == '*')
				smreka.setCharAt(pos, '#');
		}
		return smreka.toString();
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int visina = sc.nextInt();
		String spruce = smreka(visina);
		spruce = spruce.replace('.', ' ');
		// spruce = spruce.replace('*', '#');
		spruce = postaviLucke(spruce);

		System.out.print(spruce);
	}
}
```

```text
$ echo 4 | java Spruce      # one run; the lights change every time
   *
  ***
   #
  *#*
 *****
   *
  *##
 *#**#
**#**#*
```

### Extra: Beri (assistant's solution)

```java
import java.util.Scanner;

public class Beri {
	
	private static String preberiPriimekIme(Scanner sc) {
		// Scanner sc = new Scanner(System.in);
		String ime = sc.next();
		String priimek = sc.next();
		return String.format("%s, %s", priimek, ime);
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int davcna = sc.nextInt();
		int letoRojstva = sc.nextInt();
		
		String priimek = preberiPriimekIme(sc);
		System.out.printf("%s; (%d) %d%n", priimek, davcna, letoRojstva);
		
	}
}
```

```text
$ printf '123 1990\nJanez Novak\n' | java Beri
Novak, Janez; (123) 1990
```

### Extra: Berač (assistant's skeleton, unfinished)

There is no statement for Berač on the sheet, but the folder has its tests (`berac/`). The assistant's file is only a skeleton: two empty methods, `oznakaValute` (currency number → label: 0 → `EUR`, 1 → `GBP`, 2 → `USD`) and `preracunajVMilievre` (an amount in a currency → milli-euros), and an empty `main`. As it is, it prints nothing and fails all tests. From the tests, the input is five numbers (e.g. `12345 1390 910 5 50000`) and the output is a table of gifts (*Darilo*) and the running total in the hat (*Klobuk*) in mEUR:

```text
    Darilo          Klobuk
     0 GBP          0 mEUR
     3 EUR       3000 mEUR
     4 GBP       8560 mEUR
…
```

## Questions

- [ ] What exactly is the Berač task? (no statement on the sheet; only the skeleton and the tests)

## Connections

- Course: [[Programming 1]]
- Lecture: [[2026-10-29 - Methods and Recursion - 4]] — methods, parameters, `return`, recursion
- Previous exercises: [[2026-10-26 - Exercises for Control Structures - 3]] (Piramida, which Smreka builds on)
- Exercises: [[Sources/programming_1/vaje/prog1/p1_vaje04/vaje04.pdf|vaje04]]
- Related: [[Greatest Common Divisor]], [[Euclidean Algorithm]], [[Collatz Conjecture]], [[Return Statement]], [[Parameter]]
- [[For Loop]], [[While Loop]]

## Sources

- My lab notes: [[Sources/programming_1/vaje/prog1/p1_vaje04/zapiski.txt|zapiski.txt]]
- Assistant's solutions (reference): `programming_1/vaje/prog1/p1_vaje04/assistant/` (`Collatz.java`, `NajvecjiSkupniDelitelj.java`, `Smreka.java`, `Spruce.java`, `Beri.java`, `Berac.java`)
- My code from the lab: `programming_1/vaje/prog1/p1_vaje04/` (`CollatzovoZaporedje.java`, `NajvecjiSkupniDelitelj.java`, `Smreka.java`)
