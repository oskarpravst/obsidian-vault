---
type: "[[Concepts]]"
status: developed
aliases:
  - Limita zaporedja
  - Limita
  - Convergence
  - Konvergenca
---

# Limit of a Sequence

## Definition

$a \in \mathbb{R}$ is the **limit** (*limita*) of the [[Sequence|sequence]] $(a_n)_n$, written $a = \lim\limits_{n \to \infty} a_n$, if

$$\forall \varepsilon > 0\ \ \exists N \in \mathbb{N}:\ |a - a_n| < \varepsilon \quad \forall n \ge N$$

A sequence with a limit is **convergent** (*konvergentno*), otherwise it is **divergent** (*divergentno*).

## Explanation

- Every interval $(a - \varepsilon, a + \varepsilon)$, however small, contains **all terms from some $N$ on**. It is the idea of "knowing" a number like $\pi$: we can compute it to any precision $\varepsilon$.
- $\varepsilon > 0$ is essential ($\ge 0$ would be a different concept); $n \ge N$ or $n > N$ does not matter.
- **Growing over every bound:** $\lim a_n = \infty$ if $\forall M\ \exists N: a_n \ge M\ \forall n \ge N$. This is **not** convergence.
- **Accumulation point** (*stekališče*): every $\varepsilon$-interval around it contains infinitely many terms. Every limit is an accumulation point, but not the other way round: $(-1)^n$ has the two accumulation points $\pm 1$ and no limit.
- **Facts:** every convergent sequence is bounded. Every bounded sequence has an accumulation point.
- **Rules:** limits respect $+$, $-$, $\cdot$ and $/$ (if $b \ne 0$). The indeterminate forms are $\infty - \infty$, $\frac{\infty}{\infty}$, $1^\infty$, $\frac{0}{0}$.
- **Comparison:** $a_n \le b_n \le c_n \implies \lim a_n \le \lim b_n \le \lim c_n$.
- **Monotone convergence:** an increasing sequence converges iff it is bounded above, and then $\lim a_n = \sup a_n$ ([[Supremum and Infimum]]).

## Examples

**By definition** (Calculus 4): $\left|\frac{1}{n^2} - 0\right| < \varepsilon \iff n > \sqrt{1/\varepsilon}$, so $\frac{1}{n^2} \to 0$. For $1$ the inequality holds only for small $n$, so $1$ is not the limit.

**Standard limits** (Calculus 4): $\sqrt[n]{n} \to 1$, $\left(1 + \frac{1}{n}\right)^n \to e$, $a^n \to 0$ for $|a| < 1$.

**$\frac{\infty}{\infty}$**: $\frac{2n^2 - 5}{n^2 + n - 6} \to 2$ (divide by $n^2$).

**Recursive sequence** (Calculus 4): $a_1 = 0$, $a_n = \frac{a_{n-1} + 6}{2}$. The candidate $A = \frac{A + 6}{2} = 6$ is valid only once [[Mathematical Induction|induction]] shows the sequence is increasing and bounded by 6.

**Series** (Calculus 5): the sum of a [[Series|series]] is the limit of its partial sums.

## Connections

- [[2026-10-21 - Spectral Decomposition and Sequences - 3]] — constructing the limit, $\varepsilon$–$N$ definition (Calculus)
- [[2026-10-28 - Limits of Sequences - 4]] — examples, accumulation points, rules, convergence theorems (Calculus)
- [[2026-11-04 - Series and Convergence Tests - 5]] — the sum of a series as a limit (Calculus)
- [[2026-11-11 - Limits of Functions, Continuity and Zeros of Continuous Functions - 6]] — limits of functions are computed with sequences, the same rules (Calculus)
- [[Sequence]], [[Supremum and Infimum]], [[Series]], [[Mathematical Induction]], [[Big O Notation]]

## Sources

- J. Globevnik, M. Brojan, *Analiza I* (2012): 2.4 convergent sequences [[Sources/calculus/skripta.pdf#page=46|p. 36]]; accumulation points [[Sources/calculus/skripta.pdf#page=45|p. 35]]; convergent sequences are bounded [[Sources/calculus/skripta.pdf#page=51|p. 41]]; monotone sequences [[Sources/calculus/skripta.pdf#page=52|p. 42]]; rules [[Sources/calculus/skripta.pdf#page=54|p. 44]]; limit $+\infty$ [[Sources/calculus/skripta.pdf#page=57|p. 47]]
