---
type: "[[Concepts]]"
status: developed
aliases:
  - Veitchev diagram
  - Karnaugh map
  - Veitch method
  - Veitchev postopek
---

# Veitch Diagram

## Definition

A **Veitch diagram** (*Veitchev diagram*) of a [[Switching Function|switching function]] of $n$ variables is a grid of $2^n$ cells, one for each [[Minterm|minterm]]. **Each variable covers half of the cells.** The cell where the covered regions meet is the minterm, and we write a 1 into the cells where $f = 1$.

## Explanation

- The cell index comes from the [[Truth Table|truth table]] with $x_1$ as the most significant bit, e.g. $\bar{x}_1 x_2 \bar{x}_3 \bar{x}_4 = 0100_2 = m_4$.
- The cells are arranged so that **neighbouring cells differ in exactly one variable**. This holds **across the edges too**: the left edge touches the right, and the top touches the bottom.
- **Veitch method of minimisation:** cover all 1s with as large groups of neighbours as possible ($2, 4, 8, \dots$ cells). Each group is one term without the variables that change inside it; the groups are the [[Prime Implicant|prime implicants]]. Joining the needed groups with $\lor$ gives a minimal DNF (MDNO). It is the graphical version of the [[Quine–McCluskey Algorithm|Quine method]] and gives the same result.
- **Sizes:** 1–4 variables directly. For 5 variables the 4-variable diagram is doubled and the new half is covered by $x_5$. For 6 variables it is doubled again ($8 \times 8$).
- The same tool is often called a **Karnaugh map** (Karnaugh's refinement of Veitch's diagram, with Gray-code ordering).

## Examples

**Reading a function** (Digital circuits 3): $f = \bar{x}_1 \lor x_2 x_4 \lor x_3 x_4$. $\bar{x}_1$ is the right half, $x_2 x_4$ the second row, and $x_3 x_4$ the intersection of the $x_3$ columns with the $x_4$ rows.

**Neighbours** (Digital circuits 5): the neighbours of $m_{11} = x_1\bar{x}_2 x_3 x_4$ are $m_3, m_{15}, m_9, m_{10}$, one variable flipped each.

**Minimisation** (Digital circuits 5):

$$f = \lor(0, 1, 2, 8, 10, 11, 14, 15) = \bar{x}_1\bar{x}_2\bar{x}_3 \lor \bar{x}_2\bar{x}_4 \lor x_1 x_3$$

## Connections

- [[2026-10-22 - Veitch Diagrams, Shannon Expansion and Decomposition - 3]] — the diagram for 1–6 variables, reading functions (Digital circuits)
- [[2026-11-05 - Minimisation of Switching Functions - 5]] — adjacency across edges, Veitch method of minimisation (Digital circuits)
- [[Venn Diagram]], [[Minterm]], [[Switching Function]], [[Prime Implicant]], [[Quine–McCluskey Algorithm]], [[Disjunctive Normal Form]], [[Truth Table]]

## Sources

- Script: [[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=25|ODV skripta]], 3.1 Veitch diagram (PDF p. 25); 5.1–5.2 adjacency and Veitch method ([[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=33|PDF pp. 33–36]])
- Slides: [[Sources/introduction_to_digital_circuits/ODV.pdf#page=34|ODV]] (N. Zimic), 3-45 – 3-64, 5-1 – 5-14
- [Karnaugh map — Wikipedia](https://en.wikipedia.org/wiki/Karnaugh_map)
