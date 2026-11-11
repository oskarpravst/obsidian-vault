---
type: "[[Concepts]]"
status: developed
aliases:
  - Fibonaccijevo zaporedje
  - Fibonacci numbers
---

# Fibonacci Sequence

## Definition

The **Fibonacci sequence** (*Fibonaccijevo zaporedje*) is a multi-term recursive [[Sequence|sequence]] where every term is the sum of the previous two:

$$F_n = \begin{cases} 0 & n = 0 \\ 1 & n = 1 \\ F_{n-2} + F_{n-1} & \text{otherwise} \end{cases} \qquad 0, 1, 1, 2, 3, 5, 8, 13, 21, \dots$$

## Explanation

- The two courses index it differently. Calculus starts with $a_1 = a_2 = 1$. Programming 1 starts with $F_0 = 0$, $F_1 = 1$. It is the same sequence, shifted by one index.
- A **recurrence relation** (*rekurenčna enačba*) translates directly into a recursive [[Method|method]] ([[Recursion|recursion]]).
- **Plain recursion is very slow.** `fib(n)` calls `fib(n-1)` and `fib(n-2)`, and whole subtrees of calls repeat, so the number of calls grows exponentially.
- **[[Memoization]]** fixes this: an [[Array|array]] stores the values already computed, so each $F_k$ is computed only once (linear time).

## Examples

**Recursive version** (Programming 1, lecture 4):

```java
public static long fib(int n) {
    if (n <= 1) return n;
    return fib(n - 2) + fib(n - 1);
}
```

This is a minimal sketch of the idea. The class versions are `Fibonacci` (lecture 4) and `FibonacciMemo` (lecture 5), shown in those lecture notes.

**Recursive definition in Calculus** (Calculus 3): $a_1 = a_2 = 1$, $a_n = a_{n-1} + a_{n-2}$, an example of a multi-term recursion.

## Connections

- [[2026-10-21 - Spectral Decomposition and Sequences - 3]] — example of a multi-term recursive sequence (Calculus)
- [[2026-10-29 - Methods and Recursion - 4]] — recursive program, very inefficient (Programming 1)
- [[2026-11-05 - Arrays, Searching and Sorting - 5]] — Fibonacci with memoization (Programming 1)
- [[Sequence]], [[Recursion]], [[Memoization]], [[Mathematical Induction]]

## Sources

- J. Globevnik, M. Brojan, *Analiza I* (2012), recursive sequences: [[Sources/calculus/skripta.pdf#page=44|p. 34]]
- Slides: [[Sources/programming_1/prosojnice/05_tabele_h.pdf|05 Tabele]] (Luka Fürst), Fibonacci with memoization pp. 38–42
