---
type: "[[Lectures]]"
course: "[[Introduction to Digital Circuits]]"
date: 2026-11-05
week: "5"
---

# 2026-11-05 - Minimisation of Switching Functions

## Main Idea

**Minimisation** (*minimizacija*) looks for the shortest way to write a [[Switching Function|switching function]]. A shorter formula gives a smaller circuit; in the example the PDNO needs 49 pins and the minimal form only 14.

- A **[[Prime Implicant|prime implicant]]** (*glavni vsebovalnik*) is a term for which no smaller term exists. It is found through **adjacency** (*sosednost*): two terms are adjacent if they have the same variables and differ in exactly one negation; then they can be merged and that variable drops out.
- **[[Quine–McCluskey Algorithm|Quine's method]]** (*Quinova metoda minimizacije*) merges adjacent [[Minterm|minterms]] in a table, column by column, until no more neighbours exist. A covering table then picks the needed prime implicants and drops the redundant ones (*redundanca*). The result is the **MDNO** (minimal disjunctive normal form, *minimalna disjunktivna normalna oblika*).
- The **[[Veitch Diagram|Veitch method]]** (*Veitchev postopek minimizacije*) does the same graphically: adjacent minterms are adjacent cells of the diagram, also across the edges.

Both methods were used on the same two functions and give the same MDNO.

## Notes

### Prime implicant (*glavni vsebovalnik*)

For $x_1, x_2, x_3, x_4$:

- $m_0 = \bar{x}_1\bar{x}_2\bar{x}_3\bar{x}_4$ is a **minterm**,
- $\bar{x}_1 x_3$ is a **term** (it does not contain all variables — *ne vsebuje vseh členov*).

A **prime implicant** is a term such that no smaller term exists (*tak, da ne obstaja noben manjši term*).

**Redundancy** (*redundanca*): which prime implicants can be left out (*kakšne glavne vsebovalnike lahko spustimo*).

### Adjacency (*sosednost*)

Two terms are **adjacent** (*sosednja*) if they differ in 1 variable (*če se razlikujeta po 1 spremenljivki*): the same set of variables + they differ in 1 negation (*isti nabor + razlikujeta po 1 negaciji*).

$$
\begin{array}{c}
abd \\ \hline
\bar{a}bd \\
a\bar{b}d \\
ab\bar{d}
\end{array}
$$

A term with 3 variables has 3 neighbours (*3 sosedi*):

$$
\begin{array}{c}
abc \\ \hline
\bar{a}bc \\
a\bar{b}c \\
ab\bar{c}
\end{array}
\qquad\qquad
\begin{array}{c}
a\bar{b}c \\ \hline
\bar{a}\bar{b}c \\
abc \\
a\bar{b}\bar{c}
\end{array}
$$

Merging two adjacent terms, the variable in which they differ drops out (*spremenljivka, v kateri se razlikujeta, odpade*):

$$a\bar{b}c \lor a\bar{b}\bar{c} = a\bar{b}(c \lor \bar{c}) = a\bar{b} \cdot 1 = a\bar{b}$$

A prime implicant has no more neighbours (the terms that remain — *termi, ki ostanejo*).

### Quine's method of minimisation (*Quinova metoda minimizacije*)

#### Example 1

$$f(x_1, x_2, x_3, x_4) = \lor(0, 1, 2, 8, 10, 11, 14, 15)$$

Column $n = 4$ holds the minterms. Every pair of adjacent terms is merged into the next column ($n = 3$, then $n = 2$); a term that was merged gets a ✓. A term that has no neighbour (*nima sosedov*) is a prime implicant (boxed).

| $n = 4$ | $n = 3$ | $n = 2$ |
| --- | --- | --- |
| ✓ $\bar{x}_1\bar{x}_2\bar{x}_3\bar{x}_4$ | **$\bar{x}_1\bar{x}_2\bar{x}_3$** (prime implicant, no neighbour) | **$\bar{x}_2\bar{x}_4$** |
| ✓ $\bar{x}_1\bar{x}_2\bar{x}_3 x_4$ | ✓ $\bar{x}_1\bar{x}_2\bar{x}_4$ | **$x_1 x_3$** |
| ✓ $\bar{x}_1\bar{x}_2 x_3\bar{x}_4$ | ✓ $\bar{x}_2\bar{x}_3\bar{x}_4$ | |
| ✓ $x_1\bar{x}_2\bar{x}_3\bar{x}_4$ | ✓ $\bar{x}_2 x_3\bar{x}_4$ | |
| ✓ $x_1\bar{x}_2 x_3\bar{x}_4$ | ✓ $x_1\bar{x}_2\bar{x}_4$ | |
| ✓ $x_1\bar{x}_2 x_3 x_4$ | ✓ $x_1\bar{x}_2 x_3$ | |
| ✓ $x_1 x_2 x_3\bar{x}_4$ | ✓ $x_1 x_3\bar{x}_4$ | |
| ✓ $x_1 x_2 x_3 x_4$ | ✓ $x_1 x_3 x_4$ | |
| | ✓ $x_1 x_2 x_3$ | |

In column $n = 2$ each term appears twice (the duplicates are crossed out). $\bar{x}_2\bar{x}_4$ and $x_1 x_3$ are not adjacent (*nista soseda*), so they are prime implicants.

**Covering table.** Rows are the prime implicants, columns the minterms of

$$f(x_1, x_2, x_3, x_4) = m_0 \lor m_1 \lor m_2 \lor m_8 \lor m_{10} \lor m_{11} \lor m_{14} \lor m_{15}$$

| | $m_0$ | $m_1$ | $m_2$ | $m_8$ | $m_{10}$ | $m_{11}$ | $m_{14}$ | $m_{15}$ |
| --- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| ✓ $\bar{x}_1\bar{x}_2\bar{x}_3$ | ✓ | ✓ | | | | | | |
| ✓ $\bar{x}_2\bar{x}_4$ | ✓ (redundancy) | | ✓ | ✓ | ✓ | | | |
| $x_1 x_3$ | | | | | ✓ (redundancy) | ✓ | ✓ | ✓ |

$m_0$ and $m_{10}$ are covered twice (*redundanca*).

Which minterms does a prime implicant cover? Fill in the missing variable in both ways:

- $\bar{x}_1\bar{x}_2\bar{x}_3$ — $x_4$ is missing (*manjka*): $\bar{x}_1\bar{x}_2\bar{x}_3\bar{x}_4 = m_0$ or $\bar{x}_1\bar{x}_2\bar{x}_3 x_4 = m_1$
- $\bar{x}_2\bar{x}_4$ — $x_1$ and $x_3$ are missing:
  $x_1\bar{x}_2 x_3\bar{x}_4 = m_{10}$, $\bar{x}_1\bar{x}_2 x_3\bar{x}_4 = m_2$, $x_1\bar{x}_2\bar{x}_3\bar{x}_4 = m_8$, $\bar{x}_1\bar{x}_2\bar{x}_3\bar{x}_4 = m_0$
- $x_1 x_3$ — $x_2$ and $x_4$ are missing:
  $x_1 x_2 x_3 x_4 = m_{15}$, $x_1\bar{x}_2 x_3 x_4 = m_{11}$, $x_1 x_2 x_3\bar{x}_4 = m_{14}$, $x_1\bar{x}_2 x_3\bar{x}_4 = m_{10}$

Adding the prime implicants one by one:

$$\text{1st prime implicant:}\quad \bar{x}_1\bar{x}_2\bar{x}_3 = m_0 \lor m_1$$

$$\text{2nd prime implicant:}\quad \bar{x}_1\bar{x}_2\bar{x}_3 \lor \bar{x}_2\bar{x}_4 = m_0 \lor m_1 \lor m_2 \lor m_8 \lor m_{10}$$

and $x_1 x_3$ adds $m_{11}, m_{14}, m_{15}$. The **minimal disjunctive normal form** (*minimalna disjunktivna normalna oblika*):

$$f(x_1, x_2, x_3, x_4) = \bar{x}_1\bar{x}_2\bar{x}_3 \lor \bar{x}_2\bar{x}_4 \lor x_1 x_3$$

#### PDNO vs. MDNO circuit

![[Digital Circuits 5 PDNO and MDNO circuits.svg]]

- **PDNO:** 8 AND gates with 4 inputs and an OR gate with 8 inputs: 49 pins (*priključkov*).
- **MDNO** (after minimisation — *po minimizaciji*): 14 pins.

$$49 : 14$$

#### Example 2

$$f(x_1, x_2, x_3, x_4) = \lor(1, 4, 6, 7, 8, 9, 10, 11, 15)$$

| $n = 4$ | $n = 3$ | $n = 2$ |
| --- | --- | --- |
| ✓ $\bar{x}_1\bar{x}_2\bar{x}_3 x_4$ | **$\bar{x}_2\bar{x}_3 x_4$** | ~~$\bar{x}_2\bar{x}_3$~~ |
| ✓ $\bar{x}_1 x_2\bar{x}_3\bar{x}_4$ | **$\bar{x}_1 x_2\bar{x}_4$** | **$x_1\bar{x}_2$** |
| ✓ $\bar{x}_1 x_2 x_3\bar{x}_4$ | **$x_2 x_3\bar{x}_4$** → corrected to **$\bar{x}_1 x_2 x_3$** | |
| $\bar{x}_1 x_2 x_3 x_4$ | **$x_2 x_3 x_4$** | |
| ✓ $x_1\bar{x}_2\bar{x}_3\bar{x}_4$ | $x_1\bar{x}_2\bar{x}_3$ | |
| ✓ $x_1\bar{x}_2\bar{x}_3 x_4$ | $x_1\bar{x}_2\bar{x}_4$ | |
| $x_1\bar{x}_2 x_3\bar{x}_4$ | $x_1\bar{x}_2 x_4$ | |
| $x_1\bar{x}_2 x_3 x_4$ | $x_1\bar{x}_2 x_3$ | |
| $x_1 x_2 x_3 x_4$ | **$x_1 x_3 x_4$** | |

(bold = prime implicant, boxed in the notebook)

All prime implicants together:

$$f(x_1, x_2, x_3, x_4) = \bar{x}_2\bar{x}_3 x_4 \lor \bar{x}_1 x_2\bar{x}_4 \lor \bar{x}_1 x_2 x_3 \lor x_2 x_3 x_4 \lor x_1 x_3 x_4 \lor x_1\bar{x}_2$$

**Covering table:**

| | $m_1$ | $m_4$ | $m_6$ | $m_7$ | $m_8$ | $m_9$ | $m_{10}$ | $m_{11}$ | $m_{15}$ |
| --- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| ✓ $\bar{x}_2\bar{x}_3 x_4$ | ✓ | | | | | ✓ | | | |
| ✓ $\bar{x}_1 x_2\bar{x}_4$ | | ✓ | ✓ | | | | | | |
| $\bar{x}_1 x_2 x_3$ → not needed (*ne rabim*) | | | ✓ | ✓ | | | | | |
| ✓ $x_2 x_3 x_4$ | | | | ✓ | | | | | ✓ |
| $x_1 x_3 x_4$ → not needed (*ne rabim*) | | | | | | | | ✓ | ✓ |
| ✓ $x_1\bar{x}_2$ | | | | | ✓ | ✓ | ✓ | ✓ | |

The minterms of each prime implicant:

- $\bar{x}_2\bar{x}_3 x_4$: $x_1\bar{x}_2\bar{x}_3 x_4 = m_9$, $\bar{x}_1\bar{x}_2\bar{x}_3 x_4 = m_1$
- $\bar{x}_1 x_2\bar{x}_4$: $\bar{x}_1 x_2 x_3\bar{x}_4 = m_6$, $\bar{x}_1 x_2\bar{x}_3\bar{x}_4 = m_4$
- $\bar{x}_1 x_2 x_3$: $\bar{x}_1 x_2 x_3 x_4 = m_7$, $\bar{x}_1 x_2 x_3\bar{x}_4 = m_6$
- $x_2 x_3 x_4$: $x_1 x_2 x_3 x_4 = m_{15}$, $\bar{x}_1 x_2 x_3 x_4 = m_7$
- $x_1 x_3 x_4$: $x_1 x_2 x_3 x_4 = m_{15}$, $x_1\bar{x}_2 x_3 x_4 = m_{11}$
- $x_1\bar{x}_2$: $x_1\bar{x}_2 x_3 x_4 = m_{11}$, $x_1\bar{x}_2\bar{x}_3 x_4 = m_9$, $x_1\bar{x}_2 x_3\bar{x}_4 = m_{10}$, $x_1\bar{x}_2\bar{x}_3\bar{x}_4 = m_8$

Are all these prime implicants needed (*ali so to potrebni glavni vsebovalniki?*)? We can get rid of 2 (*2 se lahko znebim*): $\bar{x}_1 x_2 x_3$ and $x_1 x_3 x_4$ (redundancy).

$$\text{MDNO} = x_1\bar{x}_2 \lor \bar{x}_2\bar{x}_3 x_4 \lor \bar{x}_1 x_2\bar{x}_4 \lor x_2 x_3 x_4$$

### Veitch method of minimisation (*Veitchev postopek minimizacije*)

Neighbours are found graphically (*iskanje sosedov grafično*): they are the cells next to each other (*isti, ki so zraven*). What if we are on the edge (*kaj, če smo na robu*)? If we reach the edge, we go around (*če pridemo na rob, gremo okoli*).

![[Digital Circuits 5 Veitch neighbours.svg]]

Neighbours of $m_{11} = x_1\bar{x}_2 x_3 x_4$:

$$\bar{x}_1\bar{x}_2 x_3 x_4 = m_3 \qquad x_1 x_2 x_3 x_4 = m_{15} \qquad x_1\bar{x}_2\bar{x}_3 x_4 = m_9 \qquad x_1\bar{x}_2 x_3\bar{x}_4 = m_{10}$$

Neighbours of $m_4 = \bar{x}_1 x_2\bar{x}_3\bar{x}_4$, partly around the edge:

$$x_1 x_2\bar{x}_3\bar{x}_4 = m_{12} \qquad \bar{x}_1\bar{x}_2\bar{x}_3\bar{x}_4 = m_0 \qquad \bar{x}_1 x_2 x_3\bar{x}_4 = m_6 \qquad \bar{x}_1 x_2\bar{x}_3 x_4 = m_5$$

Neighbours of the term $\bar{x}_1 x_3 x_4$ (two cells):

$$x_1 x_3 x_4 \qquad \bar{x}_1\bar{x}_3 x_4 \qquad \bar{x}_1 x_3\bar{x}_4$$

The same for a term of two variables, $\bar{x}_1\bar{x}_2$ (four cells):

![[Digital Circuits 5 Veitch term neighbours.svg]]

$$\bar{x}_1\bar{x}_2: \qquad x_1\bar{x}_2 \qquad \bar{x}_1 x_2$$

#### 5 variables

The second half of the diagram is covered by $x_5$. Besides the cells next to it, a cell also has a neighbour in the **same position** in the other half (*istoležno*), e.g. $m_{14}$ and $m_{15}$, $m_0$ and $m_1$.

![[Digital Circuits 5 Veitch 5 variables neighbours.svg]]

Neighbours of $m_{14} = \bar{x}_1 x_2 x_3 x_4\bar{x}_5$:

$$
\begin{aligned}
x_1 x_2 x_3 x_4\bar{x}_5 &= m_{30} \\
\bar{x}_1\bar{x}_2 x_3 x_4\bar{x}_5 &= m_6 \\
\bar{x}_1 x_2\bar{x}_3 x_4\bar{x}_5 &= m_{10} \\
\bar{x}_1 x_2 x_3\bar{x}_4\bar{x}_5 &= m_{12} \\
\bar{x}_1 x_2 x_3 x_4 x_5 &= m_{15}
\end{aligned}
$$

Neighbours of $m_0 = \bar{x}_1\bar{x}_2\bar{x}_3\bar{x}_4\bar{x}_5$:

$$
\begin{aligned}
x_1\bar{x}_2\bar{x}_3\bar{x}_4\bar{x}_5 &= m_{16} \\
\bar{x}_1 x_2\bar{x}_3\bar{x}_4\bar{x}_5 &= m_8 \\
\bar{x}_1\bar{x}_2 x_3\bar{x}_4\bar{x}_5 &= m_4 \\
\bar{x}_1\bar{x}_2\bar{x}_3 x_4\bar{x}_5 &= m_2 \\
\bar{x}_1\bar{x}_2\bar{x}_3\bar{x}_4 x_5 &= m_1
\end{aligned}
$$

Neighbours of a term of two cells, $m_{14} \lor m_{10} = \bar{x}_1 x_2 x_4\bar{x}_5$:

$$
\begin{aligned}
x_1 x_2 x_4\bar{x}_5 &= m_{26} \lor m_{30} \\
\bar{x}_1\bar{x}_2 x_4\bar{x}_5 &= m_6 \lor m_2 \\
\bar{x}_1 x_2\bar{x}_4\bar{x}_5 &= m_{12} \lor m_8 \\
\bar{x}_1 x_2 x_4 x_5 &= m_{15} \lor m_{11}
\end{aligned}
$$

A term of four cells, $m_{29} \lor m_{31} \lor m_{23} \lor m_{21} = x_1 x_3 x_5$:

$$
\begin{aligned}
\bar{x}_1 x_3 x_5 &= m_{13} \lor m_{15} \lor m_7 \lor m_5 \\
x_1\bar{x}_3 x_5 &= m_{25} \lor m_{27} \lor m_{19} \lor m_{17} \\
x_1 x_3\bar{x}_5 &= m_{28} \lor m_{30} \lor m_{22} \lor m_{20}
\end{aligned}
$$

#### 6 variables

![[Digital Circuits 5 Veitch 6 variables.svg]]

Neighbours of $\bar{x}_1 x_2\bar{x}_5 x_6$:

$$x_1 x_2\bar{x}_5 x_6 \qquad \bar{x}_1\bar{x}_2\bar{x}_5 x_6 \qquad \bar{x}_1 x_2 x_5 x_6 \qquad \bar{x}_1 x_2\bar{x}_5\bar{x}_6$$

A minterm of 6 variables has 6 neighbours:

$$x_1 x_2 x_3\bar{x}_4 x_5\bar{x}_6 = m_{58}$$

$$
\begin{aligned}
&\bar{x}_1 x_2 x_3\bar{x}_4 x_5\bar{x}_6 \\
&x_1\bar{x}_2 x_3\bar{x}_4 x_5\bar{x}_6 \\
&x_1 x_2\bar{x}_3\bar{x}_4 x_5\bar{x}_6 \\
&x_1 x_2 x_3 x_4 x_5\bar{x}_6 \\
&x_1 x_2 x_3\bar{x}_4\bar{x}_5\bar{x}_6 \\
&x_1 x_2 x_3\bar{x}_4 x_5 x_6
\end{aligned}
$$

#### Minimisation with the Veitch diagram

The two functions from Quine's method, now minimised graphically: enter the 1s, cover them with as large groups of neighbours as possible, and read off the terms.

![[Digital Circuits 5 Veitch minimisation examples.svg]]

$$f(x_1, x_2, x_3, x_4) = \lor(0, 1, 2, 8, 10, 11, 14, 15) = \bar{x}_1\bar{x}_2\bar{x}_3 \lor \bar{x}_2\bar{x}_4 \lor x_1 x_3 \quad \text{(MDNO)}$$

$$f(x_1, x_2, x_3, x_4) = \lor(1, 4, 6, 7, 8, 9, 10, 11, 15) = x_1\bar{x}_2 \lor \bar{x}_2\bar{x}_3 x_4 \lor x_2 x_3 x_4 \lor \bar{x}_1 x_2\bar{x}_4$$

Both results are the same as with Quine's method.

## Questions

- [ ] How are the variables placed in the 6-variable Veitch diagram (which halves do $x_5$ and $x_6$ cover, and is the neighbour in the other half in the same or in the mirrored position)?
- [ ] When are there several different MDNOs of the same function, and how do we choose between them?

## Connections

- Course: [[Introduction to Digital Circuits]]
- Previous lecture: [[2026-10-29 - Functionally Complete Systems and Closed Classes - 4]]
- [[2026-10-22 - Veitch Diagrams, Shannon Expansion and Decomposition - 3]]: the layout of the Veitch diagram for 4, 5 and 6 variables
- [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]]: the PDNO, the starting point of minimisation
- [[Boolean Algebra]]: $a\bar{b}c \lor a\bar{b}\bar{c} = a\bar{b}$ uses distributivity and $c \lor \bar{c} = 1$
- [[Prime Implicant]], [[Quine–McCluskey Algorithm]], [[Veitch Diagram]], [[Minterm]], [[Disjunctive Normal Form]], [[Switching Function]]

## Sources

- Handwritten notes: [[Sources/introduction_to_digital_circuits/photoNotes/lectures/lecture 5.pdf|lecture 5]]
- Slides: [[Sources/introduction_to_digital_circuits/ODV.pdf#page=54|ODV]] (N. Zimic), 5-1 – 5-14 (the same two examples)
- Script: [[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=33|ODV skripta]], 5.1 minimal forms and adjacency, 5.2 Veitch method (PDF pp. 33–36), 6.2 Quine's method, Zgled 19 ([[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=42|PDF pp. 42–43]])
