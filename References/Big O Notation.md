---
type: "[[Concepts]]"
status: developed
aliases:
  - O-notation
  - Bachmann–Landau notation
  - Bachmann-Landauova notacija
  - Asimptotična zahtevnost
---

# Big O Notation

## Definition

Let $f, g: \mathbb{N} \to \mathbb{N}$ (*Bachmann–Landau notation*).

- **Big O:** $f(n) = O(g(n))$ if $\dfrac{f(n)}{g(n)}$ is bounded. $f$ is **asymptotically bounded** by $g$.
- **Small o:** $f(n) = o(g(n))$ if $\lim\limits_{n \to \infty}\dfrac{f(n)}{g(n)} = 0$. $g$ **asymptotically dominates** $f$.

## Explanation

- It describes how fast a function grows for large $n$, ignoring constant factors. In computer science $f(n)$ is usually the number of steps an algorithm needs for input size $n$ ([[Time Complexity|time complexity]]).
- It is defined through a bounded quotient or a [[Limit of a Sequence|limit]] of a sequence, which is why it appears in Calculus.
- The base of a logarithm does not matter inside $O$: $\log_2 n$ and $\ln n$ differ only by a constant factor.
- **P** $= \bigcup_q O(n^q)$ is the class of problems solvable in polynomial time. **NP** is the class of problems whose solution can be checked in polynomial time. Whether $\mathrm{P} = \mathrm{NP}$ is open ([[P versus NP]]).

## Examples

| problem | complexity |
|---|---|
| largest element in a list of length $n$ | $O(n)$ |
| [[Linear Search\|linear search]] | $O(n)$ |
| [[Binary Search\|binary search]] in a sorted list | $O(\log n)$ |
| brute-force sort, $0 + 1 + \dots + (n-1) = \frac{n(n-1)}{2}$ comparisons, e.g. [[Insertion Sort\|insertion sort]] | $O(n^2)$ |
| merge sort | $O(n \log n)$ |

## Connections

- [[2026-10-28 - Limits of Sequences - 4]] — definition of $O$ and $o$, examples, P and NP (Calculus)
- [[2026-11-05 - Arrays, Searching and Sorting - 5]] — linear search needs up to $n$ steps, binary search about $\log_2 n$ (Programming 1)
- [[Limit of a Sequence]], [[Binary Search]], [[Time Complexity]], [[P versus NP]]

## Sources

- [Big O notation — Wikipedia](https://en.wikipedia.org/wiki/Big_O_notation)
