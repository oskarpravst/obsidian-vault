---
type: "[[Lectures]]"
course: "[[Calculus]]"
date: 2026-10-28
week: "4"
---

# 2026-10-28 - Limits of Sequences

## Main Idea

Continuing with [[Sequence|sequences]]:

1. Working with the $\varepsilon$–$N$ definition of the [[Limit of a Sequence|limit]] on examples (checking that a number is or is not the limit).
2. Sequences that grow or fall **over every bound** (*narašča/pada preko vsake meje*), boundedness of convergent sequences and **accumulation points** (*stekališča*).
3. **Rules for computing limits** (*pravila za računanje limit*), arithmetic with $\infty$ and the indeterminate forms; the number $e$ and continuous compounding.
4. **Convergence theorems**: comparison of limits and the **monotone convergence theorem**, used on a recursive sequence (with [[Mathematical Induction|induction]]).
5. How $2^\pi$ is defined with limits.
6. **Bachmann–Landau notation** ([[Big O Notation|$O$-notation]]) and the classes P and NP.

## Notes

### Limit — examples

$$a = \lim_{n \to \infty} a_n \iff \forall \varepsilon > 0\ \ \exists N \in \mathbb{N}:\ |a - a_n| < \varepsilon, \quad \forall n \geq N$$

- With $\varepsilon \geq 0$ instead of $\varepsilon > 0$ this would be a different concept (*če tuki ≥, je drugačen koncept*).
- Whether we write $n \geq N$ or $n > N$ does not matter (*vseeno, če je enakost*).

#### Example: $\frac{1}{n^2} \xrightarrow{n \to \infty} 0$

For a concrete $\varepsilon_1 = 0.001$:

$$\left|\frac{1}{n^2} - 0\right| < 0.001 \iff \frac{1}{n^2} < 0.001 \iff 1000 < n^2 \iff n > \sqrt{1000}$$

For a general $\varepsilon > 0$ (*splošen ε*):

$$\left|\frac{1}{n^2} - 0\right| < \varepsilon \iff \frac{1}{\varepsilon} < n^2 \iff \sqrt{\frac{1}{\varepsilon}} < n \quad ✓$$

So the limit really is $0$ (*lim je res 0*).

#### Is the limit $1$? (*Ali je lim = 1?*)

$$\left|\frac{1}{n^2} - 1\right| < \varepsilon \iff 1 - \frac{1}{n^2} < \varepsilon \iff -\frac{1}{n^2} < \varepsilon - 1 \ \big/ \cdot(-1) \iff \frac{1}{n^2} > 1 - \varepsilon$$

$$n^2 < \frac{1}{1 - \varepsilon} \iff n < \sqrt{\frac{1}{1 - \varepsilon}} \quad //$$

The inequality holds only for small $n$, not for all $n \geq N$, so $1$ is not the limit (*1 ni limita*).

#### More examples

- $0.\underbrace{33\ldots3}_{n} \xrightarrow{n \to \infty} \dfrac{1}{3}$
- $(-1)^n$ is **divergent** (*divergentno*): it has no limit (*nima limite*).
- $2^n \to \infty$
- $2^{-n} \to 0$

### Growing and falling over every bound

**Definition.** A sequence $(a_n)_n$

1. **grows over every bound** (*narašča preko vsake meje*), written $\lim\limits_{n \to \infty} a_n = \infty$, if
   $$\forall M \in \mathbb{R}\ \ \exists N \in \mathbb{N}:\ a_n \geq M, \quad \forall n \geq N$$
2. **falls over every bound** (*pada preko vsake meje*), written $\lim\limits_{n \to \infty} a_n = -\infty$, if
   $$\forall m \in \mathbb{R}\ \ \exists N \in \mathbb{N}:\ a_n \leq m, \quad \forall n \geq N$$

The notation $\lim a_n = \infty$ is **not convergence** (*ni konvergenca*): the limit is not a real number.

![[Calculus 4 growing over every bound.svg]]

Example from the notebook next to the sketch: $1, 2, 1, 3, 1, 4, \dots$

> [!theorem] Claim (*trditev*)
> Every convergent sequence is bounded (*vsako konvergentno zaporedje je omejeno*).

**Proof** (*dokaz*). Take $\varepsilon > 0$ and $a = \lim a_n$. There is an $N$ such that the bounded interval $(a - \varepsilon, a + \varepsilon)$ contains $a_N, a_{N+1}, \dots$

![[Calculus 4 epsilon interval.svg]]

The set of terms is

$$\{a_n\}_n \subseteq (a - \varepsilon, a + \varepsilon) \cup \{a_1, a_2, \dots, a_{N-1}\},$$

a bounded interval together with finitely many numbers, so it is bounded (*omejeno*). $\blacksquare$

### Accumulation points (*stekališča*)

**Definition.** $a \in \mathbb{R}$ is an **accumulation point** (*stekališče*) of the sequence $(a_n)_n$ if for every $\varepsilon > 0$ the interval

$$(a - \varepsilon,\ a + \varepsilon)$$

contains infinitely many terms of the sequence (*vsebuje neskončno členov zaporedja*).

Example: $(-1)^n$ has 2 accumulation points: $1$ and $-1$.

> [!theorem] Claims (*trditev*)
> - Every limit is an accumulation point (*vsaka limita je stekališče*).
> - Every bounded sequence has an accumulation point (in $\mathbb{R}$) (*vsako omejeno zaporedje ima stekališče*).

### Examples (of (non-)convergence)

$$\lim_{n \to \infty} n^a,\ a \in \mathbb{R} \;=\; \begin{cases} \infty, & a > 0 \\ 1, & a = 0 \\ 0, & a < 0 \end{cases}$$

$$\lim_{n \to \infty} a^n \;=\; \begin{cases} \infty, & a > 1 \\ 1, & a = 1 \\ 0, & a \in (-1, 1) \\ \text{does not exist}, & a \leq -1 \end{cases}$$

$$\lim_{n \to \infty} \sqrt[n]{n} = 1, \qquad \lim_{n \to \infty}\left(1 + \frac{1}{n}\right)^n = e, \qquad \lim_{n \to \infty}\left(1 - \frac{1}{n}\right)^n = \ ?\ \text{(computed below)}$$

### Rules for computing limits (*pravila za računanje limit*)

Let $\lim\limits_{n \to \infty} a_n = a$ and $\lim\limits_{n \to \infty} b_n = b$. Then

$$\lim_{n \to \infty}(a_n \pm b_n) = a \pm b, \qquad \lim_{n \to \infty}(a_n \cdot b_n) = a \cdot b$$

$$\lim_{n \to \infty}\frac{a_n}{b_n} = \frac{a}{b}, \quad \text{if } b \neq 0 \text{ and } b_n \neq 0\ \ \forall n$$

(The notebook writes the first rule with a dot over $\pm$, i.e. for $+$, $-$ and $\cdot$.)

**In the sense of growing over every bound** (*v smislu naraščanja preko vseh mej*), for $a \in \mathbb{R}$, $b > 0$:

$$\infty + a = \infty, \qquad \infty + \infty = \infty, \qquad \infty \cdot b = \infty, \qquad \infty \cdot (-b) = -\infty, \qquad \frac{1}{\infty} = 0, \qquad \infty^\infty = \infty$$

**Problematic situations** (*problematične situacije*), the indeterminate forms:

$$\infty - \infty, \qquad \frac{\infty}{\infty}, \qquad 1^\infty, \qquad \frac{0}{0}$$

#### Example: $\frac{\infty}{\infty}$

Numerator and denominator both go to $\infty$, so divide both by $n^2$:

$$\lim_{n \to \infty}\frac{2n^2 - 5}{n^2 + n - 6} = \lim_{n \to \infty}\frac{2 - \frac{5}{n^2}}{1 + \frac{1}{n} - \frac{6}{n^2}} = \frac{2 - 0}{1 + 0 - 0} = 2$$

#### Example: $1^\infty$ and the number $e$

$$\lim_{n \to \infty}\left(1 + \frac{1}{n}\right)^n = \lim_{n \to \infty}\left(\frac{n + 1}{n}\right)^n = e$$

$$
\begin{aligned}
\lim_{n \to \infty}\left(1 - \frac{1}{n}\right)^n &= \lim_{n \to \infty}\left(\frac{n - 1}{n}\right)^n = \lim_{n \to \infty}\left(\left(\frac{n}{n - 1}\right)^{-1}\right)^n \\
&= \lim_{n \to \infty}\Bigg(\underbrace{\left(1 + \frac{1}{n - 1}\right)^{n - 1}}_{\to\, e}\Bigg)^{\overbrace{\scriptstyle -\frac{n}{n-1}}^{\to\, -1}} = e^{-1}
\end{aligned}
$$

using $1 + \frac{1}{n-1} = \frac{n-1}{n-1} + \frac{1}{n-1} = \frac{n}{n-1}$.

Shifting the index does not change the limit: if $\lim\limits_{n \to \infty} a_n = a$, then also $\lim\limits_{n + 5 \to \infty} a_n = a$ (this is why $(1 + \frac{1}{n-1})^{n-1} \to e$).

#### Example: interest (*obresti*)

Capital $K$ with $4\,\%$ yearly interest (*4 % letno obračuna*):

| compounding | after one year |
| --- | --- |
| yearly (*letno*) | $K(1 + 0.04)$ |
| 4× a year (*4× letno*) | $K\left(1 + \frac{0.04}{4}\right)^4$ |
| monthly (*mesečno*) | $K\left(1 + \frac{0.04}{12}\right)^{12}$ |
| continuous (*stalno obračunavanje*) | $K \cdot \lim\limits_{n \to \infty}\left(1 + \frac{0.04}{n}\right)^n = K \cdot e^{0.04}$ |

From top to bottom the amount grows, from the smallest (*najmanj*) to the largest (*največ*).

### Convergence theorems (*izrek o konvergenci*)

> [!theorem] 1. Comparison
> If $a_n \leq b_n \leq c_n$ for all $n$, then
> $$\lim_{n \to \infty} a_n \leq \lim_{n \to \infty} b_n \leq \lim_{n \to \infty} c_n$$

**Example.** The sine is bounded (*sinus je omejen*), so

$$-\frac{1}{n} \leq \frac{\sin\left(e^n + \tan(n^2 + 16) + n^{38}\right)}{n} \leq \frac{1}{n}$$

Since $\lim\limits_{n \to \infty} \frac{1}{n} = 0$ (and $-\frac{1}{n} \to 0$), this sequence also goes to $0$ (*torej ta tudi*).

> [!theorem] 2. Monotone convergence (increasing)
> An increasing sequence (*naraščajoče zaporedje*) is convergent **if and only if** (*natanko tedaj, ko*) it is bounded above (*navzgor omejeno*). In that case
> $$\lim_{n \to \infty} a_n = \sup a_n$$

If an increasing sequence is not bounded above, it grows over every bound (it cannot have a maximum — *maksimuma ne more meti*).

> [!theorem] 3. Monotone convergence (decreasing)
> A decreasing sequence (*padajoče zaporedje*) is convergent if and only if it is … (homework — *doma*)

#### Example: a recursive sequence

$$a_1 = 0, \qquad a_n = \frac{a_{n-1} + 6}{2}$$

Investigate the convergence of $a_n$ (*razišči konvergenco zaporedja*). The first terms:

$$a_2 = 3, \qquad a_3 = \frac{9}{2}, \qquad a_4 = \frac{21}{4}, \qquad \dots$$

We look at (*gledamo*): **monotonicity** (*monotonost*), **boundedness** (*omejenost*) and the **(potential) limit** (*limita, potencialna*).

**Potential limit.** Let $A = \lim\limits_{n \to \infty} a_n$. Taking the limit of both sides of the recursion (and $\lim a_{n-1} = A$ as well):

$$\lim_{n \to \infty} a_n = \frac{\lim\limits_{n \to \infty} a_{n-1} + 6}{2} \quad\Longrightarrow\quad A = \frac{A + 6}{2} \quad\Longrightarrow\quad A = 6$$

This is only valid **if the limit exists** (*če limita obstaja*) — the calculation alone can lead us astray (*lahko se prav zakadi*).

**Boundedness.** We prove that $a_n$ is bounded above by $6$: $a_n \leq 6$ for all $n \in \mathbb{N}$ (equivalently $-a_n \geq -6$, used below as $(*)$). By [[Mathematical Induction|induction]] (*indukcija*):

- I. Base: $a_1 = 0 \leq 6$ ✓
- II. Step: assume $a_n \leq 6$. We prove (*dokazujemo*)
  $$a_{n+1} = \frac{a_n + 6}{2} \leq \frac{6 + 6}{2} = 6 \quad ✓$$
  (the inequality is where the induction hypothesis is used — *dokaz vmes*).

**Monotonicity.** We prove that $a_n$ is increasing, i.e. $a_n - a_{n-1} \geq 0$:

$$a_n - a_{n-1} = \frac{a_{n-1} + 6}{2} - \frac{2a_{n-1}}{2} = \frac{6 - a_{n-1}}{2} \overset{(*)}{\geq} \frac{6 - 6}{2} = 0$$

**Conclusion.** The sequence is increasing and bounded above, so by theorem 2 it is convergent. Its limit (the only possible one — *edina možna*) is $6$.

### How do we define $2^\pi$? (*Kako definiramo 2^π?*)

Step by step, for $r, q \in \mathbb{N}$:

- $2^r = \underbrace{2 \cdot 2 \cdots 2}_{r}$
- $2^{\frac{1}{q}} = a > 0$ such that $a^q = 2$
- $2^{\frac{r}{q}} = \underbrace{2^{\frac{1}{q}} \cdot 2^{\frac{1}{q}} \cdots 2^{\frac{1}{q}}}_{r}$
- Choose a sequence $b_n \in \mathbb{Q}$ for all $n$ with $\lim\limits_{n \to \infty} b_n = \pi$, and define
  $$2^\pi = \lim_{n \to \infty} 2^{b_n}$$

In $\mathbb{C}$ (*v ℂ*): $\sqrt[4]{7} = 7^{\frac{1}{4}}$ has 4 solutions (*rešitve*), while $2^{\frac{1}{\pi}}$ has infinitely many ($\infty$ *rešitev*).

### Bachmann–Landau notation (*Bachmann-Landauova notacija*)

This is the [[Big O Notation|$O$-notation]]. Let $f, g: \mathbb{N} \to \mathbb{N}$.

- **Big O:** $f(n) = O(g(n))$ if $\dfrac{f(n)}{g(n)}$ is bounded (*omejeno*).
  $f$ is **asymptotically bounded** by $g$ (*f je asimptotično omejena z g*).
- **Small o:** $f(n) = o(g(n))$ if
  $$\lim_{n \to \infty}\frac{f(n)}{g(n)} = 0$$
  $g$ **asymptotically dominates** $f$ (*g asimptotično dominira f*).

**Examples** (*primeri*):

| problem | complexity |
| --- | --- |
| find the largest element in a list of length $n$ (*poišči največji člen v seznamu dolžine n*) | $O(n)$ |
| find a given element (*določeni*) in a sorted list of length $n$ | $O(\ln n)$ |
| sort a list (*uredi seznam*), brute force: $0 + 1 + 2 + \dots + (n-1) = \frac{(n-1)(n-2)}{2}$ | $O(n^2)$ |
| sort a list, [[Merge Sort\|merge sort]] | $O(n \log n)$ |

### P and NP

- **P** — problems solvable in polynomial time (*problemi rešljivi v polinomskem času*):
  $$\mathrm{P} = \bigcup_{q \in \mathbb{N}} O(n^q)$$
- **NP** — problems whose solution can be verified in polynomial time (*problemi, katerih rešitev se lahko verificira v polinomskem času*) (guesses — *poiskusi*).

The biggest open question (*največje odprto vprašanje*): does [[P versus NP|$\mathrm{P} = \mathrm{NP}$]] hold?

## Questions

- [ ] What does the sketch next to the definition of "grows over every bound" show, and how does the example $1, 2, 1, 3, 1, 4, \dots$ relate to it? (It is unbounded, but its terms keep returning to $1$, so is it really $\lim a_n = \infty$?)
- [ ] How does theorem 3 end: a decreasing sequence is convergent if and only if it is …? (homework)
- [ ] Why does $2^{\frac{1}{\pi}}$ have infinitely many values in $\mathbb{C}$, while $\sqrt[4]{7}$ has only 4?

## Connections

- Course: [[Calculus]]
- Previous lecture: [[2026-10-21 - Spectral Decomposition and Sequences - 3]] — definitions of sequence, bounded and monotone sequences, $\varepsilon$–$N$ limit
- [[2026-10-11 - Numbers - 1]] — [[Supremum and Infimum|supremum]] (limit of an increasing bounded sequence)
- [[Mathematical Induction]] — proving the bound $a_n \leq 6$ (also used in Discrete structures)
- [[Big O Notation]], [[P versus NP]] — time complexity, also relevant for Programming 1

## Sources

- Handwritten notes: [[Sources/calculus/photoNotes/lectures/lecture 4.pdf|lecture 4]]
- J. Globevnik, M. Brojan, *Analiza I* (2012): accumulation points (Def. 24, Izrek 6) [[Sources/calculus/skripta.pdf#page=45|skripta p. 35]]; convergent sequences are bounded (Trditev 13) [[Sources/calculus/skripta.pdf#page=51|p. 41]]; monotone sequences (Izrek 8, 9) [[Sources/calculus/skripta.pdf#page=52|p. 42]]; rules for limits (Izrek 12, 13) [[Sources/calculus/skripta.pdf#page=54|p. 44]]; limit $+\infty$ (Def. 28) [[Sources/calculus/skripta.pdf#page=57|p. 47]]
- [Big O notation — Wikipedia](https://en.wikipedia.org/wiki/Big_O_notation)
