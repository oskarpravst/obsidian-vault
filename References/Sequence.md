---
type: "[[Concepts]]"
status: developed
aliases:
  - Zaporedje
  - Zaporedja
---

# Sequence

## Definition

A **sequence** (*zaporedje*) is a map

$$\mathbb{N} \to \mathbb{R}, \qquad n \mapsto a_n$$

written $(a_n)_n = (a_1, a_2, \dots)$. $n$ is the **index** (*indeks*) and $a_n$ the **term** (*člen*). Like an array, the order of the terms matters.

## Explanation

**Ways to define a sequence:**

- **explicitly** (*eksplicitno*): $a_n = f(n)$
- **recursively** (*rekurzivno*): one-term $a_{n+1} = f(a_n)$ with an initial term, or multi-term with the first few terms (e.g. the [[Fibonacci Sequence|Fibonacci sequence]])

**Properties** (*lastnosti*): a sequence is

- **bounded above / below** (*navzgor / navzdol omejeno*) if some $M$ / $m$ satisfies $a_n \le M$ / $a_n \ge m$ for all $n$; then it has a [[Supremum and Infimum|supremum / infimum]]
- **bounded** (*omejeno*) if it is bounded above and below
- **increasing** (*naraščajoče*) if $a_{n+1} \ge a_n$ (strictly if $>$), **decreasing** (*padajoče*) if $a_{n+1} \le a_n$
- **monotone** (*monotono*) if it is increasing or decreasing

A sequence is **convergent** if it has a [[Limit of a Sequence|limit]], otherwise **divergent**.

**Graphical display** of $a_{n+1} = f(a_n)$ (cobweb plot): go up from $a_n$ to the graph of $f$, across to $y = x$, and repeat. A limit can only be at an intersection of $f$ and $y = x$.

## Examples

| sequence | definition |
|---|---|
| arithmetic (*aritmetično*) | $a_n = a_1 + (n-1)k$, $a_{n+1} = a_n + k$ |
| geometric (*geometrijsko*) | $a_n = a_1 q^{n-1}$, $a_{n+1} = a_n q$ |
| alternating | $((-1)^n)_n = (-1, 1, -1, \dots)$, bounded but divergent |
| [[Collatz Conjecture\|Collatz]] | $a_{n+1} = a_n/2$ if even, $3a_n + 1$ if odd |
| recursive (Calculus 4) | $a_1 = 0$, $a_n = \frac{a_{n-1} + 6}{2}$, increasing, bounded by 6, limit 6 |

The partial sums of a sequence form a new sequence, whose limit is the sum of a [[Series|series]].

## Connections

- [[2026-10-21 - Spectral Decomposition and Sequences - 3]] — definition, explicit and recursive sequences, properties (Calculus)
- [[2026-10-28 - Limits of Sequences - 4]] — limits, accumulation points, monotone convergence (Calculus)
- [[Limit of a Sequence]], [[Supremum and Infimum]], [[Fibonacci Sequence]], [[Collatz Conjecture]], [[Series]], [[Mathematical Induction]], [[Array]]

## Sources

- J. Globevnik, M. Brojan, *Analiza I* (2012), 2.2 sequences: [[Sources/calculus/skripta.pdf#page=43|p. 33]]; 2.5 monotone sequences: [[Sources/calculus/skripta.pdf#page=51|p. 41]]
