---
type: "[[Lectures]]"
course: "[[Introduction to Digital Circuits]]"
date: 2026-10-15
week: "2"
---

# 2026-10-15 - Complete Normal Forms and Logic Functions

## Main Idea

Every [[Switching Function|switching function]] can be written from its [[Truth Table|truth table]] in two complete normal forms: as a disjunction of [[Minterm|minterms]] (PDNO, from the rows where $f = 1$) or as a conjunction of [[Maxterm|maxterms]] (PKNO, from the rows where $f = 0$). Minterms and maxterms are connected by [[De Morgan's Laws|De Morgan's law]], which lets us convert between the two forms. For $n$ variables there are $2^{2^n}$ different logic functions; for two variables these are 16 functions, among them NAND, NOR, XOR and equivalence, each with its own logic symbol. In hardware, logic 0 and 1 are represented by voltage levels.

## Notes

### ODV 2 — Writing truth tables

Write the rows of a truth table in binary order (00, 01, 10, 11):

| $a$ | $b$ | $a \lor b$ |
|:-:|:-:|:-:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

**Don't use this** (*ne uporabljaj tega*) — rows in random order:

| $a$ | $b$ | $a \lor b$ |
|:-:|:-:|:-:|
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |
| 0 | 0 | 0 |

### Minterms and maxterms (*mintermi in makstermi*)

For $n$ variables there are $2^n$ combinations (*kombinacij*). For two variables the minterms are:

$$xy, \quad x\bar{y}, \quad \bar{x}y, \quad \bar{x}\bar{y}$$

#### Minterm

$$m_i = x_1^{w_{1i}} x_2^{w_{2i}} \dots x_n^{w_{ni}}, \qquad i = 0, \dots, 2^n - 1$$

where

- $x^0 = \bar{x}$ … negation (*negacija*)
- $x^1 = x$ … no negation (*ni negacije*)
- $\tilde{w}_i = (w_{1i}, w_{2i}, \dots, w_{ni})$ … the input vector of row $i$ (the binary digits of $i$)

**Example:** $n = 4$, $i = 9$ → $\tilde{w}_9 = (1, 0, 0, 1)$ (first digit $w_{1,9}$, last digit $w_{4,9}$)

$$
m_9 = x_1^{w_{1,9}} x_2^{w_{2,9}} x_3^{w_{3,9}} x_4^{w_{4,9}}
= x_1^1 x_2^0 x_3^0 x_4^1
= x_1 \bar{x}_2 \bar{x}_3 x_4
$$

#### Maxterm (*maksterm*)

The dual form of a minterm is a maxterm:

$$M_{2^n-1-i} = x_1^{\overline{w_{1i}}} \lor x_2^{\overline{w_{2i}}} \lor \dots \lor x_n^{\overline{w_{ni}}}$$

**Example:** $M_5$ for $n = 3$ — first calculate $i$ (*najprej izračunaj $i$*):

$$2^3 - 1 - i = 5 \implies i = 2$$

#### Properties (*lastnosti*)

- **Minterm:** equals 1 in only one row (index) of the truth table.
- **Maxterm:** equals 0 in only one row (index) — the index runs in the opposite direction (*v obratni smeri*).

**Negation of a minterm is a maxterm** — using [[De Morgan's Laws|De Morgan]] ($\overline{ab} = \bar{a} \lor \bar{b}$) and $\overline{a^b} = a^{\bar{b}}$:

$$
\begin{aligned}
\overline{m_i} &= \overline{x_1^{w_{1i}} x_2^{w_{2i}} \dots x_n^{w_{ni}}} \\
&= \overline{x_1^{w_{1i}}} \lor \overline{x_2^{w_{2i}}} \lor \dots \lor \overline{x_n^{w_{ni}}} \\
&= x_1^{\overline{w_{1i}}} \lor x_2^{\overline{w_{2i}}} \lor \dots \lor x_n^{\overline{w_{ni}}} \\
&= M_{2^n-1-i} \quad \text{(maxterm)}
\end{aligned}
$$

Therefore:

$$m_i \lor M_{2^n-1-i} = m_i \lor \overline{m_i} = 1$$
$$m_i \, M_{2^n-1-i} = 0 \quad \text{(dual)}$$

The disjunction of all minterms is 1:

$$\bigvee_{i=0}^{2^n-1} m_i = m_0 \lor m_1 \lor \dots \lor m_{2^n-1} = 1$$

Two different minterms are never 1 at the same time:

$$m_i \, m_j = 0, \qquad i \neq j$$

### PDNO — complete disjunctive normal form (*popolna disjunktivna normalna oblika*)

$$f(x_1, x_2, \dots, x_n) = \bigvee_{i=0}^{2^n-1} m_i f_i$$

where $f_i = f(\tilde{w}_i)$ is the function value in row $i$ (e.g. row 5 → $f_5 = f(1, 0, 1)$).

**Example:**

| $i$ | $x_1$ | $x_2$ | $x_3$ | $f(x_1, x_2, x_3)$ |
|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 0 | $f_0 = 0$ |
| 1 | 0 | 0 | 1 | $f_1 = 1$ |
| 2 | 0 | 1 | 0 | $f_2 = 1$ |
| 3 | 0 | 1 | 1 | $f_3 = 0$ |
| 4 | 1 | 0 | 0 | $f_4 = 1$ |
| 5 | 1 | 0 | 1 | $f_5 = 0$ |
| 6 | 1 | 1 | 0 | $f_6 = 0$ |
| 7 | 1 | 1 | 1 | $f_7 = 1$ |

$$
\begin{aligned}
f(x_1, x_2, x_3) &= \bigvee_{i=0}^{7} m_i f_i \\
&= m_0 f_0 \lor m_1 f_1 \lor m_2 f_2 \lor m_3 f_3 \lor m_4 f_4 \lor m_5 f_5 \lor m_6 f_6 \lor m_7 f_7 \\
&= m_0 0 \lor m_1 1 \lor m_2 1 \lor m_3 0 \lor m_4 1 \lor m_5 0 \lor m_6 0 \lor m_7 1 \\
&= m_1 \lor m_2 \lor m_4 \lor m_7 \\
&= \bar{x}_1 \bar{x}_2 x_3 \lor \bar{x}_1 x_2 \bar{x}_3 \lor x_1 \bar{x}_2 \bar{x}_3 \lor x_1 x_2 x_3
\end{aligned}
$$

The terms with $f_i = 0$ drop out.

**Circuit:** one 3-input AND gate per minterm, all outputs into one OR gate:

![[Digital Circuits 2 PDNO circuit.svg]]

### PKNO — complete conjunctive normal form (*popolna konjunktivna normalna oblika*)

$$f(x_1, x_2, \dots, x_n) = \mathop{\&}_{i=0}^{2^n-1} \left( M_{2^n-1-i} \lor f_i \right)$$

We look at the rows where $f_i = 0$ (*gledamo, kjer je $f_i = 0$*).

**Same example as above:**

$$
\begin{aligned}
f(x_1, x_2, x_3) &= \mathop{\&}_{i=0}^{7} \left( M_{2^n-1-i} \lor f_i \right) \\
&= (M_7 \lor f_0)(M_6 \lor f_1)(M_5 \lor f_2)(M_4 \lor f_3)(M_3 \lor f_4)(M_2 \lor f_5)(M_1 \lor f_6)(M_0 \lor f_7) \\
&= (M_7 \lor 0)(M_6 \lor 1)(M_5 \lor 1)(M_4 \lor 0)(M_3 \lor 1)(M_2 \lor 0)(M_1 \lor 0)(M_0 \lor 1)
\end{aligned}
$$

Using $a \lor 1 = 1$ and $a \lor 0 = a$:

$$
\begin{aligned}
&= M_7 \, 1 \, 1 \, M_4 \, 1 \, M_2 \, M_1 \, 1 = M_7 M_4 M_2 M_1 \\
&= \underbrace{(x_1 \lor x_2 \lor x_3)}_{M_7} \underbrace{(x_1 \lor \bar{x}_2 \lor \bar{x}_3)}_{M_4} \underbrace{(\bar{x}_1 \lor x_2 \lor \bar{x}_3)}_{M_2} \underbrace{(\bar{x}_1 \lor \bar{x}_2 \lor x_3)}_{M_1}
\end{aligned}
$$

### Simplified notation (*poenostavljeni zapisi*)

Only the indices of the terms are written:

- PDNO: $f(x_1, x_2, x_3) = \lor(1, 2, 4, 7)$ → $m_1, m_2, m_4, m_7$
- PKNO: $f(x_1, x_2, x_3) = \&(7, 4, 2, 1)$ → $M_7, M_4, M_2, M_1$

### Converting from one form to the other (*pretvarjanje iz ene v drugo obliko*)

$$f(x_1, x_2, x_3) = \lor(1, 4, 5, 6, 7)$$

| $x_1$ | $x_2$ | $x_3$ | $f(x_1, x_2, x_3)$ | $\overline{f(x_1, x_2, x_3)}$ |
|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 0 | 1 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 0 | 1 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 1 | 0 |
| 1 | 1 | 0 | 1 | 0 |
| 1 | 1 | 1 | 1 | 0 |

$$\overline{f(x_1, x_2, x_3)} = \lor(0, 2, 3) = m_0 \lor m_2 \lor m_3$$

Negate both sides ($\bar{\bar{f}} = f$) and use De Morgan ($\overline{a \lor b \lor c} = \bar{a}\bar{b}\bar{c}$):

$$
\begin{aligned}
f(x_1, x_2, x_3) = \overline{\overline{f(x_1, x_2, x_3)}} &= \overline{m_0 \lor m_2 \lor m_3} \\
&= \overline{m_0}\,\overline{m_2}\,\overline{m_3} = M_7 M_5 M_4 = \&(7, 5, 4)
\end{aligned}
$$

**Example with 4 variables** (PKNO → PDNO):

$$f(x_1, x_2, x_3, x_4) = \&(15, 13, 11, 10, 9, 5, 2, 1, 0) = M_{15} M_{13} M_{11} M_{10} M_9 M_5 M_2 M_1 M_0 \quad \text{(PKNO)}$$

The missing maxterms give the negated function $\bar{f}$:

$$\overline{f(x_1, x_2, x_3, x_4)} = \&(14, 12, 8, 7, 6, 4, 3) = M_{14} M_{12} M_8 M_7 M_6 M_4 M_3$$

We negate (*negiramo*):

$$f(x_1, x_2, x_3, x_4) = \overline{M_{14} M_{12} M_8 M_7 M_6 M_4 M_3}$$

Using $\overline{ab} = \bar{a} \lor \bar{b}$:

$$
\begin{aligned}
&= \overline{M_{14}} \lor \overline{M_{12}} \lor \overline{M_8} \lor \overline{M_7} \lor \overline{M_6} \lor \overline{M_4} \lor \overline{M_3} \qquad (15 - 14,\ 15 - 12,\ \dots) \\
&= m_1 \lor m_3 \lor m_7 \lor m_8 \lor m_9 \lor m_{11} \lor m_{12} \\
&= \lor(1, 3, 7, 8, 9, 11, 12) \quad \text{(PDNO)}
\end{aligned}
$$

**Terminology:**

- **complete** (*popolna*) — all variables appear (in every term)
- **normal** (*normalne*) — at most two levels of logic operators (*največ dva nivoja*)

### Chain forms (*verižne oblike*) and tree non-normal form (*drevesna nenormalna oblika*)

Trade-off: speed or number of elements? (*hitrost ali število elementov?*)

### Logic functions (*logične funkcije*)

A switching function (p.f.) with inputs $x_1, x_2, \dots, x_n$ and output $f(x_1, x_2, \dots, x_n)$. How many different functions can we make (*koliko različnih funkcij lahko naredim*)?

![[Digital Circuits 2 switching function.svg]]

In general (*v splošnem*): $2^{2^n}$

- $n = 1$: $2^{2^1} = 4$ functions:
  - $f(x) = \bar{x}$
  - $f(x) = x$
  - $f(x) = 1$
  - $f(x) = 0$
- $n = 2$: $2^{2^2} = 2^4 = 16$
- $n = 3$: $2^{2^3} = 256$

#### The 16 functions of two variables

For 2 independent variables we can make 16 different functions $f(x_1, x_2)$:

| Function | Expression | Name |
|---|---|---|
| $f_0$ | $0$ | constant 0 (*konstanta 0*) |
| $f_1$ | $\overline{x_1 \lor x_2} = x_1 \downarrow x_2$ | negation of disjunction, [[Peirce Arrow\|Peirce / NOR operator]] (*Piercov operator*) |
| $f_2$ | $\bar{x}_1 x_2 = \overline{x_2 \to x_1} = \overline{x_1 \lor \bar{x}_2}$ | negation of implication |
| $f_3$ | $\bar{x}_1$ | a function of 2 variables, but the result does not depend on $x_2$ |
| $f_4$ | $x_1 \bar{x}_2 = \overline{x_1 \to x_2}$ | negation of implication |
| $f_5$ | $\bar{x}_2$ | |
| $f_6$ | $x_1 \bar{x}_2 \lor \bar{x}_1 x_2 = x_1 \nabla x_2$ | [[Exclusive Or\|sum modulo 2]] (*vsota po modulu 2*) |
| $f_7$ | $\overline{x_1 x_2} = x_1 \uparrow x_2$ | [[Sheffer Stroke\|Sheffer symbol, NAND]] (*Shefferjev simbol*) |
| $f_8$ | $x_1 x_2$ | conjunction (*konjunkcija*) |
| $f_9$ | $\bar{x}_1 \bar{x}_2 \lor x_1 x_2 = x_1 \equiv x_2$ | equivalence (*ekvivalenca*) |
| $f_{10}$ | | |
| $f_{11}$ | | implication (*implikacija*) |
| $f_{12}$ – $f_{14}$ | | known, nothing new (*poznamo, nič novega*) |
| $f_{15}$ | $1$ | constant 1 |

**Implication** — the order matters (*vrstni red pomemben*):

$$a \to b = \bar{a} \lor b$$
$$b \to a = a \lor \bar{b}$$

We will avoid implications (*implikacije se bomo izogibali*).

**Sum modulo 2** ($f_6$):

| $x_1$ | $x_2$ | $f_6(x_1, x_2)$ |
|:-:|:-:|:-:|
| 0 | 0 | $0 + 0 = 0$ |
| 0 | 1 | $0 + 1 = 1$ |
| 1 | 0 | $1 + 0 = 1$ |
| 1 | 1 | $1 + 1 = 2$, $2 / 2 = 1$ (remainder 0) $= 0$ |

### Logic symbols (*logični simboli*)

Symbols of the [[Logic Gate|logic gates]]. The circle (bubble) on the output means negation (*negacija*).

| Symbol | Shape | Output |
|---|---|---|
| Sheffer (NAND) | AND gate with a bubble | $x_1 \uparrow x_2$ |
| Peirce (NOR) | OR gate with a bubble | $x_1 \downarrow x_2$ |
| Sum modulo 2 (XOR) | OR gate with an extra curved line on the inputs | $x_1 \nabla x_2$ |
| Equivalence (XNOR) | XOR gate with a bubble | $x_1 \equiv x_2$ |

There are different standards for the symbols (*različni standardi*).

![[Digital Circuits 2 logic symbols.svg]]

### Logic schemes (*logične sheme*)

**Voltage** (*napetost*): 5 V = 1, 0 V = 0.

| Voltage | Logic value |
|---|---|
| 3.5 – 5 V | 1 |
| between? (*vmes?*) | undefined logic value (*nedefinirana logična vrednost*) — at that point it uses a lot of energy |
| 0 – 1.5 V | 0 |

- Disturbances (*motnje*).
- Transitions between states heat up the devices (*prehodi med stanji nam grejejo naprave*) — the faster I switch, the faster it heats up.

### Integrated circuits (*integrirana vezja*)

An integrated circuit contains the logic circuits (*logična vezja*) and the power supply (*napajanje*), connected to the outside through pins (*priključki*):

- GND = 0 V
- VCC = 5 V

![[Digital Circuits 2 integrated circuit.svg|459]]

## Questions

- [ ] 

## Connections

- Course: [[Introduction to Digital Circuits]]
- Previous lecture: [[2026-10-11 - Boolean Algebra - 1]] — switching functions, truth tables, logic symbols
- Related: [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] (normal forms and NAND/NOR in Discrete structures)
- PDNO and PKNO correspond to the [[Disjunctive Normal Form]] and [[Conjunctive Normal Form]] of propositional logic

## Sources

- Handwritten notes: [[Sources/introduction_to_digital_circuits/photoNotes/lectures/lecture 2.pdf|lecture 2]]
- Slides: [[Sources/introduction_to_digital_circuits/ODV.pdf|ODV]] (N. Zimic), 3-28 – 3-44
- Script: [[Sources/introduction_to_digital_circuits/ODV_skripta.pdf|ODV skripta]], ch. 2.1–2.2 (PDF pp. 19–23)
