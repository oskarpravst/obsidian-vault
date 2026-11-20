---
type: "[[Lectures]]"
course: "[[Programming 1]]"
date: 2026-11-16
week: "6"
---

# 2026-11-16 - Exercises for Reference Types, 2D Arrays and Classes

## Main Idea

Lab exercises (*vaje*) for week 6, *Arrays 2* (*Tabele 2*). The main task, Volitve (elections), works on a three-dimensional array `int[][][]` — an array of arrays of arrays, as in the lecture on [[Two-dimensional Array|two-dimensional arrays]]. Each method walks over a different pair of dimensions: summing over polling stations, building a 2D table of totals, looking for the index of a maximum over years, and counting a ranking. `Volitve` has no `main`: it is a class of [[Static Method|static methods]] that test classes call, i.e. a library (*knjižnica*). This week the tests are therefore test classes (`Test01.java` …) instead of input files. The assistant also showed Mravlja (ant): counting paths on a wall with [[Recursion|recursion]] and with [[Memoization|memoization]], and an unfinished skeleton StolpicniDiagram. The assistant's solutions are the reference solutions below.

## Tasks

**Volitve** — in Butale there are elections every year, always with the same parties and the same polling stations. Counting starts at year 0, and parties and polling stations are indexed from 0. Professor Butnik wrote the results of all elections into a table `int[][][]` of size $L \times S \times V$ ($L$ years, $S$ parties, $V$ polling stations; $L, S, V > 0$). The element `t[l][s][v]` is the number of votes that party `s` received in year `l` at polling station `v`. Complete the class `Volitve` with:

- `public static int steviloGlasov(int[][][] t, int leto, int stranka)` — the total number of votes (over all polling stations) of the given party in the given year. (tests 1–3)
- `public static int[][] glasovi(int[][][] t)` — for every year and every party the number of votes in that year, returned as a table of size $L \times S$. (tests 4–6)
- `public static int najVolisce(int[][][] t, int stranka)` — the index of the polling station where the party received the most votes summed over all years; if there are several, the first one. (tests 7–9)
- `public static int vsotaUvrstitev(int[][][] t, int stranka, int volisce)` — the sum of the party's rankings (*uvrstitev*) at the given polling station over all years. E.g. for $L = 3$, places 3, 4 and 1 give $3 + 4 + 1 = 8$. The ranking of a party in a year at a polling station is $1 + n_>$, where $n_>$ is the number of parties that received strictly more votes there that year. (tests 10–12)

**Testing:** this time each test is a test class that builds a table of results, calls one of the methods at least once and prints the results. `tj.exe` is run as `tj.exe <folder with Volitve> <folder with tests> <folder with results>` (the first argument is the folder that contains `Volitve.java`, not the file itself); if everything is in one folder, simply `tj.exe`.

Tests 1, 4, 7 and 10 all use this table ($L = 3$, $S = 5$, $V = 4$):

```java
int[][][] volitve = {
    {
        {20,  5,  0, 10},
        {30, 40, 45, 25},
        {50, 20, 20, 15},
        { 0, 15,  5, 25},
        { 0, 20, 30, 25},
    },
    {
        {60,  5, 25,  0},
        {10, 15, 15, 30},
        {10, 65, 15, 55},
        { 0,  5, 25,  0},
        {20, 10, 20, 15},
    },
    {
        {20, 10, 10,  0},
        { 5, 30,  5, 90},
        {15, 30, 10, 10},
        {40, 20,  5,  0},
        {20, 10, 70,  0},
    },
};
```

```text
$ java Test01        # steviloGlasov for every year (row) and party (column)
  35 140 105  45  75
  90  70 145  30  65
  40 130  65  65 100
$ java Test04        # Arrays.deepToString(Volitve.glasovi(volitve))
[[35, 140, 105, 45, 75], [90, 70, 145, 30, 65], [40, 130, 65, 65, 100]]
$ java Test07        # najVolisce for every party
0
3
1
0
2
$ java Test10        # vsotaUvrstitev for every party (row) and polling station (column)
   6  13   8  12
  10   4   9   4
   8   4   9   7
  10  11   9   8
   8   9   6   7
```

## Notes

### From my lab notes (`zapiski.txt`)

- If (a class has) only static methods → a library (*knjižnica*).
- `tj` folder-with-classes tests results `-threads 10`
- switch (*stikalo*) `-p 1-4`
- `Arrays.deepToString(izidi)`
- The ants (*mravlje*) could also be done with [[Dynamic Programming|dynamic programming]] (*dinamično programiranje*).

`Arrays.toString` prints only the outer level of a multi-dimensional array (the addresses of the inner arrays); `Arrays.deepToString` prints the nested arrays as well, as in Test04.

### Volitve

- The indices are always `t[leto][stranka][volisce]`; the loop bounds come from the lengths: `t.length` = years, `t[leto].length` = parties, `t[leto][stranka].length` = polling stations.
- `steviloGlasov` fixes the year and the party and sums the innermost array `t[leto][stranka]`.
- `glasovi` creates a new `int[t.length][t[0].length]` table ($L \times S$) and fills every cell by calling `steviloGlasov` — reusing the first method instead of a third nested loop.
- `najVolisce` fixes the party and swaps the order of the loops: the outer loop goes over polling stations, the inner one sums over **years**. The comparison is strict (`>`), so for equal sums the first polling station stays.
- `vsotaUvrstitev` follows the definition: for each year the ranking starts at 1 and increases for every party `s` with strictly more votes at that polling station (`>`; parties with equal votes share the place). The rankings are summed over years.
- The comments `[1-3]`, `[4-6]`, … in the assistant's code are the numbers of the tests for each method.

### Mravlja (extra)

`stPoti(visina, sirina)` counts the paths from the upper left to the lower right corner of a wall of the given height and width. A wall that is one row high or one column wide has exactly one path; otherwise the paths split into those that go through the wall one row lower and one column narrower: `stPoti(v - 1, s) + stPoti(v, s - 1)`. Plain recursion recomputes the same subproblems many times, so `stPotiMemo` stores the results in `memo[v][s]` (0 = not computed yet). Because a $v \times s$ wall has as many paths as an $s \times v$ wall, it also checks `memo[s][v]`.

### StolpicniDiagram (extra, skeleton)

A bar chart (*stolpični diagram*) drawn into a `char[27][115]` "drawing board" (*risalna plošča*), like Sinus last week. `initPlosca` fills it with spaces and draws the $x$ axis (`'-'`) at 2/3 of the height. `narisiStolpec` and `narisiStolpicniDiagram` are empty, so only the axis is printed.

## Code

### Volitve (assistant's solution)

```java
public class Volitve {

	//  izidi[stevilo let][stevilo strank][stevilo volisc]
	
	/**
	 * Vrne skupno stevilo glasov, ki jih je v podanem letu kumulativno 
	 * prejela stranka. [1-3]
	 *
	 * @return	stevilo glasov
	 */
	 
	public static int steviloGlasov(int[][][] t, int leto, int stranka) {
		int stGlasov = 0;
		for (int volisce = 0; volisce < t[leto][stranka].length; volisce++)
			stGlasov += t[leto][stranka][volisce];
		return stGlasov;
	}

	/**	
	 * Za leto in stranko izracuna stevilo glasov, ki jih je stranka
	 * prejela v tistem letu. [4-6]
	 *
	 * @param t	izidi volitev za vso butalsko zgodovino
	 * @return	tabela[leto][stranka]
	 */

	public static int[][] glasovi(int[][][] t) {
		int[][] gls = new int[t.length][t[0].length];
		for (int leto = 0; leto < t.length; leto++) {
			for (int stranka = 0; stranka < t[leto].length; stranka++) {
				gls[leto][stranka] = Volitve.steviloGlasov(t, leto, stranka);
			}	
		}
		return gls;
	}
	
	/**
	 * Vrne indeks volisca, na katerem je stranka v skupnem sestevku 
	 * preko vseh let prejela najvec glasov. [7-9]
	 *
	 * @param t	izidi volitev za vso butalsko zgodovino
	 * @param stranka	stranka, ki nas zanima
	 * @return	indeks volisca
	 */	

	public static int najVolisce(int[][][] t, int stranka) {
		int stVolisc = t[0][stranka].length;
		int vMaxVolisce = 0;
		int iMaxVolisce = 0;
		
		for (int volisce = 0; volisce < stVolisc; volisce++) {
			int sumVolisce = 0;
			for (int leto = 0; leto < t.length; leto++) {
				sumVolisce += t[leto][stranka][volisce];
			}
			if (sumVolisce > vMaxVolisce) {
				vMaxVolisce = sumVolisce;
				iMaxVolisce = volisce;
			}
		}
		return iMaxVolisce;
	}

	/**
	 * Izracuna vsoto uvrstitev, ki jih je stranka dosegla na voliscu. [10-12]
	 *
	 * @param t			izidi volitev za vso butalsko zgodovino
	 * @param stranka	stranka, ki nas zanima
	 * @param volisce 	volisce, za katerega racunamo uvrstitev
	 * @return			vsota uvrstitev
	 */

	public static int vsotaUvrstitev(int[][][] t, int stranka, int volisce) {
		// volilni indeks, indeks uspesnosti stranke
		int sumUvrstitev = 0;
		for (int leto = 0; leto < t.length; leto++) {
			int uvrstitevVLetu = 1;
			
			for (int s = 0; s < t[leto].length; s++) {
				if (t[leto][s][volisce] > t[leto][stranka][volisce])
					uvrstitevVLetu++;
			}
			sumUvrstitev += uvrstitevVLetu;
		}
		return sumUvrstitev;
	}

	// pomozne metode
	
	private static void izpisi(int[][] t) {
		for (int i = 0; i < t.length; i++) {
			for (int j = 0; j < t[i].length; j++) {
				System.out.printf("%5d", t[i][j]);
			}
			System.out.println();
		}
	}
	
	// za rocno testiranje ...
	/*
	public static void main(String[] args) {
		// Arrays.deepToString(tabela)
		
		int[][] t = new int[5][];
		for (int i = 0; i < t.length; i++) {
			t[i] = new int[i + 1];
			for (int j = 0; j < t[i].length; j++)
				t[i][j] = i + j + 1;
		}
		izpisi(t);
	}
	*/
}
```

Passes all 12 tests.

My solution (`Volitve.java`) solves the first three methods differently but correctly: `steviloGlasov` uses a [[Enhanced For Loop|for-each loop]], and `najVolisce` moves the sum over years into its own helper method:

```java
	public static int steviloGlasov(int[][][] t, int leto, int stranka) {
		int steviloGlasov = 0;
		for (int element: t[leto][stranka]) {
			steviloGlasov += element;
		}
		return steviloGlasov;
	}

	public static int strankaGlasovi(int[][][]t, int stranka, int volisce) {
		int skupaj = 0;
		for (int i = 0; i < t.length; i++) {
			skupaj += t[i][stranka][volisce];
		}
		return skupaj;
	}
```

As it is, it **does not compile**: the started helper `uvrstitev(int[][][]t, int stranka, int volisce, int leto)` has an empty body (`missing return statement`), so it passes 0/12 tests. Without that unfinished method it passes tests 1–9; `vsotaUvrstitev` still returns `-1`, so tests 10–12 fail.

### Extra: Mravlja (assistant's solution)

```java
import java.util.Scanner;

public class Mravlja {

    /** 
     * Vrne stevilo poti od zgornjega levega do spodnjega desnega kota za
     * steno s podano visino in sirino.
     */

    private static long stPoti(int visina, int sirina) {
		if (visina == 1 || sirina == 1)
			return 1;
		
		return stPoti(visina - 1, sirina) + 
				stPoti(visina, sirina - 1);
    }

    /** 
     * Razlicica metode stPoti, ki uporablja memoizacijo --- pomnjenje ze
     * izracunanih vrednosti.
     * @param memo memo[v][s]: 0 oziroma ze izracunano stevilo poti za
     *    steno velikosti v x s ali s x v 
	 * @return stevilo poti
     */

	public static long stPotiMemo(int visina, int sirina, long[][] memo) {
		if (visina == 1 || sirina == 1)
			return 1;
		
		// 1 - ali je neka druga mravlja ze resila ta problem
		if (memo[visina][sirina] > 0)
			return memo[visina][sirina];
		if (memo[sirina][visina] > 0)
			return memo[sirina][visina];
		
		// 2 - (še vedno) vse mravlje do kolen v blato :\
		
		memo[visina][sirina] = stPotiMemo(visina - 1, sirina, memo) + 
								stPotiMemo(visina, sirina - 1, memo);
		return memo[visina][sirina];
	}

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int visina = sc.nextInt();
        int sirina = sc.nextInt();

		// v.1 - osnovna razlicica
        // System.out.println(stPoti(visina, sirina));
		
		// v.2 - memoizacija
		int m = Math.max(visina, sirina) + 1;
		long[][] memo = new long[m][m];
		System.out.println(stPotiMemo(visina, sirina, memo));
		
    }
}
```

```text
$ echo 3 3 | java Mravlja
6
$ echo 3 4 | java Mravlja
10
$ echo 10 10 | java Mravlja
48620
$ echo 17 17 | java Mravlja
601080390
```

My `Mravlja.java` is the empty skeleton (`stPoti` returns `-1`).

### Extra: StolpicniDiagram (assistant's skeleton, unfinished)

```java
import java.util.Scanner;
import java.util.Locale;

public class StolpicniDiagram {
	
	private static final int SIRINA = 115;
	private static final int VISINA = 27;
	
	/**
	 * Pomozne metode
	 */
	
	private static void izpisi(char[][] t) {
		for (int i = 0; i < t.length; i++) {
			for (int j = 0; j < t[i].length; j++) {
				System.out.printf("%c", t[i][j]);
			}
			System.out.println();
		}
	}
	
	private static double[] preberiPodatke() {
		Scanner sc = new Scanner(System.in).useLocale(Locale.US);
		int n = sc.nextInt();
		double[] data = new double[n];
		for (int i = 0; i < n; i++)
			data[i] = sc.nextDouble();
		return data;
	}	
	
	private static char[][] initPlosca(int visina, int sirina) {
		char[][] t = new char[visina][sirina];
		for (int i = 0; i < t.length; i++) {
			for (int j = 0; j < t[i].length; j++) {
				char value = ' ';
				if (i == 2 * t.length / 3)
					value = '-';
				t[i][j] = value;
			}	
		}
		return t;
	}
	
	/**
	 * Na risalni plosci na mestu (x, y) narise stolpec.
	 * @param t risalna plosca
	 * @param visina visina stolpca
	 * @param sirina sirina stolpca
	 */

	private static void narisiStolpec(char[][] t, int y, int x, int visina, int sirina) {
		
	}
	
	/**
	 * Na risalni plosci narise stolpcini diagram za podatke v tabeli data.
	 * Koordinata x se nahaja na 2/3 risalne plosce.
	 *
	 * @param t risalna plosca
	 * @param data podatki za stolpicni diagram
	 */
	
	private static void narisiStolpicniDiagram(char[][] t, double[] data) {
		
	}
	

	
	public static void main(String[] args) {
		double[] podatki = preberiPodatke();
		char[][] plosca = initPlosca(VISINA, SIRINA);
		narisiStolpicniDiagram(plosca, podatki);
		izpisi(plosca);
	}
}
```

With any input it prints 27 lines of spaces with a line of 115 `-` in row 19 (index 18 = `2 * 27 / 3`). My `StolpicniDiagram.java` is the same file.

## Questions

- [ ] 

## Connections

- Course: [[Programming 1]]
- Lecture: [[2026-11-12 - Reference Types, 2D Arrays and Classes - 6]] (multi-dimensional arrays as arrays of pointers, memoization)
- Previous exercises: [[2026-11-09 - Exercises for Arrays, Searching and Sorting - 5]] (Sinus drawing board, `Arrays.toString`)
- Exercises: [[Sources/programming_1/vaje/prog1/p1_vaje06/vaje06.pdf|vaje06]]
- Related: [[Array]], [[Two-dimensional Array]], [[Static Method]], [[Recursion]], [[Memoization]], [[Dynamic Programming]]

## Sources

- Lab notes: [[Sources/programming_1/vaje/prog1/p1_vaje06/zapiski.txt|zapiski.txt]]
- Assistant's solutions: `programming_1/vaje/prog1/p1_vaje06/assistant/` (`Volitve.java`, `Mravlja.java`, `StolpicniDiagram.java`)
- My solutions: `programming_1/vaje/prog1/p1_vaje06/` (`Volitve.java`, `Mravlja.java`, `StolpicniDiagram.java`)
- Tests: `programming_1/vaje/prog1/p1_vaje06/volitve/` (`Test01.java` … `Test12.java`, `test01.out` … `test12.out`)
