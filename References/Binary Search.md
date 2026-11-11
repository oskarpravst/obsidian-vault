---
type: "[[Concepts]]"
status: developed
aliases:
  - Dvojiško iskanje
  - Bisekcija
  - Bisection
---

# Binary Search

## Definition

**Binary search** (*dvojiško iskanje, bisekcija*) finds an element `x` in a **sorted** array by repeatedly comparing it with the middle element of the remaining part and throwing away the half where `x` cannot be.

## Explanation

- Keep a left bound `lm` and a right bound `dm`. Look at `s = (lm + dm) / 2`:
  - `t[s] == x`: found
  - `x > t[s]`: `lm = s + 1`
  - `x < t[s]`: `dm = s - 1`
- Repeat **while `lm <= dm`**. When `lm == dm` there is still one element left to check. When `lm > dm` the element is not there.
- Every step halves the interval, so it needs about $\log_2 n$ steps: $O(\log n)$ instead of $O(n)$ for [[Linear Search|linear search]] ([[Big O Notation]]). For 100 elements that is at most 7 steps.
- It only works on a **sorted** array, so it always pays off to keep lists sorted.
- The same halving idea is the best strategy for the number-guessing game.

## Examples

**`dvojiskoIskanje`** (Programming 1, lecture 5, class code `Poisci`):

```java
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
```

**Guessing a number** (lecture 3): always guess the middle of the remaining interval. For an upper bound of 100 at most $\lceil \log_2 100 \rceil = 7$ guesses are needed.

## Connections

- [[2026-10-22 - Loop Examples, break and switch - 3]] — guessing a number, at most 7 guesses (Programming 1)
- [[2026-11-05 - Arrays, Searching and Sorting - 5]] — binary search in a sorted array (Programming 1)
- [[Array]], [[Linear Search]], [[Big O Notation]], [[Logarithm]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/05_tabele_h.pdf|05 Tabele]] (Luka Fürst), searching pp. 19–26
