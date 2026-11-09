---
type: "[[Lectures]]"
course: "[[Introduction to Digital Circuits]]"
date: 2026-10-29
week: "4"
---

# 2026-10-29 - Functionally Complete Systems and Closed Classes

## Main Idea

A **[[Functional Completeness|functionally complete system]]** (*funkcijsko poln sistem*) is a set of functions that can realise any switching function. There are two ways to check a set:

- **Reduction to a known complete system:** express $\lor$, $\land$ and negation with the functions of the set. Examples: $\{\downarrow\}$, $\{\uparrow\}$, $\{\to, 0\}$, $\{\equiv, \lor, 0\}$.
- **[[Closed Class|Closed classes]]** (*zaprti razredi*): there are 5 classic closed classes, $T_0$, $T_1$, $S$, $L$ and $M$. A set is complete if it **opens** every one of them (*odpira*), i.e. for every class at least one function of the set is not in it.

At the end: the **Sheffer** and **Peirce** complete systems. Every function can be written with [[Sheffer Stroke|NAND]] only (PSNO, which is the PDNO) or with [[Peirce Arrow|NOR]] only (PPNO, which is the PKNO). Each gives a two-level circuit.

## Notes

### ODV 4 — Functionally complete system (*funkcijsko poln sistem*)

Starting from $\{\lor, \land, \neg\}$, conjunction and disjunction can be swapped with [[De Morgan's Laws|De Morgan]]:

$$ab = \overline{\bar{a} \lor \bar{b}} \qquad a \lor b = \overline{\bar{a}\bar{b}}$$

#### Peirce arrow / NOR $\{\downarrow\}$

$$a \downarrow b = \overline{a \lor b}$$

With $b = a$ we get negation:

$$a \downarrow a = \overline{a \lor a} = \bar{a}$$

$$a \lor b = \overline{a \downarrow b} = (a \downarrow b) \downarrow (a \downarrow b)$$

$$ab = \overline{\bar{a} \lor \bar{b}} = \bar{a} \downarrow \bar{b} = (a \downarrow a) \downarrow (b \downarrow b)$$

#### Sheffer stroke / NAND $\{\uparrow\}$

$$a \uparrow b = \overline{ab}$$

$$a \uparrow a = \overline{aa} = \bar{a}$$

$$ab = \overline{a \uparrow b} = (a \uparrow b) \uparrow (a \uparrow b)$$

$$a \lor b = \overline{\bar{a}\bar{b}} = \bar{a} \uparrow \bar{b} = (a \uparrow a) \uparrow (b \uparrow b)$$

#### $\{\to, 0\}$

$$a \to b = \bar{a} \lor b$$

$$a \to 0 = \bar{a} \lor 0 = \bar{a}$$

$$a \lor b = \bar{a} \to b = (a \to 0) \to b$$

$$ab = \overline{\bar{a} \lor \bar{b}} = \overline{a \to \bar{b}} = \overline{a \to (b \to 0)} = \big(a \to (b \to 0)\big) \to 0$$

#### $\{\equiv, \lor, 0\}$

$$a \equiv 0 = \bar{a}$$

$$ab = \overline{\bar{a} \lor \bar{b}} = \overline{(a \equiv 0) \lor (b \equiv 0)} = \big((a \equiv 0) \lor (b \equiv 0)\big) \equiv 0$$

#### Example of a set that is not functionally complete (*primer funkcijsko ne-polnega sistema*)

$$\{\equiv, \lor, \land\}$$

We cannot get negation (*negacije ne moremo dobiti*):

$$a \equiv 1 = a \qquad a \lor 1 = 1$$

All three functions preserve one ($1 \equiv 1 = 1$, $1 \lor 1 = 1$, $1 \land 1 = 1$, so they are all in $T_1$), so every combination of them gives 1 when all inputs are 1, and $\bar{a}$ is not possible.

### Closed classes (*zaprti razredi*)

$$M \subset P_2$$

If we have conjunction and disjunction ($a \lor b$, $ab$) and want to realise a function with $f(0, 0) = 1$, we cannot do it in any way (*tega v nobenem primeru ne moremo narediti*), so this is a closed class (*torej je zaprt razred*).

**Classic closed classes** (*klasični zaprti razredi*):

1. preserving zero (*ohranja ničle*): $f(0, 0) = 0$
2. preserving one (*ohranja enice*): $f(1, 1) = 1$
3. self-dual functions (*sebidualne funkcije*)
4. linear functions (*linearne funkcije*)
5. monotone functions (*monotone funkcije*)

#### 1. $T_0$ — preserving zero

$$f(x_1, x_2, \dots, x_n) \in T_0 : \quad f(0, 0, \dots, 0) = 0$$

$$0 \lor 0 = 0 \qquad 00 = 0$$

This is a closed class (*to je zaprt razred*).

#### 2. $T_1$ — preserving one

$$f(x_1, x_2, \dots, x_n) \in T_1 : \quad f(1, 1, \dots, 1) = 1$$

$$1 \lor 1 = 1 \qquad 11 = 1$$

We cannot realise $f(1, 1) = 0$ (*ne moremo realizirati*).

#### 3. $S$ — self-dual functions

$$f(x_1, x_2, \dots, x_n) \in S : \quad \underbrace{\overline{f(\bar{x}_1, \bar{x}_2, \dots, \bar{x}_n)} = f_d(x_1, x_2, \dots, x_n)}_{\text{dual function}} = f(x_1, x_2, \dots, x_n)$$

(see [[Duality]])

Example:

| $x_1$ | $x_2$ | $x_3$ | $f(x_1, x_2, x_3)$ |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 1 |

$$f(x_1, x_2, x_3) = m_1 \lor m_2 \lor m_4 \lor m_7 = \lor(1, 2, 4, 7) = \bar{x}_1\bar{x}_2x_3 \lor \bar{x}_1x_2\bar{x}_3 \lor x_1\bar{x}_2\bar{x}_3 \lor x_1x_2x_3$$

$$
\begin{aligned}
f_d(x_1, x_2, x_3) &= \overline{f(\bar{x}_1, \bar{x}_2, \bar{x}_3)} \\
&= \overline{\bar{\bar{x}}_1\bar{\bar{x}}_2\bar{x}_3 \lor \bar{\bar{x}}_1\bar{x}_2\bar{\bar{x}}_3 \lor \bar{x}_1\bar{\bar{x}}_2\bar{\bar{x}}_3 \lor \bar{x}_1\bar{x}_2\bar{x}_3} \\
&= \overline{x_1x_2\bar{x}_3 \lor x_1\bar{x}_2x_3 \lor \bar{x}_1x_2x_3 \lor \bar{x}_1\bar{x}_2\bar{x}_3} \\
&= \overline{\lor(6, 5, 3, 0)} = \overline{\lor(0, 3, 5, 6)} \\
&= \lor(1, 2, 4, 7)
\end{aligned}
$$

$f_d = f$, so this is a self-dual function (*sebidualna funkcija*).

#### 4. $L$ — linear functions

$f \in L$ if we can write it with a linear equation (*če lahko zapišem z linearno enačbo*), using the [[Exclusive Or|sum modulo 2]] $\nabla$:

$$f(x_1, x_2, \dots, x_n) = a_0 \nabla a_1x_1 \nabla a_2x_2 \nabla \dots \nabla a_nx_n$$

Example:

| $x_1$ | $x_2$ | $x_3$ | $f(x_1, x_2, x_3)$ |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 0 |

$$f(x_1, x_2, x_3) = a_0 \nabla a_1x_1 \nabla a_2x_2 \nabla a_3x_3$$

$$
\left.
\begin{aligned}
f(0, 0, 0) &= a_0 \nabla a_1x_1 \nabla a_2x_2 \nabla a_3x_3 = 0 \\
f(0, 0, 1) &= a_0 \nabla a_1x_1 \nabla a_2x_2 \nabla a_3x_3 = 0 \\
&\ \ \vdots \\
f(1, 1, 1) &= a_0 \nabla a_1x_1 \nabla a_2x_2 \nabla a_3x_3 = 0
\end{aligned}
\right\}\ 8 \text{ equations}, \ 4 \text{ unknowns}
$$

We take any 4 equations and compute the $a$'s, then use the other 4 to check (*vzamem poljubne 4 enačbe, izračunam a-je, potem uporabim ostale 4 za preverit*). If they hold, the function is linear; if not, it is not.

We take the rows $000$, $100$, $010$, $001$, because they are the easiest to compute (*ker je najlažje zračunat*):

$$
\begin{aligned}
f(0, 0, 0) &= a_0 \nabla a_10 \nabla a_20 \nabla a_30 = a_0 = 0 \\
f(1, 0, 0) &= a_0 \nabla a_11 \nabla a_20 \nabla a_30 = a_0 \nabla a_1 = a_1 = 1 \\
f(0, 1, 0) &= a_0 \nabla a_10 \nabla a_21 \nabla a_30 = a_0 \nabla a_2 = a_2 = 1 \\
f(0, 0, 1) &= a_0 \nabla a_10 \nabla a_20 \nabla a_31 = a_0 \nabla a_3 = a_3 = 0
\end{aligned}
$$

We still have 4 unused equations, which we must check (*imamo še 4 neuporabljene enačbe, moramo preverit*):

$$
\begin{aligned}
f(0, 1, 1) &= a_0 \nabla a_10 \nabla a_21 \nabla a_31 = a_0 \nabla a_2 \nabla a_3 = 0 \nabla 1 \nabla 0 = 1 \ \checkmark \\
f(1, 0, 1) &= a_0 \nabla a_11 \nabla a_20 \nabla a_31 = a_0 \nabla a_1 \nabla a_3 = 0 \nabla 1 \nabla 0 = 1 \ \checkmark \\
f(1, 1, 0) &= a_0 \nabla a_11 \nabla a_21 \nabla a_30 = a_0 \nabla a_1 \nabla a_2 = 0 \nabla 1 \nabla 1 = 0 \ \checkmark \\
f(1, 1, 1) &= a_0 \nabla a_11 \nabla a_21 \nabla a_31 = a_0 \nabla a_1 \nabla a_2 \nabla a_3 = 0 \nabla 1 \nabla 1 \nabla 0 = 0 \ \checkmark
\end{aligned}
$$

This shows that the function is linear (*s tem smo pokazali, da je funkcija linearna*). Written with the linear equation:

$$f(x_1, x_2, x_3) = a_0 \nabla a_1x_1 \nabla a_2x_2 \nabla a_3x_3 = 0 \nabla 1x_1 \nabla 1x_2 \nabla 0x_3 = x_1 \nabla x_2$$

#### 5. $M$ — monotone functions

$$f(x_1, x_2, \dots, x_n) \in M : \quad \tilde{w}_i \le \tilde{w}_j \;\to\; f(\tilde{w}_i) \le f(\tilde{w}_j)$$

$\tilde{w}$ is an input vector (*vhodni vektor*) of $f(x_1, x_2, x_3)$: $(0, 0, 0)$, $(0, 0, 1)$, …, $(1, 1, 1)$.

Vectors are compared position by position:

- $(0, 0, 0, 0) < (0, 0, 1, 0)$, because it is larger in one position (*ker je na 1 mestu večji*)
- $(0, 0, 1, 1) < (0, 1, 1, 1)$
- $(1, 1, 0, 0)$ and $(0, 0, 1, 0)$ **cannot be compared** (*ne da se primerjat*), because there is a contradiction (*protislovje*)
- $(1, 1, 1, 0)$ and $(0, 0, 0, 1)$ cannot be compared either

### Checking functional completeness with closed classes

We check functional completeness by whether the set **opens these 5 classes** (*funkcijsko polnost preverimo, če odpirajo teh 5 razredov*).

#### Example: $F = \{\lor, \to, 1\}$

$a \to b = \bar{a} \lor b$

| $a$ | $b$ | $a \lor b$ | $a \to b$ | $1$ |
|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 1 | 1 |
| 0 | 1 | 1 | 1 | 1 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

**$T_0$:**

- $0 \lor 0 = 0$ (in class $T_0$, *spada v razred $T_0$*)
- $0 \to 0 = 1$ (not in it)
- $1 = 1$ (not in it)

**$T_1$:**

- $1 \lor 1 = 1$ (in $T_1$)
- $1 \to 1 = 1$ (in $T_1$)
- $1 = 1$ (in $T_1$)

Already from this we can conclude that the set is not functionally complete (we cannot escape $T_1$, *ne moremo pobegniti $T_1$*): we can never get $f(1, 1, 1, \dots, 1) = 0$.

**$S$:**

- $x_1 \lor x_2 \overset{?}{=} \overline{\bar{x}_1 \lor \bar{x}_2} = x_1x_2$ (not equal, *ni enako*)
- $x_1 \to x_2 \overset{?}{=} \overline{\bar{x}_1 \to \bar{x}_2}$ (not equal)
- $1 \ne \bar{1}$

None of the functions is self-dual (*nobena od funkcij ni sebi dualna*).

**$L$:** disjunction:

$$
\begin{aligned}
f(x_1, x_2) &= a_0 \nabla a_1x_1 \nabla a_2x_2 \\
f(0, 0) &= a_0 \nabla a_10 \nabla a_20 = a_0 = 0 \\
f(1, 0) &= a_0 \nabla a_11 \nabla a_20 = a_0 \nabla a_1 = 0 \nabla a_1 = a_1 = 1 \\
f(0, 1) &= a_0 \nabla a_10 \nabla a_21 = a_0 \nabla a_2 = 0 \nabla a_2 = a_2 = 1 \\
f(1, 1) &= a_0 \nabla a_1x_1 \nabla a_2x_2 = 0 \nabla 1 \nabla 1 = 0
\end{aligned}
$$

But $1 \lor 1 = 1$, so disjunction is not linear (*disjunkcija ni linearna*).

Now for $a \to b$:

$$
\begin{aligned}
f(0, 0) &= a_0 = 1 \\
f(1, 0) &= a_0 \nabla a_1 = 1 \nabla a_1 = 0 \;\Rightarrow\; a_1 = 1 \\
f(0, 1) &= a_0 \nabla a_2 = 1 \nabla a_2 = 1 \;\Rightarrow\; a_2 = 0 \\
f(1, 1) &= a_0 \nabla a_1 \nabla a_2 = 1 \nabla 1 \nabla 0 = 0
\end{aligned}
$$

But $1 \to 1 = 1$, so implication is not linear either (*tudi implikacija ni linearna*). The constant 1 is linear (*konstanta 1 je linearna*).

**$M$:**

| $\tilde{w}_i$ | $\tilde{w}_j$ | disjunction $f(\tilde{w}_i) \le f(\tilde{w}_j)$ | implication $f(\tilde{w}_i) \le f(\tilde{w}_j)$ |
|---|---|:-:|:-:|
| $(0, 0) <$ | $(0, 1)$ | $0 \le 1$ | $1 \le 1$ |
| $(0, 0) <$ | $(1, 0)$ | $0 \le 1$ | $1 \not\le 0$ → not monotone |
| $(0, 0) <$ | $(1, 1)$ | $0 \le 1$ | $1 \le 1$ |
| $(0, 1)$ | $(1, 0)$ ! | — | — |
| $(0, 1) <$ | $(1, 1)$ | $1 \le 1$ | $1 \le 1$ |
| $(1, 0) <$ | $(1, 1)$ | $1 \le 1$ | $0 \le 1$ |
| | | ✓ monotone (*je monotona*) | not monotone (*ni monotona*) |

The constant 1 is monotone (*konstanta 1 je monotona*).

**Conclusion:** because we have problems with $T_1$, this set is not complete (*ker imamo težave s $T_1$, ta nabor ni poln*). If we had $F = \{\lor, \to, 0\}$, it would be complete (*bi bil poln*).

Summary of the example (from the checks above):

| | $T_0$ | $T_1$ | $S$ | $L$ | $M$ |
|---|:-:|:-:|:-:|:-:|:-:|
| $x_1 \lor x_2$ | ∈ | ∈ | ∉ | ∉ | ∈ |
| $x_1 \to x_2$ | ∉ | ∈ | ∉ | ∉ | ∉ |
| $1$ | ∉ | ∈ | ∉ | ∈ | ∈ |

### Sheffer functionally complete system (*Shefferjev funkcijsko poln sistem*)

The **PSNO** (complete Sheffer normal form, *popolna Shefferjeva normalna oblika*):

$$f(x_1, x_2, \dots, x_n) = \mathop{\Large\uparrow}_{i=0}^{2^n-1} (f_i \uparrow s_i) \qquad s_i = x_1^{w_{1i}} \uparrow x_2^{w_{2i}} \uparrow \dots \uparrow x_n^{w_{ni}}$$

Compare with the **PDNO**:

$$f(x_1, x_2, \dots, x_n) = \bigvee_{i=0}^{2^n-1} f_i m_i \qquad m_i = x_1^{w_{1i}} x_2^{w_{2i}} \dots x_n^{w_{ni}}$$

A chain of $\uparrow$ is **one operator** with many inputs, not a pairwise chain. $a \uparrow b \uparrow c$ is one 3-input NAND gate, while $(a \uparrow b) \uparrow c$ is two gates. The same holds for $\downarrow$, so watch the brackets (*isto velja pri $\downarrow$, pazi na oklepaje*):

![[Digital Circuits 4 NAND symbols.svg]]

The whole $f_i \uparrow x_1^{w_{1i}} \uparrow x_2^{w_{2i}} \uparrow \dots \uparrow x_n^{w_{ni}}$ is one operator (*to je vse skupaj 1 operator*):

$$
\begin{aligned}
f(x_1, x_2, \dots, x_n) &= \mathop{\Large\uparrow}_{i=0}^{2^n-1} \big(f_i \uparrow x_1^{w_{1i}} \uparrow x_2^{w_{2i}} \uparrow \dots \uparrow x_n^{w_{ni}}\big) = \mathop{\Large\uparrow}_{i=0}^{2^n-1} \overline{f_i\, x_1^{w_{1i}} x_2^{w_{2i}} \dots x_n^{w_{ni}}} \\
&= \mathop{\Large\uparrow}_{i=0}^{2^n-1} \overline{f_i m_i} = \overline{f_0m_0} \uparrow \overline{f_1m_1} \uparrow \dots \uparrow \overline{f_{2^n-1}m_{2^n-1}} \\
&= \overline{\overline{f_0m_0}\;\overline{f_1m_1} \dots \overline{f_{2^n-1}m_{2^n-1}}} \\
&= f_0m_0 \lor f_1m_1 \lor \dots \lor f_{2^n-1}m_{2^n-1} = \bigvee_{i=0}^{2^n-1} f_i m_i \quad \text{(PDNO)}
\end{aligned}
$$

So the PSNO is a two-level circuit of NAND gates:

![[Digital Circuits 4 PSNO circuit.svg]]

#### Example: $f(x_1, x_2, x_3, x_4) = \bar{x}_3 \lor \bar{x}_1x_2x_4$

The highest level (*najvišji nivo*) is the $\lor$. We use:

$$\bar{a} \lor \bar{b} = \overline{ab} = a \uparrow b \qquad a \lor b = \bar{a} \uparrow \bar{b}$$

$$f = x_3 \uparrow \overline{\bar{x}_1x_2x_4} = x_3 \uparrow (\bar{x}_1 \uparrow x_2 \uparrow x_4)$$

The bracket is important (*oklepaj je pomemben*).

### Peirce functionally complete system

The **PPNO** (complete Peirce normal form, *popolna Peirceova normalna oblika*):

$$f(x_1, x_2, \dots, x_n) = \mathop{\Large\downarrow}_{i=0}^{2^n-1} \big(f_i \downarrow P_{2^n-1-i}\big) \qquad P_{2^n-1-i} = x_1^{\bar{w}_{1i}} \downarrow x_2^{\bar{w}_{2i}} \downarrow \dots \downarrow x_n^{\bar{w}_{ni}}$$

PPNO → PKNO: the PPNO corresponds to the PKNO, as the PSNO does to the PDNO. It is a two-level circuit of NOR gates; $P$ are the outputs of the first level:

![[Digital Circuits 4 PPNO circuit.svg]]

#### Example: $f(x_1, x_2, x_3, x_4) = \overline{\bar{x}_3 \lor \bar{x}_1x_2x_4}$

$$\overline{a \lor b} = a \downarrow b$$

$$
\begin{aligned}
f &= \bar{x}_3 \downarrow \bar{x}_1x_2x_4 \\
&= \bar{x}_3 \downarrow \big(\overline{x_1 \lor \bar{x}_2 \lor \bar{x}_4}\big) \\
&= \bar{x}_3 \downarrow (x_1 \downarrow \bar{x}_2 \downarrow \bar{x}_4)
\end{aligned}
$$

If we leave out the brackets, $f(x_1, x_2, x_3, x_4) = \bar{x}_3 \downarrow x_1 \downarrow \bar{x}_2 \downarrow \bar{x}_4$ is a single 4-input NOR gate. **That is not the same** (*ni isto, če izpustimo oklepaje*):

![[Digital Circuits 4 NOR without brackets.svg]]

## Questions

- [ ] Why are the five classes $T_0$, $T_1$, $S$, $L$, $M$ enough, so that a set opening all of them is always complete?
- [ ] How do we check linearity with a Veitch diagram (the script mentions it as a second method)?

## Connections

- Course: [[Introduction to Digital Circuits]]
- Previous lecture: [[2026-10-22 - Veitch Diagrams, Shannon Expansion and Decomposition - 3]]
- [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]]: PDNO and PKNO, which the PSNO and PPNO rewrite
- [[Functional Completeness]]: the same idea in Discrete structures, [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]]
- [[Sheffer Stroke]], [[Peirce Arrow]], [[Duality]], [[Exclusive Or]], [[Minterm]], [[Maxterm]], [[De Morgan's Laws]]
- Exercises: [[Sources/introduction_to_digital_circuits/vaje/vaja4/vaje 4.pdf|vaje 4]]

## Sources

- Handwritten notes: [[Sources/introduction_to_digital_circuits/photoNotes/lectures/lecture 4.pdf|lecture 4]]
- Slides: [[Sources/introduction_to_digital_circuits/ODV.pdf#page=44|ODV]] (N. Zimic), 4-1 – 4-19
- Script: [[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=26|ODV skripta]], 3.2 functionally complete system (PDF p. 26), 4.1 closed classes and checking functional completeness ([[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=27|PDF p. 27]])
