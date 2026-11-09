---
type: "[[Lectures]]"
course: "[[Programming 1]]"
date: 2026-11-09
week: "5"
---

# 2026-11-09 - Exercises for Arrays, Searching and Sorting

## Main Idea

Lab exercises (*vaje*) for week 5, *Arrays 1* (*Tabele 1*). Both tasks read the input into an [[Array|array]] (*tabela*) and then work on it: Vrsta zbor checks each element against its neighbours (with care at the two ends of the array), and Zgoščenke (drugič) keeps the used space of each CD in an array, looks for the index of the minimum, and prints the array with `Arrays.toString`. The boundary checks in Vrsta zbor rely on [[Short-circuit Evaluation|short-circuit evaluation]] (*kratkostično izvajanje*), which is also the topic of my lab notes. The assistant also showed Izštevanka (a counting-out rhyme: removing an element from an array) and two unfinished skeletons with [[Two-dimensional Array|two-dimensional arrays]]: TestSudoku and Sinus. The assistant's solutions are the reference solutions below.

## Tasks

**Vrsta zbor** — at the command "Fall in!" (*V vrsto zbor!*) the soldiers should line up by height from the shortest to the tallest, but they are not very good at it. The corporal wants to know who is at least *locally correct*: a soldier is placed locally correctly (*lokalno pravilno*) if their left neighbour (if there is one) is shorter or equally tall, and their right neighbour (if there is one) taller or equally tall. Read $n \in [2, 100]$ and then $n$ heights from $[1, 10^9]$ (in the second line, separated by single spaces), and print the indices of all locally correct soldiers in ascending order, each on its own line; if there are none, print `NOBEDEN`.

```text
$ printf '10\n185 172 180 181 190 183 178 185 191 207\n' | java VrstaZbor
2
3
7
8
9
$ printf '6\n175 169 183 176 200 180\n' | java VrstaZbor
NOBEDEN
```

**Zgoščenke (drugič)** (CDs, second time) — we want to save files on $n$ empty CDs, each of which holds $k$ units of data. The files (none larger than $k$) are handled in order: each one goes to the CD with the most free space at the moment; if there are several, the first of them. Read $n \in [1, 100]$ and $k \in [1, 10^9]$, then the file sizes from $[1, k]$, one per line. For every successfully saved file print

```text
velikostDatoteke EP -> zgoscenka številkaZgoščenke zasedenostiZgoščenk
```

(file size, the CD's number from 1 on, and the used space of all CDs). The program stops when the files run out, or when the file does not fit even on the least used CD. The sheet suggests `Arrays.toString(t)`, which returns the array as the string `[e0, e1, …, en−1]`.

```text
$ printf '3 700\n300\n200\n500\n400\n400\n150\n200\n' | java ZgoscenkeDve
300 EP -> zgoscenka 1 [300, 0, 0]
200 EP -> zgoscenka 2 [300, 200, 0]
500 EP -> zgoscenka 3 [300, 200, 500]
400 EP -> zgoscenka 2 [300, 600, 500]
400 EP -> zgoscenka 1 [700, 600, 500]
150 EP -> zgoscenka 3 [700, 600, 650]
```

The last file (200) is not saved: the least used CD has 650, and $650 + 200 > 700$.

## Notes

### From my lab notes (`zapiski.txt`)

- The class `Arrays` (*razred Arrays*): sorting (*urejanje*), shuffle, comparison (*primerjava*), representation as a string (*predstavitev kot string*).
- `Arrays.toString(imeTabele);`
- A property of Java (*lastnost jave*) →
  - `true` or something (*true ali neki*)
  - `false` and something (*false in neki*)

The last two lines are [[Short-circuit Evaluation|short-circuit evaluation]]: `true || …` is already `true` and `false && …` already `false`, so Java does not evaluate the right-hand side.

### Vrsta zbor

- `preberiVisine` creates an array of length $n$ and fills it with the heights; the `Scanner` is passed in as a parameter (as in Beri last week).
- `lokalnoPravilno(t, ix)` is one expression with two parts joined by `&&`: the left neighbour is fine **and** the right neighbour is fine.
- Each part handles the missing neighbour with `||`: `ix == 0 || t[ix - 1] <= t[ix]`. For the first soldier `ix == 0` is `true`, so `t[ix - 1]` (which would be `t[-1]`, an `ArrayIndexOutOfBoundsException`) is never evaluated. The same holds for the last soldier with `ix == t.length - 1`. This is exactly the "`true` or something" from my notes.
- The first and the last soldier must still be checked: in test case 1 the last soldier (index 9, 207 cm) is locally correct.
- `NOBEDEN` needs a flag: `vsajEden` (*at least one*) becomes `true` at the first printed index, and `NOBEDEN` is printed after the loop only if it stayed `false`.

### Zgoščenke (drugič)

- `zasedenosti[i]` is the used space of CD `i`; a new `int` array is all zeros, so all CDs start empty.
- The CD with the most free space is the one with the least used space, so the solution only needs `indeksMinimuma` (the same method as in the lecture's *Primer*). The comparison is strict (`t[i] < t[ixMin]`), so for equal values the first CD stays, as the task requires.
- `while (sc.hasNextInt())` reads files until the input runs out; `break` ends the loop when the file does not fit on the least used CD.
- The output numbers the CDs from 1, so it prints `ixZgoscenke + 1`.
- `vNiz` builds the same string as `Arrays.toString` with a `StringBuilder` ("in case `Arrays.toString` stinks to us"); it is not used in `main`.

### Izštevanka

- A counting-out rhyme (*izštevanka*) with `stBesed` words among `stOtrok` children: the child at index `(stBesed - 1) % stOtrok` drops out, and the game is repeated until one child is left (`stOtrok - 1` rounds). Each round counting starts again at the first remaining child.
- Removing an element from an array is not possible directly, since the length of an array is fixed. The assistant showed two ways:
  - v.1 (commented out): shift the elements right of `ix` one place to the left and keep the *effective length* `d` of the array (`stOtrokVIgri`);
  - v.2: make a new array that is one element shorter and copy everything except index `ix` into it (`izloci(t, ix)` returns the new array, so `main` assigns `otroci = izloci(otroci, ixIzpadlega)`).

### TestSudoku and Sinus (skeletons)

- TestSudoku reads an $N \times N$ `int[][]` and prints it with lines between the $3 \times 3$ blocks; the checks `containsAll`, `blockContainsAll` and `isSudokuValid` (rows, columns, $3 \times 3$ squares) are empty and return `false`, so it prints `false` even for a valid sudoku.
- Sinus creates a `char[27][115]` "drawing board" (*risalna plošča*) and prints it; `narisiSinus` is empty, so the board contains only `'\0'` (the default value of `char`).

## Code

### Vrsta zbor (assistant's solution)

```java
import java.util.Scanner;

public class VrstaZbor {
	
	/** 
	 * Naredi tabelo, prebere visine vojakov in jo vrne
	 */
	
	private static int[] preberiVisine(int n, Scanner sc) {
		int[] t = new int[n];
		for (int i = 0; i < t.length; i++)
			t[i] = sc.nextInt();
		return t;
	}
	
	private static void izpisi(int[] t) {
		System.out.printf("[");
		for (int i = 0; 
		i < t.length; i++) {
			if (i > 0)
				System.out.printf(", ");
			System.out.printf("%d", t[i]);
		}
		System.out.printf("]%n");
	}
	
	/** 
	 * Vrne true natanko v primeru, ce je element tabele 't' na indeksu 'ix' vecji
	 * ali enak kot njegov levi sosed in hkrati manjsi ali enak kot njegov desni sosed.
	 */
	
	private static boolean lokalnoPravilno(int[] t, int ix) {
		return (ix == 0 || t[ix - 1] <= t[ix]) && 
				(ix == t.length - 1 || t[ix] <= t[ix + 1]);
	}

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int stVojakov = sc.nextInt();
		int[] visine = preberiVisine(stVojakov, sc);
		// izpisi(visine);
		
		// izpisi indekse pravilno postavljenih oz. NIHCE
		boolean vsajEden = false;
		for (int i = 0; i < visine.length; i++) {
			if (lokalnoPravilno(visine, i)) {
				System.out.println(i);
				vsajEden = true;
			}
		}
		if (!vsajEden) {
			System.out.println("NOBEDEN");
		}
		
		
	}
}
```

My lab solution (`Zbor.java`) has the same structure (`preberiVisine`, `lokalnoPravilno`, a flag), but joins the two neighbours with `||` instead of `&&`, so one good neighbour is already enough. It passes 4/10 tests; on test case 1 it prints `1 2 3 4 6 7 8 9` instead of `2 3 7 8 9`, and on test case 2 `1 2 3 4` instead of `NOBEDEN`:

```java
private static boolean lokalnoPravilno(int[] t, int ix) {
	if (ix > 0 && t[ix - 1] <= t[ix] || ix < t.length - 1 && t[ix] <= t[ix + 1]) {
		return true;
	} 
	return false;

}
```

My version from home (`doma/Zbor.java`) uses `&&`, but only counts soldiers that have both neighbours, so the first and the last soldier are never printed. It passes 3/10 tests; on test case 1 it prints `2 3 7 8` (the last soldier, 9, is missing):

```java
for (int i = 0; i <= steviloVojakov; i++) {
    if ((i - 1 >= 0 && i + 1 < steviloVojakov) && (vojaki[i - 1] <= vojaki[i]) && (vojaki[i] <= vojaki[i + 1] )) {
        System.out.println(i);
        vsajEn = true;
    }
}
```

### Zgoščenke (drugič) (assistant's solution)

```java
import java.util.Scanner;
import java.util.Arrays;

public class ZgoscenkeDve {

	/** ce nam Arrays.toString smrdi... */

	private static String vNiz(int[] t) {
		StringBuilder sb = new StringBuilder("[");
		for (int i = 0; i < t.length; i++) {
			if (i > 0)
				sb.append(", ");
			sb.append(t[i]);
		}
		sb.append("]");
		return sb.toString();
	}

	/** Vrne indeks najmanjsega elementa v tabeli. */
	
	private static int indeksMinimuma(int[] t) {
		int ixMin = 0;
		for (int i = 1; i < t.length; i++) {
			if (t[i] < t[ixMin])
				ixMin = i;
		}
		return ixMin;
	}

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int stZgoscenk = sc.nextInt();
		int kapacitetaZgoscenke = sc.nextInt();
		
		int[] zasedenosti = new int[stZgoscenk];
		
		while (sc.hasNextInt()) {
			int fileSize = sc.nextInt();
			
			// indeks najmanj zasedene zgoscenke
			int ixZgoscenke = indeksMinimuma(zasedenosti);
			if (fileSize + zasedenosti[ixZgoscenke] > kapacitetaZgoscenke) {
				break;
			}
			zasedenosti[ixZgoscenke] += fileSize;
			
			System.out.printf("%d EP -> zgoscenka %d %s%n", 
						fileSize, ixZgoscenke + 1, Arrays.toString(zasedenosti));
		}
		
		
		
	}
}
```

My lab solution (`Zgoscenke2.java`) puts saving one file into a method `zapisDatoteke` that returns whether it succeeded, and `main` calls it in a `do`–`while`. As it is, it **does not compile**: in `indeksMinimuma` the variable is misspelled (`indeksMinumima = i;` → `cannot find symbol`). With the typo fixed it passes all 10 tests, but when the files run out `sc.nextInt()` throws a `NoSuchElementException` (it does not check `hasNextInt()`), so the program ends with an exception after the correct output.

```java
public static boolean zapisDatoteke (int[] t, Scanner sc, int kapacitetaZgoscenke) {
	int vrednost = sc.nextInt();
	int a = indeksMinimuma(t);
	
	if (t[a] + vrednost <= kapacitetaZgoscenke) {
		t[a] += vrednost;
		
		System.out.printf("%d EP -> zgoscenka %d %s%n", vrednost, a + 1, Arrays.toString(t));
		return true;
	} 
	return false;
}
```

### Extra: Izštevanka (assistant's solution)

```java
import java.util.Scanner;
import java.util.Arrays;

public class Izstevanka {

	/** 
	 * Vrne indeks otroka, ki izpade.
	 *
	 * @param stOtrok "stevilo (preostalih) otrok
	 * @param stBesed "stevilo besed izstevanke
	 * @return indeks izpadlega otroka
	 */
	
	private static int kdoIzpade(int stOtrok, int stBesed) {
		return (stBesed - 1) % stOtrok;
	}

	/** 
	 * Izloci element z indeksom 'ix' iz tabele 't' tako, da elemente tabele
	 * 't' desno od indeksa 'ix' pomakne za eno mesto v levo.
	 *
	 * @param t tabela z imeni otrok
	 * @param ix indeks izpadlega otroka
	 * @param d efektivna dolzina tabele (do kod se nam splaca pomikati)
	 */
	 
	private static void izloci(String[] t, int ix, int d) {
		for (int i = ix; i < d - 1; i++)
			t[i] = t[i + 1];
	}
	
	private static String[] izloci(String[] t, int ix) {
		String[] nova = new String[t.length - 1];
		for (int i = 0, iNova = 0; i < t.length; i++) {
			if (i == ix)
				continue;
			nova[iNova] = t[i];
			iNova++;
		}
		return nova;
	}
	
	private static String[] preberiOtroke(int stOtrok, Scanner sc) {
		String[] t = new String[stOtrok];
		for (int i = 0; i < stOtrok; i++)
			t[i] = sc.next();
		return t;
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);

		int stOtrok = sc.nextInt();
		int stBesed = sc.nextInt();

		String[] otroci = preberiOtroke(stOtrok, sc);
		
		int stKrogov = stOtrok - 1;
		/*
		// v.1
		int stOtrokVIgri = stOtrok;
		
		for (int krog = 0; krog < stKrogov; krog++) {
			int ixIzpadlega = kdoIzpade(stOtrokVIgri, stBesed);
			System.out.println(otroci[ixIzpadlega]);
		
			izloci(otroci, ixIzpadlega, stOtrokVIgri);
			stOtrokVIgri--;
		}
		*/
		
		// v.2
		for (int krog = 0; krog < stKrogov; krog++) {
			int ixIzpadlega = kdoIzpade(otroci.length, stBesed);
			System.out.println(otroci[ixIzpadlega]);
		
			otroci = izloci(otroci, ixIzpadlega);
		}
	}
}
```

```text
$ echo 5 3 Ana Bor Cene Dana Eva | java Izstevanka
Cene
Dana
Eva
Ana
```

Bor is the last child left. The two methods `izloci` have the same name but different parameters ([[Method Overloading|overloading]]).

### Extra: TestSudoku (assistant's skeleton, unfinished)

Only the reading and the printing are written; the three checks are empty.

```java
private static int[][] preberiTabelo() {
	Scanner sc = new Scanner(System.in);
	int size = sc.nextInt();
	int[][] sudoku = new int[size][size];
	for (int i = 0; i < sudoku.length; i++) {
		for (int j = 0; j < sudoku[i].length; j++) {
			sudoku[i][j] = sc.nextInt();
		}
	}
	return sudoku;
}

private static boolean isSudokuValid(int[][] sudoku) {
	// 1 - preveri vrstice
	
	// 2 - preveri stolpce
	
	// 3 - preveri kvadrate velikosti 3 x 3
	
	return false;
}
```

```text
$ java TestSudoku < valid-sudoku.txt
+-------+-------+-------+
| 5 3 4 | 6 7 8 | 9 1 2 |
| 6 7 2 | 1 9 5 | 3 4 8 |
| 1 9 8 | 3 4 2 | 5 6 7 |
+-------+-------+-------+
| 8 5 9 | 7 6 1 | 4 2 3 |
| 4 2 6 | 8 5 3 | 7 9 1 |
| 7 1 3 | 9 2 4 | 8 5 6 |
+-------+-------+-------+
| 9 6 1 | 5 3 7 | 2 8 4 |
| 2 8 7 | 4 1 9 | 6 3 5 |
| 3 4 5 | 2 8 6 | 1 7 9 |
+-------+-------+-------+
false
```

`printf("+%1$s+%1$s+%1$s+%n", tile)` uses the same argument three times (`%1$s` = the first argument).

### Extra: Sinus (assistant's skeleton, unfinished)

```java
private static char[][] initPlosca(int visina, int sirina) {
	char[][] t = new char[visina][sirina];
	return t;
}

private static void narisiSinus(char[][] t, int kotZacetka) {
	
}
```

`main` calls `narisiSinus(plosca, -540)` and prints the board: 27 lines of 115 `'\0'` characters, so nothing visible yet.

## Questions

- [ ] In Izštevanka every round counts again from the first remaining child (`(stBesed - 1) % stOtrok`); is that the intended rule, or should counting continue from the child after the one who dropped out? (no statement on the sheet)

## Connections

- Course: [[Programming 1]]
- Lecture: [[2026-11-05 - Arrays, Searching and Sorting - 5]] — arrays, `Arrays.toString`, `indeksMinimuma`, default values
- Previous exercises: [[2026-11-02 - Exercises for Methods and Recursion - 4]] (Beri: passing a `Scanner` to a method)
- Exercises: [[Sources/programming_1/vaje/prog1/p1_vaje05/naFaksu/vaje05.pdf|vaje05]]
- Related: [[Array]], [[Short-circuit Evaluation]], [[Two-dimensional Array]], [[Method Overloading]], [[Method]]
- [[For Loop]], [[While Loop]], [[Do-while Loop]]

## Sources

- My lab notes: [[Sources/programming_1/vaje/prog1/p1_vaje05/naFaksu/zapiski.txt|zapiski.txt]]
- Assistant's solutions (reference): `programming_1/vaje/prog1/p1_vaje05/naFaksu/assistant/` (`VrstaZbor.java`, `ZgoscenkeDve.java`, `Izstevanka.java`, `TestSudoku.java`, `Sinus.java`)
- My code from the lab: `programming_1/vaje/prog1/p1_vaje05/naFaksu/` (`Zbor.java`, `Zgoscenke2.java`); from home: `programming_1/vaje/prog1/p1_vaje05/doma/Zbor.java`
