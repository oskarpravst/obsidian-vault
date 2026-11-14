---
type: "[[Lectures]]"
course: "[[Calculus]]"
date: 2026-11-04
week: "5"
---

# 2026-11-04 - Series and Convergence Tests

## Main Idea

**Series** (*vrste*): infinite sums of real numbers.

1. Motivation: Achilles and the tortoise, $0.333\ldots = \frac{1}{3}$, a square shaded half by half.
2. Definition of a [[Series|series]], its partial sums and its sum as a [[Limit of a Sequence|limit]]. If a series converges, its terms go to $0$; the [[Harmonic Series|harmonic series]] shows that the converse is false.
3. The [[Geometric Series|geometric series]] and when it converges; rules for computing with series.
4. **Dominance** of series ([[Comparison Test|comparison test]]) and [[Absolute Convergence|absolute convergence]].
5. Why series matter: [[Power Series|power series]] are "infinite polynomials" that a computer can evaluate.
6. **Convergence tests** (*konvergenčni kriteriji*): the [[Ratio Test|ratio test]], the [[Root Test|root test]] and the [[Leibniz Test|Leibniz test]]; differentiating and integrating a power series term by term.

## Notes

### Motivation

1. **Achilles and the tortoise paradox** (*paradoks o Ahilu in želvi*): Achilles can never catch the tortoise (*Ahil nikoli ne more ujeti*).
2. An infinite sum can have a finite value:
   $$0.3 + 0.03 + 0.003 + 0.0003 + \dots = \frac{1}{3}$$
3. A unit square: shade half of it, then half of what is left, and so on.

![[Calculus 5 shaded square.svg]]

| shaded (*pobarvano*) | remainder (*ostanek*) |
| --- | --- |
| $\frac{1}{2} + \frac{1}{4} + \frac{1}{8} + \frac{1}{16} + \dots$ | $\frac{1}{2}$, then halved again and again $/2/2/2\ldots$ |
| $= 1$ | $\to 0$ (goes to $0$ — *gre proti 0*) |

### Definition of a series

**Definition.** A **series** (*vrsta*) is a symbolic sum of (real) numbers (*simbolična vsota števil*):

$$a_1 + a_2 + a_3 + \dots = \sum_{n=1}^{\infty} a_n, \qquad a_n \in \mathbb{R}\ \ \forall n$$

The **$m$-th partial sum** (*$m$-ta delna vsota*):

$$S_m = a_1 + a_2 + \dots + a_m = \sum_{n=1}^{m} a_n$$

The series **converges** (*konvergira*) if the sequence of partial sums $(S_m)_m$ converges. In that case the **sum of the series** (*vsota vrste*) is

$$\sum_{n=1}^{\infty} a_n = \lim_{n \to \infty} S_n$$

So limits are the tool for working with infinity (*limite so orodje, ko se igramo z neskončnostjo*).

The series **diverges** (*divergira*) if it does not converge.

> [!theorem] Claim (*trditev*)
> If $\sum\limits_{n=1}^{\infty} a_n$ converges, then $\lim\limits_{n \to \infty} a_n = 0$.
> The converse is not true (*obrat ni res*).

Proof: write it out (*dokaz — napiši*).

### Harmonic series (*harmonična vrsta*)

The typical example (*tipičen primer*) of why the converse fails: the terms go to $0$, but the series **diverges**. Group the terms:

$$
\begin{aligned}
\sum_{n=1}^{\infty} \frac{1}{n} = \ & 1 && \geq \tfrac{1}{2} \\
+\ & \tfrac{1}{2} && \geq \tfrac{1}{2} \\
+\ & \tfrac{1}{3} + \tfrac{1}{4} && \geq \tfrac{1}{2} \\
+\ & \tfrac{1}{5} + \tfrac{1}{6} + \tfrac{1}{7} + \tfrac{1}{8} && \geq \tfrac{1}{2} \\
+\ & \tfrac{1}{9} + \dots + \tfrac{1}{16} && \geq \tfrac{1}{2} \\
+\ & \dots
\end{aligned}
$$

Infinitely many groups each add at least $\frac{1}{2}$, so the sum goes to $+\infty$ and the series diverges (*torej vrsta divergira*):

$$\sum_{n=1}^{2^k} \frac{1}{n} \geq \frac{k}{2} \xrightarrow{k \to \infty} \infty$$

so the partial sums do not converge (*ne konvergira*).

### Geometric series (*geometrijska vrsta*)

$$\sum_{n=1}^{\infty} q^n$$

**Example: a repeating decimal.**

$$0.\overline{123} = x = 123 \cdot \sum_{n=1}^{\infty}\left(\frac{1}{1000}\right)^n$$

$$1000x = 123.\overline{123} \quad\Longrightarrow\quad 999x = 123 \quad\Longrightarrow\quad x = \frac{123}{999}$$

**Partial sums.** Multiply by $q$ and subtract:

$$
\begin{aligned}
S_m &= q + q^2 + \dots + q^m \qquad / \cdot q \\
q S_m &= q^2 + q^3 + \dots + q^{m+1} \\
S_m - q S_m &= q - q^{m+1} \\
S_m (1 - q) &= q - q^{m+1}
\end{aligned}
$$

and for $q \neq 1$ (*za $q \neq 1$*):

$$S_m = \frac{q - q^{m+1}}{1 - q}$$

**Sum.** Letting $m \to \infty$:

$$\sum_{n=1}^{\infty} q^n = \lim_{m \to \infty} S_m = \begin{cases} \dfrac{q}{1 - q}, & |q| < 1 \\ \text{diverges (DIV)}, & |q| > 1 \\ \text{diverges (DIV)}, & q = 1 \\ \text{diverges (DIV)}, & q = -1 \end{cases}$$

**Example** (*primer*):

$$\sum_{n=1}^{\infty} \frac{2^{2n+1}}{5^n} = 2\sum_{n=1}^{\infty}\left(\frac{4}{5}\right)^n = 2 \cdot \frac{\frac{4}{5}}{1 - \frac{4}{5}} = \dots$$

But

$$\sum_{n=1}^{\infty} \frac{2^{3n+1}}{5^n} = 2\sum_{n=1}^{\infty}\left(\frac{8}{5}\right)^n = \infty$$

Here $q = \frac{8}{5} > 1$, so the formula $2 \cdot \frac{8/5}{1 - 8/5}$ does not work (*to ne funkcionira*) — it was crossed out in the notebook.

### Rules for computing with series (*pravila za računanje vrst*), $c \in \mathbb{R}$

Let $\sum\limits_{n=1}^{\infty} a_n$ and $\sum\limits_{n=1}^{\infty} b_n$ be convergent series. Then these are convergent too (*kdaj sta konvergentni tudi*):

1. $$\sum_{n=1}^{\infty}(a_n + b_n) = \sum_{n=1}^{\infty} a_n + \sum_{n=1}^{\infty} b_n$$
   The converse does not hold (*obrat ne velja*).
2. $$\sum_{n=1}^{\infty}(c \cdot a_n) = c\sum_{n=1}^{\infty} a_n$$

Examples:

- $\sum\limits_{n=1}^{\infty}\left(\frac{1}{2^n} + \frac{2}{5^n}\right)$ — we know how to do this (*znamo*): two geometric series.
- A series that starts later, with $j = n - 4$:
  $$\sum_{n=5}^{\infty} q^n = q^4\sum_{n=5}^{\infty} q^{n-4} = q^4\sum_{j=1}^{\infty} q^j = \dots$$

#### Example: does it converge? (*ali konvergira?*)

$$(*)\qquad \sum_{n=1}^{\infty}\left(\frac{1}{n} - \frac{1}{n+1}\right) = \sum_{n=1}^{\infty}\frac{n + 1 - n}{n(n+1)} = \sum_{n=1}^{\infty}\frac{1}{n^2 + n} \leq \sum_{n=1}^{\infty}\frac{1}{n^2} \quad \text{(converges)}$$

so $(*)$ converges too (*torej tudi $*$ konvergira*). If the larger series converges, the smaller one converges too (*če večja vrsta konvergira, potem tudi manjša vrsta konvergira*).

### Dominance of series (*dominiranje vrst*)

Let $\sum\limits_{n=1}^{\infty} a_n$ and $\sum\limits_{n=1}^{\infty} b_n$ be series with non-negative terms (*vrsti z nenegativnimi členi*). Let the first **dominate** the second (*naj prva dominira drugo*): $a_n \geq b_n$ for all $n$. Then:

1. If $\sum\limits_{n=1}^{\infty} a_n$ converges, then $\sum\limits_{n=1}^{\infty} b_n$ converges too.
2. If $\sum\limits_{n=1}^{\infty} b_n$ diverges, then $\sum\limits_{n=1}^{\infty} a_n$ diverges too (check — *preveri*).

### Absolute convergence (*absolutna konvergenca*)

**Definition.** The series $\sum\limits_{n=1}^{\infty} a_n$ **converges absolutely** (*absolutno konvergira*) if $\sum\limits_{n=1}^{\infty} |a_n|$ converges.

> [!theorem] Claim (*trditev*)
> Every absolutely convergent series converges (*vsaka absolutno konvergentna vrsta konvergira*).

Examples (*primeri*):

1. $\sum\limits_{n=1}^{\infty}\left(-\frac{1}{2}\right)^n$ converges absolutely.
2. $\sum\limits_{n=1}^{\infty}\frac{(-1)^n}{n}$ does not converge absolutely. With it we can express any number, even $\pi$ (*s tem lahko izrazimo katerokoli število, tudi π*).

### Why does this matter? (*Zakaj je to važno?*)

- Computers and people know how to add and multiply (*znajo seštevati, množiti*), so we want to work with polynomials (*hočemo delati s polinomi*).
- If we want to compute something on a computer, we have to write it as a polynomial (*zapisati v polinomu*).
- An "infinite polynomial" (*neskončen polinom*) is a **power series** (*potenčna vrsta*):
  $$a_0 + a_1 x + a_2 x^2 + \dots = \sum_{n=0}^{\infty} a_n x^n$$
- This is like the jump from rational to irrational numbers (*preskok iz racionalnih na iracionalna*). A decimal expansion is the sum of a series (*decimalni zapis je vsota vrste*).
- **Goal** (*cilj*): write functions in the form of a power series.
- Bottom line: approximating with polynomials is like the decimal expansion of numbers.
- In the past: logarithm tables (*logaritemske tablice*); today: power series.

### Convergence tests (*konvergenčni kriteriji*)

Let $\sum\limits_{n=1}^{\infty} a_n$ be a series with $a_n \neq 0$ for all $n$.

#### 1. Ratio test (*kvocientni kriterij*)

$$D_n := \left|\frac{a_{n+1}}{a_n}\right|$$

Let $\lim\limits_{n \to \infty} D_n = D$ exist. Then:

$$(*)\qquad \begin{aligned} D < 1 &\implies \text{the series converges (absolutely)} \\ D > 1 &\implies \text{the series diverges} \\ D = 1 &\implies \text{we don't know (?)} \end{aligned}$$

The proof is by comparison with the geometric series (*dokaz s primerjavo z geometrijsko vrsto*).

**Example:** for which $x$ does the series converge (*za katere $x$ konvergira*)?

$$\sum_{n=0}^{\infty} n x^n, \qquad D_n = \left|\frac{(n+1)x^{n+1}}{n x^n}\right| = \left|\underbrace{\frac{n+1}{n}}_{\to\,1}\, x\right| \xrightarrow{n \to \infty} |x|$$

- $x = 0$: converges ✓
- $|x| < 1$: converges (absolutely)
- $|x| \geq 1$: diverges
- $x = 1$ diverges, $x = -1$ diverges: $|x| = 1$ has to be checked separately (*preverimo posebej*).

#### 2. Root test (*korenski kriterij*)

$$C_n := \sqrt[n]{|a_n|}$$

(A side remark on notation next to it: $:=$ means a definition (*Def*), $==$ means comparison (*primerjanje*), and $a = 5$ an assignment. The test compares with the geometric series $\sum q^n$.)

Let $\lim\limits_{n \to \infty} C_n = C$ exist. Then:

- $C < 1 \implies$ the series converges absolutely
- $C > 1 \implies$ the series diverges
- $C = 1 \implies$ ? (edge cases that have to be checked separately — *robni primeri, ki jih je treba posebej notri vržt*)

**Example:** for which $x$ does

$$\sum_{n=1}^{\infty}\frac{x^n}{n^n}$$

converge? $C_n = \sqrt[n]{\dfrac{x^n}{n^n}} = \dfrac{x}{n} \xrightarrow{n \to \infty} 0 = C$.

$C = 0 < 1$, so the series converges absolutely for every $x$ (*za vsak $x$*).

#### Power series can be differentiated and integrated term by term ("time capsule")

> [!theorem] Theorem (*izrek*)
> On the regions $(*)$ (from before — *od prej*, i.e. where the ratio test gives convergence) the sum of the power series $\sum\limits_{n=0}^{\infty} b_n x^n$ is a continuously differentiable function $f(x)$ (*zvezno odvedljiva funkcija*), and
> $$f'(x) = \sum_{n=0}^{\infty} b_n \cdot (x^n)'$$
> $$\int f(x)\,dx = \sum_{n=0}^{\infty} b_n \int x^n\,dx$$

The [[Derivative|derivative]] and the [[Integral|integral]] can be pulled into the series (*odvod, integral se lahko vrže v vrsto*). In practice this is extremely useful (*v praksi ta zadeva ful dobra*).

**Question** (*vprašanje*):

$$1 + x + \frac{x^2}{2} + \frac{x^3}{3!} + \frac{x^4}{4!} + \dots = \sum_{n=0}^{\infty}\frac{x^n}{n!} = e^x$$

Homework (*doma*): check the convergence with both tests and say which one is more efficient (*povej, kateri je bolj učinkovit*).

Derivative (*odvod*), term by term:

$$0 + 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \dots$$

the same series (*isto*) — so $(e^x)' = e^x$.

#### 3. Leibniz test (*Leibnizov kriterij*)

Let $(a_n)_n$ be a decreasing sequence (*padajoče zaporedje*) with $\lim\limits_{n \to \infty} a_n = 0$. Then

$$\sum_{n=1}^{\infty}(-1)^n a_n \quad \text{converges.}$$

**Example:** $\sum\limits_{n=1}^{\infty}\dfrac{(-1)^n}{n}$ converges (but not absolutely — *a ne absolutno*).

## Questions

- [ ] How does the proof go that the terms of a convergent series go to $0$? (*dokaz — napiši*)
- [ ] Why is the converse of the rule for $\sum(a_n + b_n)$ false? (Example where $\sum(a_n + b_n)$ converges but $\sum a_n$ and $\sum b_n$ do not.)
- [ ] How can $\sum\frac{(-1)^n}{n}$ be used to express any number, even $\pi$?
- [ ] Homework: check the convergence of $\sum\frac{x^n}{n!}$ with the ratio test and the root test. Which one is more efficient?
- [ ] Why does the ratio test say nothing when $D = 1$? (An example of a convergent and a divergent series with $D = 1$.)

## Connections

- Course: [[Calculus]]
- Previous lecture: [[2026-10-28 - Limits of Sequences - 4]] — limits of sequences, $\lim(1 + \frac{1}{n})^n = e$, comparison of limits; the sum of a series is the limit of its partial sums
- [[2026-10-21 - Spectral Decomposition and Sequences - 3]] — sequences
- [[Derivative]], [[Integral]] — term-by-term differentiation and integration of power series
- Exercises: [[Sources/calculus/photoNotes/vaje/vaje 5.pdf|vaje 5]]

## Sources

- Handwritten notes: [[Sources/calculus/photoNotes/lectures/lecture 5.pdf|lecture 5]]
- J. Globevnik, M. Brojan, *Analiza I* (2012), ch. 6 *Vrste*: definition of a series and $\lim a_n = 0$ (Def. 94, Posledica 32) [[Sources/calculus/skripta.pdf#page=227|skripta p. 217]]; geometric series, rules (Izrek 73, 74) [[Sources/calculus/skripta.pdf#page=229|p. 219]]; harmonic series [[Sources/calculus/skripta.pdf#page=230|p. 220]]; comparison (Izrek 75) and ratio test (Izrek 76) [[Sources/calculus/skripta.pdf#page=232|p. 222]]; root test (Izrek 77) [[Sources/calculus/skripta.pdf#page=234|p. 224]]; absolute convergence (Def. 96, Izrek 80, 81) [[Sources/calculus/skripta.pdf#page=239|p. 229]]; Riemann's rearrangement theorem (Izrek 83) [[Sources/calculus/skripta.pdf#page=242|p. 232]]; Leibniz test (Izrek 84) [[Sources/calculus/skripta.pdf#page=243|p. 233]]; term-by-term differentiation and integration of power series (Izrek 96) [[Sources/calculus/skripta.pdf#page=256|p. 246]]
