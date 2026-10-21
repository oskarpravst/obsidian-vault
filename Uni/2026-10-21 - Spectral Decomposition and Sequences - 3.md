---
type: "[[Lectures]]"
course: "[[Calculus]]"
date: 2026-10-21
week: "3"
---

# 2026-10-21 - Spectral Decomposition and Sequences

## Main Idea

Two parts:

1. **Why complex numbers are used: spectral decomposition** (*spektralna dekompozicija*). A measured signal is a sum of individual signals. Using [[Euler's Formula|Euler's formula]] we build "pure frequency" vectors $C_k$ from complex exponentials. Every signal can be written uniquely as a combination of them, and the coefficients come from a [[Dot Product|scalar product]]. This is the [[Discrete Fourier Transform|discrete Fourier transform]] (DFT).
2. **[[Sequence|Sequences]]** (*zaporedja*): definition and ways to define one (explicitly, recursively), arithmetic and geometric sequences, the graphical display of a recursive sequence, properties (bounded, monotone), and the definition of the [[Limit of a Sequence|limit]].

## Notes

### OMA 3 — Euler's formula and the scalar product

$$e^{it} = \cos t + i\sin t$$

**Scalar product** (*skalarni produkt*):

$$(v_1, v_2, \dots, v_n) \cdot (w_1, w_2, \dots, w_n) = v_1 w_1 + v_2 w_2 + \dots + v_n w_n$$

#### Exercise (*vaja*)

$$a = \left(e^{2i\pi\frac{0}{4}},\ e^{2i\pi\frac{1}{4}},\ e^{2i\pi\frac{2}{4}},\ e^{2i\pi\frac{3}{4}}\right), \qquad b = \left(e^{2i\pi\frac{0}{4}},\ e^{2i\pi\frac{2}{4}},\ e^{2i\pi\frac{4}{4}},\ e^{2i\pi\frac{6}{4}}\right)$$

![[Calculus 3 vectors a and b.svg]]

So $a = (1, i, -1, -i)$ and $b = (1, -1, 1, -1)$.

$$a \cdot \bar{a} = 1^2 + 1^2 + 1^2 + 1^2 = 4 = b \cdot \bar{b}$$

$$a \cdot \bar{b} = e^{-i2\pi\cdot\frac{0}{4}} + e^{-i2\pi\frac{1}{4}} + e^{-i2\pi\frac{2}{4}} + e^{-i2\pi\frac{3}{4}} = 0$$

### Why are complex numbers used? Spectral decomposition

*Zakaj se uporabljajo kompleksna števila?* → spectral decomposition (*spektralna dekompozicija*).

We have a measurement (*meritev*) that is a **sum of signals**. We want to split it into the individual signals.

Example: **noise cancelling**:

$$\cos t + \cos(t + \pi) = 0$$

![[Calculus 3 noise cancelling.svg]]

**Resolution** (*resolucija*): $N = 2^m$, $m \in \mathbb{N} \setminus \{0\}$.

#### The frequency vectors $C_k$

$$C_k = \left(e^{i2\pi\frac{k\cdot 0}{N}},\ e^{i2\pi\frac{k\cdot 1}{N}},\ e^{i2\pi\frac{k\cdot 2}{N}},\ \dots,\ e^{i2\pi\frac{k(N-1)}{N}}\right) = \left(e^{i2\pi\frac{k\cdot n}{N}}\right)_{n=0}^{N-1}$$

- $k$ is the **frequency** (*frekvenca*).
- $C_k$ is a sequence (*zaporedje*) of $N$ numbers.

A **signal** is

$$X = \sum_{k=0}^{N-1} y_k \cdot C_k, \qquad y_k = r_k \cdot e^{i\varphi_k} \in \mathbb{C}$$

- $r_k$ is the **strength** (*jakost*),
- $\varphi_k$ is the **shift** (*zamik*).

> [!theorem] Theorem (*izrek*)
> Every sequence $X$ has such a representation, and it is **unique** (*enoličen zapis*).

#### Spectral decomposition of cosine and sine

$$\cos t = \operatorname{Re}(e^{it}) = \frac{e^{it} + e^{-it}}{2}$$

$$\left(\cos\frac{2\pi k n}{N}\right)_{n=0}^{N-1} = \frac{1}{2} C_k + \frac{1}{2} C_{N-k}$$

This is the spectral decomposition of the cosine (*spektralna dekompozicija kosinusa*). Here

$$C_k = \overline{C_{N-k}}$$

$$\sin t = \operatorname{Im}(e^{it}) = \frac{e^{it} - e^{-it}}{2i}$$

$$\left(\sin\frac{2\pi k n}{N}\right)_{n=0}^{N-1} = -\frac{i}{2} C_k + \frac{i}{2} C_{N-k}$$

This is the spectral decomposition of the sine (*spektralna dekompozicija sinusa*).

#### Example: $\cos t + \sin t$

> [!theorem] Theorem (*izrek*)
> For real signals (*za realne signale*) the coefficients satisfy $y_k = \overline{y_{N-k}}$.
>
> (The identity $C_k = \overline{C_{N-k}}$ for the vectors holds always, see above.)

$$
\begin{aligned}
\left(\cos\frac{2\pi k n}{N} + \sin\frac{2\pi k n}{N}\right)_{n=0}^{N-1}
&= \left(\frac{1}{2} - \frac{i}{2}\right) C_k + \left(\frac{1}{2} + \frac{i}{2}\right) C_{N-k} \\
&= \frac{1}{\sqrt{2}} e^{-i\frac{\pi}{4}} C_k + \frac{1}{\sqrt{2}} e^{i\frac{\pi}{4}} C_{N-k} \\
&= \frac{2}{\sqrt{2}} \operatorname{Re}\left(e^{-i\frac{\pi}{4}} \cdot C_k\right) \\
&= \sqrt{2} \cdot \left(\cos\left(\frac{2\pi k n}{N} - \frac{\pi}{4}\right)\right)_{n=0}^{N-1}
\end{aligned}
$$

So

$$\cos t + \sin t = \sqrt{2}\,\cos\left(t - \frac{\pi}{4}\right)$$

#### How do we get the coefficients? (DFT)

**Question** (*vprašanje*): how do we get $(y_0, y_1, \dots, y_{N-1})$ from $(x_0, x_1, \dots, x_{N-1})$?

**Lemma** (*lema*, claim — *trditev*):

$$C_p \cdot \overline{C_q} = \begin{cases} 0, & p \neq q \\ N, & p = q \end{cases}$$

Multiply $X = \sum_{k=0}^{N-1} y_k \cdot C_k$ by $\overline{C_q}$. By the lemma only the term $k = q$ remains:

$$X \cdot \overline{C_q} = y_q \cdot \underbrace{C_q \cdot \overline{C_q}}_{N}$$

$$y_q = \frac{1}{N} \cdot X \cdot \overline{C_q}$$

This is the **DFT** (*discrete Fourier transform*).

> [!note] Convolution (*konvolucija*)
> The notebook writes "convolution" under this formula, but $y_q = \frac{1}{N} X \cdot \overline{C_q}$ is a scalar product: the projection of $X$ onto $C_q$. Convolution enters the DFT elsewhere: by the convolution theorem, the DFT turns a (circular) convolution of signals into a product of their coefficients.

### Sequences (*zaporedja*)

**Definition.** A [[Sequence|sequence]] (*zaporedje*) is a map (*preslikava*)

$$\mathbb{N} \to \mathbb{R}, \qquad n \mapsto a_n$$

**Notation** (*zapisi*): $(a_n)_n = (a_1, a_2, \dots)$

- $n$ is the **index** (*indeks*),
- $a_n$ is the **term** (*člen*).
- $(\ )$ is like an array: the order matters (*važen vrstni red*). With $[\ ]$ the order does not matter (*ni pomemben vrstni red*).

#### Explicit definition (*eksplicitno*)

$$a_n = f(n)$$

#### Recursive definition (*rekurzivno*)

1. **One-term** (*enočleno*): we give the initial term (*začetni člen*) and
   $$a_{n+1} = f(a_n)$$
2. **Multi-term** (*veččleno*): we give the first few terms and the recursion.

   Example: the [[Fibonacci Sequence|Fibonacci sequence]] (*Fibonaccijevo zaporedje*)
   $$a_1 = a_2 = 1, \qquad a_n = a_{n-1} + a_{n-2}$$

#### Arithmetic sequence (*aritmetično zaporedje*)

$$a_n = a_1 + (n-1)k, \qquad a_{n+1} = a_n + k, \qquad k \in \mathbb{R}$$

#### Geometric sequence (*geometrijsko zaporedje*)

$$a_n = a_1 \cdot q^{n-1}, \qquad a_{n+1} = a_n \cdot q, \qquad q \in \mathbb{R}$$

Example: $\left((-1)^n\right)_n = (-1, 1, -1, 1, \dots)$

#### Example: the [[Collatz Conjecture|Collatz conjecture]] (*Collatzova domneva*)

$$a_{n+1} = \begin{cases} \dfrac{a_n}{2}, & \text{if } a_n \text{ is even (*sodo*)} \\[2mm] 3a_n + 1, & \text{if } a_n \text{ is odd (*liho*)} \end{cases}$$

**Conjecture** (*domneva*): does this sequence return to $1$ for every $a_1 \in \mathbb{N}$?

#### Graphical display of a recursive sequence (*grafični prikaz rekurzivnega zaporedja*)

For $a_{n+1} = f(a_n)$: go up from $a_n$ to the graph of $f$, then across to the line $y = x$, which gives $a_{n+1}$ on the $x$-axis, and repeat.

![[Calculus 3 cobweb.svg]]

The sequence converges to this limit (*konvergira proti tej limiti*): the intersection of $f(x)$ and $y = x$.

### Properties of sequences (*lastnosti zaporedij*)

A sequence $(a_n)_n$ is:

- **bounded above** (*navzgor omejeno*) if there is an upper bound (*zgornja meja*) $M \in \mathbb{R}$: $\forall n \in \mathbb{N}:\ a_n \leq M$.
  Such a sequence has a least upper bound, the **supremum** $\sup(a_n)$.
- **bounded below** (*navzdol omejeno*) if there is a lower bound (*spodnja meja*) $m \in \mathbb{R}$: $\forall n \in \mathbb{N}:\ a_n \geq m$.
  Such a sequence has a greatest lower bound, the **infimum** $\inf(a_n)$.
- **bounded** (*omejeno*) if it is bounded above and below.
- **increasing** (*naraščajoče*) if $a_{n+1} \geq a_n$, $\forall n$ (**strictly increasing** — *strogo naraščajoče* — if $a_{n+1} > a_n$, $\forall n$).
- **decreasing** (*padajoče*) if $a_{n+1} \leq a_n$, $\forall n$ (**strictly decreasing** — *strogo padajoče* — if $a_{n+1} < a_n$, $\forall n$).
- **monotone** (*monotono*) if it is increasing or decreasing.

### Constructing the limit (*konstrukcija limite*)

**What does it mean that we know $\pi$?** (*Kaj pomeni, da poznamo π?*) We can compute the number to any precision (*na poljubno natančnost*).

- We know $\pi$ if we can compute any finite number of its digits (*poljubno končno št. njegovih števk*).
- We know it if we can compute it arbitrarily well (*poljubno dobro*): for any precision $\varepsilon > 0$ we will sooner or later compute $\pi$ to within $\varepsilon$ (*prej ali slej izračunali π na ε natančno*).

### Limit (*limita*)

**Definition.** $a \in \mathbb{R}$ is the [[Limit of a Sequence|limit]] of the sequence $(a_n)_n$, written $a = \lim\limits_{n \to \infty} a_n$, if

$$\forall \varepsilon > 0\ \ \exists N \in \mathbb{N}:\ |a - a_n| < \varepsilon, \quad \forall n \geq N$$

A sequence is **convergent** (*konvergentno*) if it has a limit, and **divergent** (*divergentno*) if it does not.

## Questions

- [ ] Why is the resolution chosen as $N = 2^m$?

## Connections

- Course: [[Calculus]]
- Previous lecture: [[2026-10-14 - Polar Form of Complex Numbers - 2]] — Euler's formula, $n$-th roots of unity (the entries of $C_k$ lie on a regular $N$-gon)
- [[2026-10-11 - Numbers - 1]] — bounds, supremum and infimum of sets
- [[Complex Number]]

## Sources

- Handwritten notes: [[Sources/calculus/photoNotes/lectures/lecture 3.pdf|lecture 3]]
- J. Globevnik, M. Brojan, *Analiza I* (2012), sections 2.2 sequences, 2.4 convergent sequences, 2.5 monotone sequences: [[Sources/calculus/skripta.pdf#page=43|skripta p. 33]], [[Sources/calculus/skripta.pdf#page=46|p. 36]], [[Sources/calculus/skripta.pdf#page=51|p. 41]]
- [Discrete Fourier transform — Wikipedia](https://en.wikipedia.org/wiki/Discrete_Fourier_transform)
