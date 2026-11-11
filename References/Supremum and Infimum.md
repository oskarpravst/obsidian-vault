---
type: "[[Concepts]]"
status: developed
aliases:
  - Supremum
  - Infimum
  - Natančna zgornja meja
  - Natančna spodnja meja
---

# Supremum and Infimum

## Definition

Let $A \subseteq \mathbb{R}$, $A \ne \emptyset$.

- $A$ is **bounded above** (*navzgor omejena*) if $\exists M \in \mathbb{R}: m \le M\ \forall m \in A$. Such an $M$ is an **upper bound** (*zgornja meja*).
- The **supremum** $\sup(A)$ is the **least upper bound**. If $\sup(A) \in A$, it is the **maximum** $\max(A)$.
- Analogously, the **infimum** $\inf(A)$ is the **greatest lower bound** (*spodnja meja*), and the **minimum** $\min(A)$ if it lies in $A$.

## Explanation

- In $\mathbb{R}$ every non-empty set that is bounded above **has** a supremum. This is the completeness of the real numbers, and it fails in $\mathbb{Q}$.
- The supremum need not be in the set: then the set has a supremum but no maximum.
- The same applies to a [[Sequence|sequence]], viewed as its set of terms: a sequence bounded above has $\sup(a_n)$.
- **Monotone convergence:** an increasing sequence that is bounded above converges to its supremum, $\lim a_n = \sup a_n$.

## Examples

| $A$ | $\sup$ | $\max$ |
|---|:-:|:-:|
| $(0, 5)$ | $5$ | — |
| $(1, 3]$ | $3$ | $3$ |
| $(5, \infty)$ | — | — |
| $(-\infty, 5]$ | $5$ | $5$ |

**Recursive sequence** (Calculus 4): $a_1 = 0$, $a_n = \frac{a_{n-1} + 6}{2}$ is increasing and bounded above by $6$, so it converges to $\sup a_n = 6$.

## Connections

- [[2026-10-11 - Numbers - 1]] — definitions, table of examples, infimum and minimum (Calculus)
- [[2026-10-21 - Spectral Decomposition and Sequences - 3]] — bounded sequences, $\sup(a_n)$ and $\inf(a_n)$ (Calculus)
- [[2026-10-28 - Limits of Sequences - 4]] — monotone convergence, $\lim a_n = \sup a_n$ (Calculus)
- [[2026-11-11 - Limits of Functions, Continuity and Zeros of Continuous Functions - 6]] — a continuous function on [a, b] reaches its inf and sup, inf = min, sup = max (Calculus)
- [[Sequence]], [[Limit of a Sequence]]

## Sources

- J. Globevnik, M. Brojan, *Analiza I* (2012), supremum and infimum: [[Sources/calculus/skripta.pdf#page=19|p. 9]]; monotone sequences: [[Sources/calculus/skripta.pdf#page=52|p. 42]]
