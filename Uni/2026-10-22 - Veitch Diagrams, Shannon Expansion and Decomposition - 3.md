---
type: "[[Lectures]]"
course: "[[Introduction to Digital Circuits]]"
date: 2026-10-22
week: "3"
---

# 2026-10-22 - Veitch Diagrams, Shannon Expansion and Decomposition

## Main Idea

A [[Switching Function|switching function]] can be drawn instead of written. [[Venn Diagram|Venn diagrams]] show that the regions cut out by the circles are exactly the [[Minterm|minterms]]. A [[Veitch Diagram|Veitch diagram]] arranges the $2^n$ minterms in a grid where every variable covers half of the cells. We enter the 1s of the function into it.

Then three tools for working with a function:

- **[[Shannon Expansion|Separation]]** (*ločenje*, Shannon's theorem) splits a function by one variable into two functions of $n-1$ variables. Separating by all variables gives the PDNO (or, in the dual form, the PKNO).
- **[[Functional Decomposition|Decomposition]]** (*dekompozicija preklopne funkcije*) writes $f$ as $g(h(\dots), \dots)$ with disjoint inputs. It is not always possible.
- The **[[Boolean Difference|Boolean difference]]** (*preklopna / Boolova diferenca*) tells whether $f$ depends on a variable $x_i$.

## Notes

### ODV 3 — Venn diagrams (*Vennovi diagrami*)

![[Digital Circuits 3 Venn diagrams.svg]]

Each circle bounds one variable. The intersections, and the outside of the circles, are the minterms (*to so mintermi*):

- 2 variables: $x\bar{y}$, $xy$, $\bar{x}y$ and outside $\bar{x}\bar{y}$
- 3 variables: $a\bar{b}\bar{c}$, $ab\bar{c}$, $\bar{a}b\bar{c}$, $abc$, $a\bar{b}c$, $\bar{a}bc$, $\bar{a}\bar{b}c$ and outside $\bar{a}\bar{b}\bar{c}$

### Veitch diagram (*Veitchev diagram*)

A Veitch diagram for $n$ variables has $2^n$ cells, one for each minterm. **Each variable covers half of the cells** (*$x_1$ pokriva polovico polj*). The cell where the covered regions meet is the minterm:

![[Digital Circuits 3 Veitch 4 variables.svg]]

- row 1, column 2: $x_1, x_2, x_3, \bar{x}_4$ → minterm $m_{14}$
- row 1, column 4: $\bar{x}_1, x_2, \bar{x}_3, \bar{x}_4$ → minterm $m_4$

The index comes from the truth table, with $x_1$ as the most significant bit:

| | $x_1$ | $x_2$ | $x_3$ | $x_4$ |
|---|:-:|:-:|:-:|:-:|
| $m_4$ | 0 | 1 | 0 | 0 |
| $m_{14}$ | 1 | 1 | 1 | 0 |

#### Example

We write only the 1s into the cells:

![[Digital Circuits 3 Veitch example.svg]]

$$f(x_1, x_2, x_3, x_4) = \bar{x}_1 \lor x_2 x_4 \lor x_3 x_4$$

- $\bar{x}_1$ is the right half (columns 3–4),
- $x_2 x_4$ is the second row,
- $x_3 x_4$ is where the $x_3$ columns meet the $x_4$ rows.

#### For 1, 2 and 3 variables (*za 1, 2, 3 spremenljivke*)

![[Digital Circuits 3 Veitch 1-3 variables.svg]]

- $n = 1$: two cells, $m_1$ (covered by $x_1$) and $m_0$. Example: $f(x) = \bar{x}$ has $0$ in the $x$ cell and $1$ in the other.
- $n = 2$: four cells, $\begin{smallmatrix} m_3 & m_1 \\ m_2 & m_0 \end{smallmatrix}$.
- $n = 3$: eight cells; $x_1$ covers the left half, $x_2$ the top row, $x_3$ the middle two columns.

#### For 5 variables (*za 5 spremenljivk*)

$n = 5$, so $2^5 = 32$ cells. The diagram for 4 variables is doubled, and the new half is covered by $x_5$:

![[Digital Circuits 3 Veitch 5 variables.svg]]

$$\bar{x}_1 x_2 x_3 \bar{x}_4 \bar{x}_5 = m_{12}$$

(the notebook computes the index from the binary digits $01100_2 = 8 + 4 = 12$).

#### Larger diagram ($8 \times 8$)

![[Digital Circuits 3 Veitch 6 variables.svg]]

The notebook marks the cell $\bar{x}_1 \bar{x}_2 x_3 x_4 x_5 = m_7$ ($00111_2 = 7$ with $x_1$ as the most significant bit; the notebook wrote $m_{13}$). The notebook labels both the top half and the left half as $x_5$. For 6 variables one of them must be $x_6$.

### Separation — Shannon's theorem (*ločenje, Shanonov teorem*)

Separating a function of 3 variables gives two functions of 2 variables (*3 sp. → 2 sp., 2 sp.*):

$$f(a, b, c) = f(0, b, c)\,\bar{a} \lor f(1, b, c)\,a$$

| $a$ | $b$ | $c$ | |
|:-:|:-:|:-:|---|
| 0 | 0 | 0 | |
| 0 | 0 | 1 | $f(0, b, c)$ |
| 0 | 1 | 0 | |
| 0 | 1 | 1 | |
| 1 | 0 | 0 | |
| 1 | 0 | 1 | $f(1, b, c)$ |
| 1 | 1 | 0 | |
| 1 | 1 | 1 | |

The upper half of the truth table is $f(0, b, c)$ and the lower half is $f(1, b, c)$.

In general (separated by $x_1$, *ločil sem po $x_1$*):

$$f(x_1, x_2, \dots, x_n) = f(0, x_2, \dots, x_n)\,\bar{x}_1 \lor f(1, x_2, \dots, x_n)\,x_1$$

#### Dual form (*dualna oblika*)

$$f(a, b, c) = \big(f(0, b, c) \lor a\big)\big(f(1, b, c) \lor \bar{a}\big)$$

$$f(x_1, x_2, \dots, x_n) = \big(\underbrace{f(0, x_2, \dots, x_n)}_{f_0(x_2, \dots, x_n)} \lor x_1\big)\big(\underbrace{f(1, x_2, \dots, x_n)}_{f_1(x_2, \dots, x_n)} \lor \bar{x}_1\big)$$

$f$ has $n$ variables; $f_0$ and $f_1$ have $n - 1$ variables each.

#### Separating by all variables gives the PDNO

Separate by $b$ (*ločimo po spremenljivki $b$*):

$$= \big(f(0, 0, c)\,\bar{b} \lor f(0, 1, c)\,b\big)\,\bar{a} \lor \big(f(1, 0, c)\,\bar{b} \lor f(1, 1, c)\,b\big)\,a$$

Separate by $c$:

$$
\begin{aligned}
= \Big(&\big(f(0,0,0)\,\bar{c} \lor f(0,0,1)\,c\big)\,\bar{b} \lor \big(f(0,1,0)\,\bar{c} \lor f(0,1,1)\,c\big)\,b\Big)\,\bar{a} \;\lor \\
\Big(&\big(f(1,0,0)\,\bar{c} \lor f(1,0,1)\,c\big)\,\bar{b} \lor \big(f(1,1,0)\,\bar{c} \lor f(1,1,1)\,c\big)\,b\Big)\,a
\end{aligned}
$$

If we open the brackets (*če odpravimo oklepaje*):

$$
\begin{aligned}
= {} & f(0,0,0)\,\bar{c}\bar{b}\bar{a} \lor f(0,0,1)\,c\bar{b}\bar{a} \lor f(0,1,0)\,\bar{c}b\bar{a} \lor f(0,1,1)\,cb\bar{a} \\
\lor {} & f(1,0,0)\,\bar{c}\bar{b}a \lor f(1,0,1)\,c\bar{b}a \lor f(1,1,0)\,\bar{c}ba \lor f(1,1,1)\,cba \\
= {} & m_0 f(0,0,0) \lor m_1 f(0,0,1) \lor m_2 f(0,1,0) \lor m_3 f(0,1,1) \\
\lor {} & m_4 f(1,0,0) \lor m_5 f(1,0,1) \lor m_6 f(1,1,0) \lor m_7 f(1,1,1)
\end{aligned}
$$

This is the **PDNO**:

$$= m_0 f_0 \lor m_1 f_1 \lor \dots \lor m_7 f_7 = \bigvee_{i=0}^{7} m_i f_i$$

In the truth table each separation halves the rows again: $f(0, b, c)$ splits into $f(0, 0, c)$ and $f(0, 1, c)$, these into $f(0, 0, 0)$ and $f(0, 0, 1)$, … We keep halving (*delimo na pol*) until we reach the PDNO.

#### Example 1: $f(x_1, x_2, x_3) = (x_1 \nabla x_2) \lor x_1 x_2 x_3$

Separate by $x_1$:

$$
\begin{aligned}
f(x_1, x_2, x_3) &= f(0, x_2, x_3)\,\bar{x}_1 \lor f(1, x_2, x_3)\,x_1 \\
&= \big((0 \nabla x_2) \lor 0x_2x_3\big)\,\bar{x}_1 \lor \big((1 \nabla x_2) \lor 1x_2x_3\big)\,x_1 \\
&= \underbrace{(x_2)}_{f(0, x_2, x_3)}\,\bar{x}_1 \lor \underbrace{(\bar{x}_2 \lor x_2 x_3)}_{f(1, x_2, x_3)}\,x_1
\end{aligned}
$$

Separate by $x_2$:

$$
\begin{aligned}
&= (0\bar{x}_2 \lor 1x_2)\,\bar{x}_1 \lor \big((\bar{0} \lor 0x_3)\,\bar{x}_2 \lor (\bar{1} \lor 1x_3)\,x_2\big)\,x_1 \\
&= x_2\bar{x}_1 \lor (\bar{x}_2 \lor x_3 x_2)\,x_1
\end{aligned}
$$

The $\bar{x}_2$ part will be 1 anyway (*to bo itak 1*), whatever $x_3$ is. Separate by $x_3$:

$$
\begin{aligned}
&= (1\bar{x}_3 \lor 1x_3)\,x_2\bar{x}_1 \lor \big((1x_3 \lor 1\bar{x}_3)\,\bar{x}_2 \lor (0\bar{x}_3 \lor 1x_3)\,x_2\big)\,x_1 \\
&= \bar{x}_3x_2\bar{x}_1 \lor x_3x_2\bar{x}_1 \lor x_3\bar{x}_2x_1 \lor \bar{x}_3\bar{x}_2x_1 \lor x_1x_2x_3 \\
&= \bar{x}_1x_2\bar{x}_3 \lor \bar{x}_1x_2x_3 \lor x_1\bar{x}_2x_3 \lor x_1\bar{x}_2\bar{x}_3 \lor x_1x_2x_3 \\
&= m_2 \lor m_3 \lor m_5 \lor m_4 \lor m_7
\end{aligned}
$$

Check with the truth table:

| $x_1$ | $x_2$ | $x_3$ | $f$ |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 1 |

**The same function with the dual form** gives the PKNO:

$$
\begin{aligned}
f(x_1, x_2, x_3) &= \big(f(0, x_2, x_3) \lor x_1\big)\big(f(1, x_2, x_3) \lor \bar{x}_1\big) \\
&= \big((0 \nabla x_2) \lor 0x_2x_3 \lor x_1\big)\big((1 \nabla x_2) \lor 1x_2x_3 \lor \bar{x}_1\big) \\
&= \big((x_2) \lor x_1\big)\big((\bar{x}_2 \lor x_2x_3) \lor \bar{x}_1\big) \\
&= \big((0 \lor x_2)(1 \lor \bar{x}_2) \lor x_1\big)\Big(\big((\bar{0} \lor 0x_3) \lor x_2\big)\big((\bar{1} \lor 1x_3) \lor \bar{x}_2\big) \lor \bar{x}_1\Big) \\
&= (x_2 \lor x_1)\big((x_3) \lor \bar{x}_2 \lor \bar{x}_1\big) \\
&= \big((0 \lor x_3)(0 \lor \bar{x}_3) \lor x_2 \lor x_1\big)\big((0 \lor x_3)(1 \lor \bar{x}_3) \lor \bar{x}_2 \lor \bar{x}_1\big) \\
&= (x_3 \lor x_2 \lor x_1)(\bar{x}_3 \lor x_2 \lor x_1)(x_3 \lor \bar{x}_2 \lor \bar{x}_1) \\
&= M_7\, M_6\, M_1
\end{aligned}
$$

These are the rows where $f = 0$ (000, 001, 110), with the maxterm index $2^n - 1 - i$ as in [[2026-10-15 - Complete Normal Forms and Logic Functions - 2|lecture 2]].

#### Example 2: $f(x_1, x_2, x_3) = \bar{x}_1\bar{x}_2 \lor x_1\bar{x}_2\bar{x}_3 \lor x_1x_2x_3$

$$
\begin{aligned}
f &= (\bar{0}\bar{x}_2 \lor 0\bar{x}_2\bar{x}_3 \lor 0x_2x_3)\,\bar{x}_1 \lor (\bar{1}\bar{x}_2 \lor 1\bar{x}_2\bar{x}_3 \lor 1x_2x_3)\,x_1 \\
&= (\bar{x}_2)\,\bar{x}_1 \lor (\bar{x}_2\bar{x}_3 \lor x_2x_3)\,x_1 \\
&= (\bar{0}\bar{x}_2 \lor \bar{1}x_2)\,\bar{x}_1 \lor \big((\bar{0}\bar{x}_3 \lor 0x_3)\,\bar{x}_2 \lor (\bar{1}\bar{x}_3 \lor 1x_3)\,x_2\big)\,x_1 \\
&= \bar{x}_2\bar{x}_1 \lor (\bar{x}_3\bar{x}_2 \lor x_3x_2)\,x_1 \\
&= (1\bar{x}_3 \lor 1x_3)\,\bar{x}_2\bar{x}_1 \lor \Big(\big((\bar{0}\bar{x}_2)\,\bar{x}_3 \lor (\bar{1}\bar{x}_2)\,x_3\big) \lor \big((0x_2)\,\bar{x}_3 \lor (1x_2)\,x_3\big)\Big)\,x_1 \\
&= \bar{x}_3\bar{x}_2\bar{x}_1 \lor x_3\bar{x}_2\bar{x}_1 \lor (\bar{x}_2\bar{x}_3 \lor x_2x_3)\,x_1 \\
&= \bar{x}_1\bar{x}_2\bar{x}_3 \lor \bar{x}_1\bar{x}_2x_3 \lor x_1\bar{x}_2\bar{x}_3 \lor x_1x_2x_3 \\
&= m_0 \lor m_1 \lor m_4 \lor m_7
\end{aligned}
$$

### Decomposition of a switching function (*dekompozicija preklopne funkcije*)

**Not always possible** (*ni vedno možna*).

We split the inputs into two parts, if possible (*vhode razdelim na 2 dela, če se da*): $s$ inputs go into a function $h$, and its output goes together with the remaining $n - s$ inputs into $g$.

![[Digital Circuits 3 decomposition.svg]]

The notebook adds that this does not hold for non-commutative functions (*to ne velja pri nekomutativnih funkcijah*).

The inputs do not have to be in order; any permutation $x_{i_1}, x_{i_2}, \dots, x_{i_n}$ can be used (*lahko damo poljubno permutacijo*):

$$f(x_1, x_2, \dots, x_n) = g\big(h(x_{i_1}, x_{i_2}, \dots, x_{i_s}),\ x_{i_{s+1}}, \dots, x_{i_n}\big)$$

The same variable must not appear in both functions (*ista spremenljivka ne sme nastopati v različnih funkcijah*).

#### Example

$$f(x_1, x_2, x_3, x_4, x_5) = x_1x_2x_3 \lor x_1x_2x_4 \lor x_1x_2x_5 = x_1x_2(x_3 \lor x_4 \lor x_5)$$

$$h(x_3, x_4, x_5) = x_3 \lor x_4 \lor x_5, \qquad g(a, b, c) = abc$$

$$f(x_1, x_2, x_3, x_4, x_5) = g\big(h(x_3, x_4, x_5),\ x_1,\ x_2\big)$$

![[Digital Circuits 3 decomposition circuit.svg]]

### When does $f$ depend on $x_i$?

![[Digital Circuits 3 switching function.svg]]

How do we know whether $x_i$ has an effect (*kako vemo, če $x_i$ vpliva*)?

- We could minimise the function (we don't know how yet, *še ne znamo*). A variable that has no effect drops out, like $B$ here: $A + B + C - D - B = A + C - D$.
- Or check whether

$$f(x_1, x_2, \dots, 0, \dots, x_n) \overset{?}{=} f(x_1, x_2, \dots, 1, \dots, x_n)$$

If the equality holds (*če velja enakost*), $f$ does not depend on $x_i$.

### Switching / Boolean difference (*preklopna / Boolova diferenca*)

$$\frac{df(x_1, x_2, \dots, x_n)}{dx_i} = f(x_1, x_2, \dots, 0, \dots, x_n) \;\nabla\; f(x_1, x_2, \dots, 1, \dots, x_n)$$

It uses the [[Exclusive Or|sum modulo 2]]: if we add two equal things, we get 0 (*če seštejemo 2 enaki stvari, dobimo 0*).

| $a$ | $b$ | $a \nabla b$ |
|:-:|:-:|:-:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

The result is 0 if the function does not depend on $x_i$ (*rezultat je 0, če funkcija ni odvisna*).

#### Example: $f(x_1, x_2, x_3, x_4) = x_1x_3 \lor \bar{x}_1x_3 \lor \bar{x}_2x_4$

$$
\begin{aligned}
\frac{df(x_1, x_2, x_3, x_4)}{dx_1} &= f(0, x_2, x_3, x_4) \;\nabla\; f(1, x_2, x_3, x_4) \\
&= (0x_3 \lor \bar{0}x_3 \lor \bar{x}_2x_4) \;\nabla\; (1x_3 \lor \bar{1}x_3 \lor \bar{x}_2x_4) \\
&= (x_3 \lor \bar{x}_2x_4) \;\nabla\; (x_3 \lor \bar{x}_2x_4) = 0
\end{aligned}
$$

→ $f$ does not depend on $x_1$ (*ni odvisna od $x_1$*).

## Questions

- [ ] Why does the decomposition "not hold for non-commutative functions"? Which part of $g(h(\dots), \dots)$ does the remark refer to?
- [ ] How are the variables placed in a Veitch diagram for 6 variables (which halves do $x_5$ and $x_6$ cover)?

## Connections

- Course: [[Introduction to Digital Circuits]]
- Previous lecture: [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]]: minterms, maxterms, PDNO and PKNO (here derived again by separation)
- [[Minterm]], [[Maxterm]], [[Switching Function]], [[Exclusive Or]], [[Truth Table]]
- [[Duality]]: the dual form of separation swaps $\lor \leftrightarrow \land$ and $x_1 \leftrightarrow \bar{x}_1$
- [[Propositional Logic]]: the same normal forms (Discrete structures)

## Sources

- Handwritten notes: [[Sources/introduction_to_digital_circuits/photoNotes/lectures/lecture 3.pdf|lecture 3]]
- Slides: [[Sources/introduction_to_digital_circuits/ODV.pdf#page=34|ODV]] (N. Zimic), 3-45 – 3-64
- Script: [[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=25|ODV skripta]], 3.1 Veitch diagram (PDF p. 25), 7.1 separation of switching functions ([[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=45|PDF p. 45]])
