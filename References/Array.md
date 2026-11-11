---
type: "[[Concepts]]"
status: developed
aliases:
  - Tabela
  - Tabele
  - Arrays
---

# Array

## Definition

An **array** (*tabela*) is a sequence of variables of **the same type**, reached through **indices** (*indeksi*). The variables are the **elements / cells** (*elementi / celice*) of the array. Valid indices go from `0` to `t.length - 1`.

```text
t = | 25 | 42 | 17 | 54 | 20 | 36 |
      0    1    2    3    4    5      ← indices
```

## Explanation

- **Creating** (`int[]` is the type):

```java
int[] t = {25, 42, 17, 54, 20, 36};   // concrete elements
int[] u = new int[10];                // 10 elements with default values
```

- **The length is fixed.** `t.length` cannot change, so we cannot add elements like to a Python list. The **elements themselves can be changed**: `t[3] = 5`.
- **Default values** in `new T[n]`: `0` for integer types, `'\0'` for `char`, `false` for `boolean`, `null` for reference types.
- **Out of bounds:** `t[t.length]` throws `ArrayIndexOutOfBoundsException` at **runtime**. The compiler does not catch it.
- **Walking through:** with an index (`for (int i = 0; i < t.length; i++)`), or with the [[Enhanced For Loop|for-each loop]] when we do not need indices. In for-each the variable is a **copy**, so `element++` does not change the array. For that we need `t[i]++`.
- **Counters in an array:** instead of 5 separate counters, `frekvence[ocena - 1]++`.
- `Arrays.toString(t)` returns the array as a string (`import java.util.Arrays;`).
- Typical algorithms on arrays: [[Linear Search|linear search]], [[Binary Search|binary search]] (sorted array), [[Insertion Sort|insertion sort]], the [[Sieve of Eratosthenes|sieve of Eratosthenes]], [[Memoization|memoization]].

## Examples

**JShell** (Programming 1, lecture 5):

```text
jshell> int[] t = new int[3];
t ==> int[3] { 0, 0, 0 }

jshell> System.out.println(t[t.length]);
|  Exception java.lang.ArrayIndexOutOfBoundsException: Index 3 out of bounds for length 3
```

**Lab exercises** (week 5): both tasks first read the input into an array and then work on it.

## Connections

- [[2026-09-22 - Introduction to Academic Studies - 0]] — open question about changing arrays (Programming 1)
- [[2026-11-05 - Arrays, Searching and Sorting - 5]] — arrays, default values, for-each, searching, sorting, sieve, memoization (Programming 1)
- [[2026-11-09 - Exercises for Arrays, Searching and Sorting - 5]] — reading input into an array (Programming 1)
- [[Enhanced For Loop]], [[Binary Search]], [[Linear Search]], [[Insertion Sort]], [[Sieve of Eratosthenes]], [[Two-dimensional Array]], [[Sequence]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/05_tabele_h.pdf|05 Tabele]] (Luka Fürst), arrays pp. 3–7
