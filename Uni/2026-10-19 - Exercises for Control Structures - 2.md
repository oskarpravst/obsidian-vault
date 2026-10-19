---
type: "[[Lectures]]"
course: "[[Programming 1]]"
date: 2026-10-19
week: "2"
---

# 2026-10-19 - Exercises for Control Structures

## Main Idea

Lab exercises (*vaje*) for week 2, *Control structures 1* (*Krmilni konstrukti 1*): solving problems with loops — iterative programming (*iterativno programiranje*). A [[For Loop|`for` loop]] over an interval (Kvadrati), taking an integer apart into its digits with `% 10` and `/ 10` in a [[While Loop|`while` loop]] (Števke), and a `while` loop with a compound condition that simulates a process day by day (Romanje). The assistant's solutions are the reference solutions below.

## Tasks

**Kvadrati** — read integers $a \in [1, 10^3]$ and $b \in [a, 10^3]$ and print the squares of all integers from $a$ to $b$ inclusive, each in its own line.

```text
$ echo 5 11 | java Kvadrati
25
36
49
64
81
100
121
```

**Števke** — read an integer from $[1, 10^{18}]$ (watch out! — *pozor!*) and print its digits in reverse order: the last digit in the first line, the second-to-last in the second, …

```text
$ echo 730545 | java Stevke
5
4
5
0
3
7
```

**Romanje** — Roman sets off on a pilgrimage of length $d$. On the first day he walks $p$ units, and every following day $z$ units less than the day before because of growing tiredness. He finishes when he reaches the goal or when he is finally exhausted (on a day when he would have to walk zero or a negative length, he no longer walks). Read $d \in [1, 10^9]$, $p \in [1, 10^9]$ and $z \in [0, 10^9]$ and for every day print a line `D: Z -> K` — the day number, the remaining distance at the start and at the end of the day.

```text
$ echo 28 10 1 | java Romanje
1: 28 -> 18
2: 18 -> 9
3: 9 -> 1
4: 1 -> 0

$ echo 28 10 3 | java Romanje
1: 28 -> 18
2: 18 -> 11
3: 11 -> 7
4: 7 -> 6
```

## Notes

### From my lab notes (`zapiski.txt`)

- `java -jar as2client.jar 10.32.211.99` — the assistant's assistant (*asistentov asistent*): a client program run in the lab with the given IP address.
- Iterative programming (*iterativno programiranje*) — the topic of these exercises: solving a problem by repeating steps in a loop.
- `Math.pow()` — very slow (*zelo počasno*). In the extra example below the assistant computes the power of 10 with a loop instead (`potenca *= 10`).

### Kvadrati

The number of repetitions is known in advance (from $a$ to $b$), so a `for` loop with a counter fits best. $b \le 10^3$, so the square $\le 10^6$ fits into an `int`.

### Števke

- The input goes up to $10^{18}$, which does not fit into an `int` (max $\approx 2.1 \cdot 10^9$) — that is why the number is read as a `long` with `sc.nextLong()` and the literals are written as `10L`.
- `stevilo % 10` is the last digit, `stevilo / 10` drops the last digit (integer division). Repeat while the number is greater than 0.
- The result of `% 10` is between 0 and 9, so it can safely be cast to `int`.
- The assistant also showed a recursive version (`izpisi`) that prints the digits in the original order — only as a curiosity, we don't know recursion yet (*ne znamo še, samo kot zanimivost*).

### Romanje

- Walk while there is still some path left **and** he is still able to walk: `pot > 0 && prehodiDanes > 0`.
- On the last day he walks only what is left: if `pot < prehodiDanes`, then `prehodiDanes = pot` (so the end is `0`, not negative).
- After each day the daily distance decreases by `zmanjsanje` and the day counter increases.
- Output with `printf("%d: %d -> %d%n", ...)` in the exact required format.

## Code

### Kvadrati (assistant's solution)

```java
import java.util.Scanner;

public class Kvadrati {
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int spMeja = sc.nextInt();
		int zgMeja = sc.nextInt();
		
		for (int stevilo = spMeja; stevilo <= zgMeja; stevilo++) {
			int kvadrat = stevilo * stevilo;
			System.out.println(kvadrat);
		}
	}
}
```

My solution with a `while` loop (also passes all tests) — it changes the input variable `spMeja` itself instead of using a separate counter:

```java
while (spMeja <= zgMeja) {
    System.out.println(spMeja * spMeja);
    spMeja++;
}
```

### Števke (assistant's solution)

```java
import java.util.Scanner;

public class Stevke {
	
	public static void izpisi(long stevilo) {
		if (stevilo > 0) {
			int stevka = (int) (stevilo % 10L);
			izpisi(stevilo / 10);
			System.out.println(stevka);
		}
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		long stevilo = sc.nextLong();
		
		// izpis z rekurzijo -> ne znamo še, samo kot zanimivost
		// izpisi(stevilo);
		
		while (stevilo > 0L) {
			int stevka = (int) (stevilo % 10L);
			System.out.println(stevka);
			stevilo = stevilo / 10L;
		}
	}
}
```

My solution is the same `while` loop.

### Romanje (assistant's solution)

```java
import java.util.Scanner;

public class Romanje {
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int pot = sc.nextInt();
		int prehodiPrviDan = sc.nextInt();
		int zmanjsanje = sc.nextInt();
		
		int stDneva = 1;
		int prehodiDanes = prehodiPrviDan;
		
		// hodi dokler ima še kaj poti in hkrati je sposoben hoje
		while (pot > 0 && prehodiDanes > 0) {
			if (pot < prehodiDanes)
				prehodiDanes = pot;
			
			int ostanekPoti = pot - prehodiDanes;
			System.out.printf("%d: %d -> %d%n", stDneva, pot, ostanekPoti);
			pot -= prehodiDanes;
			prehodiDanes -= zmanjsanje;
			stDneva++;
		}
	}
}
```

My attempt was unfinished: it printed only the remaining distance (not the format `D: Z -> K`) and never decreased the daily distance by `zmanjsanje`, so it fails all tests.

```text
$ echo 28 10 1 | java Romanje     # my attempt
18
8
0
```

### Extra: digits in the original order (`IzpisStevk`, assistant)

First count the digits with $\lfloor \log_{10} |n| \rfloor + 1$, compute the highest power of 10 with a loop (instead of `Math.pow`), then take digits from the front with `/ potenca` and `% potenca`:

```java
import java.util.Scanner;

public class IzpisStevk {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		long stevilo = sc.nextLong();

		int stMest = (int) Math.floor(Math.log10(Math.abs(stevilo)) + 1);
		System.out.printf("# mest: %d%n", stMest);


		int potenca = 1;
		for (int i = 0; i < stMest - 1; i++)
			potenca *= 10;
		System.out.printf("stevilo = %d%n", stevilo);
		System.out.printf("potenca = %d%n", potenca);
		System.out.println("----");
		while (stevilo > 0) {
			int stevka = (int) (stevilo / potenca);
			stevilo = stevilo % potenca;
			System.out.println(stevka);
			// System.out.println(stevilo);
			potenca /= 10;
		}
	}
}
```

```text
$ echo 730545 | java IzpisStevk
# mest: 6
stevilo = 730545
potenca = 100000
----
7
3
0
5
4
5
```

> [!warning] Two bugs in this example (found when testing; the code above is left unchanged)
> 1. **Trailing zeros are lost.** The loop runs only `while (stevilo > 0)`; once the remaining number becomes 0, the zeros that are still to be printed are skipped. For `1000` it prints only `1` instead of `1 0 0 0`.
>    Fix: repeat exactly `stMest` times, e.g. `for (int i = 0; i < stMest; i++) { … }`.
> 2. **Overflow of `potenca`.** `potenca` is an `int` (max $\approx 2.1 \cdot 10^9$), but for an 18-digit number it must reach $10^{17}$. For `123456789012345678` it prints `potenca = 1569325056` and nonsense digits (see [[Integer Overflow]]).
>    Fix: `long potenca = 1;`.
>
> With both fixes, `1000` → `1 0 0 0`, `123456789012345678` → `1 2 3 … 7 8`, and $10^{18}$ → `1` followed by 18 zeros.

## Questions

- [ ] 

## Connections

- Course: [[Programming 1]]
- Lecture: [[2026-10-15 - Control Structures - 2]] — `while`, `for`, `op=` and `++` operators
- Previous exercises: [[2026-10-14 - Exercises for Introduction to programming - 1]] — testing with `tj.exe`
- Exercises: [[Sources/programming_1/vaje/prog1/p1_vaje02/vaje02.pdf|vaje02]]
- Related: [[Integer Overflow]] (why Števke needs `long`)

## Sources

- My lab notes: [[Sources/programming_1/vaje/prog1/p1_vaje02/zapiski.txt|zapiski.txt]]
- Assistant's solutions (reference): `programming_1/vaje/prog1/p1_vaje02/assistant/` (`Kvadrati.java`, `Stevke.java`, `Romanje.java`, `IzpisStevk.java`)
- My code: `programming_1/vaje/prog1/p1_vaje02/` (`Kvadrati.java`, `Stevke.java`, `Romanje.java`)
