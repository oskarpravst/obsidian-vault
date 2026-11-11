---
type: "[[Concepts]]"
status: developed
aliases:
  - Eratostenovo sito
  - Eratostenovo rešeto
---

# Sieve of Eratosthenes

## Definition

The **sieve of Eratosthenes** (*Eratostenovo sito / rešeto*) lists all [[Prime Number|primes]] up to a bound $n$. Write down $2, \dots, n$. Take the smallest number not yet crossed out, $p$ (a prime), and cross out all its multiples $2p, 3p, \dots$. Repeat with the next uncrossed number. The numbers left are the primes.

## Explanation

- It is enough to sieve with $p \le \sqrt{n}$: every composite number $\le n$ has a prime divisor $\le \sqrt{n}$, so it is already crossed out.
- In Java a `boolean` [[Array|array]] of length $n + 1$ marks which numbers are crossed out. A new `boolean` array is all `false`, so at the start nothing is crossed out.
- It does no divisions at all, only additions (`i += p`), which is why it is much faster than testing each number separately.

## Examples

**`PrastevilaZadnja`** (Programming 1, lecture 5), the core of the class code:

```java
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
```

The numbers $i \ge 2$ with `!sestavljeno[i]` are printed. For `30` the output is `2 3 5 7 11 13 17 19 23 29`.

## Connections

- [[2026-10-22 - Loop Examples, break and switch - 3]] — announced as version 5 of the prime numbers program (Programming 1)
- [[2026-11-05 - Arrays, Searching and Sorting - 5]] — implementation with a `boolean` array (Programming 1)
- [[Prime Number]], [[Array]], [[Boolean]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/05_tabele_h.pdf|05 Tabele]] (Luka Fürst), sieve of Eratosthenes pp. 35–37
