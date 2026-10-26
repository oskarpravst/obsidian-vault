---
type: "[[Lectures]]"
course: "[[Programming 1]]"
date: 2026-10-26
week: "3"
---

# 2026-10-26 - Exercises for Control Structures

## Main Idea

Lab exercises (*vaje*) for week 3, *Control structures 2* (*Krmilni konstrukti 2*): [[Nested Loop|nested loops]] (*gnezdene zanke*) and reading input until it runs out. Piramida draws a figure line by line with two inner [[For Loop|`for` loops]] (spaces, then stars), Kleptomanka Anka lists all combinations of three digits with three nested `for` loops, and Zgoščenke reads file sizes in a [[While Loop|`while` loop]] with `sc.hasNextInt()` and stops early with `break`. The assistant's solutions are the reference solutions below.

## Tasks

**Piramida** — read a positive integer $n \in [1, 100]$ and draw a "pyramid" of stars of height $n$. Do not print extra spaces (no trailing spaces) or empty lines.

```text
$ echo 4 | java Piramida
   *
  ***
 *****
*******

$ echo 1 | java Piramida
*
```

**Kleptomanka Anka** — Anka wants to steal a bike locked with a three-digit combination lock (`a-b-c`). Someone whispers to her that the first digit is odd, the second is greater than $m$ and the third is divisible by $d$. Read $m \in [0, 8]$ and $d \in [1, 9]$ and print every possible combination in its own line as `a-b-c`, in lexicographic order (ascending by the first digit, then the second, then the third). Finally print the number of combinations.

```text
$ echo 7 3 | java Anka
1-8-0
1-8-3
1-8-6
1-8-9
1-9-0
1-9-3
1-9-6
1-9-9
3-8-0
…
9-9-6
9-9-9
40
```

**Zgoščenke** — we want to save files onto $n$ empty CDs (*zgoščenke*), each holding $k$ units of data (EP). The files (none larger than $k$) are handled in order: first we fill the first CD; when there is not enough space left for the current file, we move on to the next CD, and we never go back to an earlier one, even if it still has enough space. Read $n \in [1, 10^4]$ and $k \in [1, 10^9]$, then file sizes from $[1, k]$, each in its own line. For every successfully saved file print `X EP -> zgoscenka Y (Z EP)` — the file size, the CD number and the amount of data currently on that CD. Stop when the input or the CDs run out.

```text
$ printf '4 700\n500\n200\n300\n600\n50\n' | java Zgoscenke
500 EP -> zgoscenka 1 (500 EP)
200 EP -> zgoscenka 1 (700 EP)
300 EP -> zgoscenka 2 (300 EP)
600 EP -> zgoscenka 3 (600 EP)
50 EP -> zgoscenka 3 (650 EP)

$ printf '4 700\n500\n200\n300\n600\n50\n100\n400\n500\n550\n' | java Zgoscenke
500 EP -> zgoscenka 1 (500 EP)
200 EP -> zgoscenka 1 (700 EP)
300 EP -> zgoscenka 2 (300 EP)
600 EP -> zgoscenka 3 (600 EP)
50 EP -> zgoscenka 3 (650 EP)
100 EP -> zgoscenka 4 (100 EP)
400 EP -> zgoscenka 4 (500 EP)
```

In the second example the last two files can no longer be saved (CD 4 is too full and there is no fifth CD).

## Notes

### From my lab notes (`zapiski.txt`)

- `itpodpora@fri.uni-lj.si` — the faculty's IT support (*IT podpora*) address.
- `Scanner` — `hasNextLine` (`hasNext…`): we ask whether there is still something on the input.
- With a `Scanner` the pointer is placed on the first number; after `nextInt` it is on the next one.
- We end the input stream with `Ctrl + D` (end of stream — *zaključek toka*).
- A `for` loop with a single-line body does not need `{}`.
- `'*' * 6` — like in Python; `"*".repeat(6)` — don't use it (*ne uporabljati*).
- Nested loops take a lot of time.
- $O(n)$ — one nested loop; $O(n^2)$ — two nested loops (see [[Time Complexity]]).
- Everything that is $n^2$ is useless (*neuporabno*).
- Statements that are too long are broken over several lines (*predolge stavke zlomimo*).

### Piramida

- The outer loop goes over the rows `i = 0 … n-1`. Row `i` has `n - i - 1` spaces in front and `2 * i + 1` stars; nothing is printed after the stars, so there are no trailing spaces.
- v.1 computes both counts from `i`; v.2 keeps two counters (`stPresledkov--`, `stZvezdic += 2`) that change after every row.
- The inner loops have a single statement as the body, so they are written without `{}`.
- v.3 uses [[Recursion|recursion]] and `String.repeat` — only for interest, we don't need to know it (*ni treba znati!*).

### Kleptomanka Anka

- Three nested `for` loops, one per digit. Because the outer loop is the first digit and the innermost the third, the combinations come out in lexicographic order on their own.
- Instead of looping over all digits and filtering with `if`, the loops step only over valid digits: `st1 = 1; st1 += 2` gives the odd digits, `st2` starts at `m + 1`, and `st3 = 0; st3 += d` gives the multiples of $d$ (0 is divisible by every $d$). The `if` version is kept in a comment.
- The counter `stKomb++` counts the combinations; it equals $5 \cdot (9 - m) \cdot (\lfloor 9/d \rfloor + 1)$, e.g. $5 \cdot 2 \cdot 4 = 40$ for `7 3`.

### Zgoščenke

- The number of files is not given, so the loop is `while (sc.hasNextInt())` — it reads until the input runs out (`Ctrl + D` when typing by hand).
- If the file does not fit (`fileSize + zasedenost > capacity`), we move to the next CD and reset `zasedenost` to 0. If there is no next CD (`stZgoscenke > n`), `break` ends the loop before the file is printed.
- Every file fits on an empty CD (size $\le k$), so one move is always enough. $k \le 10^9$, so `fileSize + zasedenost` $\le 2 \cdot 10^9$ still fits into an `int`.
- The long `printf` is broken over two lines.
- The commented version puts both conditions into the `while` (`sc.hasNextInt() && stZgoscenke <= n`) and needs an extra `if` before printing.

## Code

### Piramida (assistant's solution)

```java
import java.util.*;

/**
 * n - visina piramide
 *
 *    * 
 *   ***
 *  *****
 *
 */

public class Piramida {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int n = sc.nextInt();

		// v.1
		
		for (int i = 0; i < n; i++) {
			// izpis presledkov
			for (int j = 0; j < n - i - 1; j++)
				System.out.print(' ');
			// izpis zvzedic
			for (int j = 0; j < 2 * i + 1; j++)
				System.out.print('*');
			// skok v novo vrstico
			System.out.println();
		}
		
		// v.2 
		
		int stZvezdic = 1;
		int stPresledkov = n - 1;
		
		for (int i = 0; i < n; i++) {
			// izpis presledkov
			for (int j = 0; j < stPresledkov; j++)
				System.out.print(' ');
			// izpis zvzedic
			for (int j = 0; j < stZvezdic; j++)
				System.out.print('*');
			// skok v novo vrstico
			System.out.println();
			
			stPresledkov--;
			stZvezdic += 2;
		}
		
		// '*' * 6
		// "*".repeat(6)
		
		// v.3 - z rekurzijo - ni treba znati!!!
		
		izpisiPiramido(1, n - 1);
		
	}
	
	private static void izpisiPiramido(int stZvezdic, int stPresledkov) {
		if (stPresledkov >= 0) {
			System.out.println(" ".repeat(stPresledkov) + "*".repeat(stZvezdic));
			izpisiPiramido(stZvezdic + 2, stPresledkov - 1);
		}
	}
	
}
```

> [!warning] Prints the pyramid three times (found when testing; the code above is left unchanged)
> All three versions run one after another, so the file as it is prints the pyramid three times and fails all tests (0/10). Each version on its own is correct: keep only one of them (e.g. v.1) and it passes.

My lab solution is the same as v.2 (passes all tests). My solution from home (also passes all tests) uses `printf` with a field width instead of a loop for the spaces: `%Ns` right-aligns the string in a field of width `N`, and the string grows by `"**"` every row:

```java
String zvezdica = "*";
int trenutnaVrstica = visina;

for (int i = 0; i < visina; i++) {
    System.out.printf("%" + (trenutnaVrstica) + "s%n", zvezdica);
    trenutnaVrstica += 1;
    zvezdica += "**";
}
```

### Kleptomanka Anka (assistant's solution)

```java
import java.util.*;

/**
 * m - podatek o drugi stevki (je vecja od m)
 * d - podatek o tretji stevki (deljiva z d)
 */

public class Anka {
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int m = sc.nextInt();
		int d = sc.nextInt();
		
		int stKomb = 0;
		
		for (int st1 = 1; st1 < 10; st1 += 2) {
			// if (st1 % 2 == 1)
			for (int st2 = m + 1; st2 < 10; st2++) {
				for (int st3 = 0; st3 < 10; st3 += d) {
					// if (st3 % d == 0)
					System.out.printf("%d-%d-%d%n", st1, st2, st3);
					stKomb++;
				}
			}
		}
		System.out.println(stKomb);
		
		/*
		for (int st1 = 1; st1 < 10; st1++) {
			if (st1 % 2 == 1) {
				for (int st2 = m + 1; st2 < 10; st2++) {
					for (int st3 = 0; st3 < 10; st3++) {
						if (st3 % d == 0) {
							System.out.printf("%d-%d-%d%n", st1, st2, st3);
							stKomb++;
						}
					}
				}
			}
		}
		System.out.println(stKomb);
		*/
		
	}
}
```

My lab file `Anka.java` is empty. My solution from home (passes all tests) is like the assistant's commented version: a `while` loop over the odd first digit, and two `for` loops over all digits with the conditions checked in an `if`:

```java
while (liha < 10) {
    for (int i = 0; i < 10; i++){ // vecje od 
        for (int j = 0; j < 10; j++){ // deljiva z 
            if (j % deljivaZ == 0 && i > vecjeOd) {
                System.out.printf("%d-%d-%d%n", liha, i, j);
                steviloVseh++;
            }
        }
    }
    liha += 2;   
}
```

### Zgoščenke (assistant's solution)

```java
import java.util.Scanner;

public class Zgoscenke {
	
	// n - stevilo zgoscenk
	// capacity - velikost CD-ja v EP
	// fileSize - velikost datoteke v EP
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int n = sc.nextInt(); 
		int capacity = sc.nextInt(); 
		
		int stZgoscenke = 1;
		int zasedenost = 0;
		
		/*
		while (sc.hasNextInt() && stZgoscenke <= n) {
			int fileSize = sc.nextInt();
			
			if (fileSize + zasedenost > capacity) {
				stZgoscenke++;
				zasedenost = 0;
			}
			zasedenost += fileSize;
			
			if (stZgoscenke <= n)
				System.out.printf("%d EP -> zgoscenka %d (%d EP)%n", 
								fileSize, stZgoscenke, zasedenost);
		}
		*/
		
		while (sc.hasNextInt()) {
			int fileSize = sc.nextInt();
			
			if (fileSize + zasedenost > capacity) {
				stZgoscenke++;
				if (stZgoscenke > n)
					break;
				zasedenost = 0;
			}
			zasedenost += fileSize;
			
			System.out.printf("%d EP -> zgoscenka %d (%d EP)%n", 
								fileSize, stZgoscenke, zasedenost);
		}
		
	}
}
```

My lab attempt was unfinished: it subtracted the file size instead of adding it, never moved to the next CD, printed without `%n`, and `do { sc.nextInt(); … } while (sc.hasNextLine())` reads past the end of the input (`NoSuchElementException`). It fails all tests:

```text
$ printf '4 700\n500\n200\n…' | java Zgoscenke     # my lab attempt
500 EP -> zgoscenka 1 (-500 EP)200 EP -> zgoscenka 1 (-700 EP)300 EP -> zgoscenka 1 (-1000 EP)…
Exception in thread "main" java.util.NoSuchElementException
```

My solution from home moves to the next CD correctly, but it also fails all tests: the loop `while (velikostDatoteke <= prostorZgoscenk)` calls `sc.nextInt()` without checking `sc.hasNextInt()`, so it crashes with `NoSuchElementException` at the end of the input. It also never stops when the CDs run out ($n$ is not used), and because the output is collected in a `String` and printed only after the loop, the crash means nothing is printed at all.

### Extra: Krog (my unfinished attempt)

An attempt at drawing a circle of `#` with two nested loops over `y` and `x` from `radius` down to `-radius + 1`. There is no condition yet for whether a point lies inside the circle, so it prints a $2r \times 2r$ square:

```text
$ echo 2 | java Krog
####
####
####
####
```

## Questions

- [ ] 

## Connections

- Course: [[Programming 1]]
- Lecture: [[2026-10-15 - Control Structures - 2]] — `for` and `while` loops, reading input with `sc.hasNextInt()`
- Previous exercises: [[2026-10-19 - Exercises for Control Structures - 2]]
- Exercises: [[Sources/programming_1/vaje/prog1/p1_vaje03/naFaksu/vaje03.pdf|vaje03]]
- Related: [[Time Complexity]] (nested loops), [[Recursion]] (Piramida v.3)

## Sources

- My lab notes: [[Sources/programming_1/vaje/prog1/p1_vaje03/naFaksu/zapiski.txt|zapiski.txt]]
- Assistant's solutions (reference): `programming_1/vaje/prog1/p1_vaje03/naFaksu/assistant/` (`Piramida.java`, `Anka.java`, `Zgoscenke.java`)
- My code from the lab: `programming_1/vaje/prog1/p1_vaje03/naFaksu/` (`Piramida.java`, `Anka.java`, `Zgoscenke.java`, `Krog.java`)
- My code from home: `programming_1/vaje/prog1/p1_vaje03/doma/` (`Piramida.java`, `Anka.java`, `Zgoscenke.java`)
