---
type: "[[Concepts]]"
status: developed
aliases:
  - Resničnostna tabela
  - Pravilnostna tabela
---

# Truth Table

## Definition

A truth table lists the value of a logical formula (or [[Switching Function|switching function]]) for **every** combination of input values. With $n$ variables there are $2^n$ rows.

## Explanation

- The input columns enumerate all combinations of $0$ and $1$, usually in binary counting order: $000, 001, 010, \dots, 111$. Each row is an input vector $\tilde{w}_i$, where $i$ is the row read as a binary number ($\tilde{w}_0 = (0,0,0)$, …, $\tilde{w}_{2^n-1} = (1,\dots,1)$).
- Intermediate columns evaluate subformulas step by step, following the construction tree of the formula.
- The last column is the value of the whole formula (the output).

Uses:

- **Classifying a formula:** all $1$ → [[Tautology|tautology]]; all $0$ → [[Contradiction|contradiction]]; mixed → neutral.
- **Checking equivalence:** two formulas are [[Logical Equivalence|equivalent]] iff their output columns are identical.
- **Describing circuits:** a formula, a truth table and a circuit schematic are equivalent representations of the same switching function; you can always convert a formula into a table.
- Several functions with the same input variables can share one table (one output column each).

## Examples

Disjunction $a \lor b$:

| $a$ | $b$ | $a \lor b$ |
|:-:|:-:|:-:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

$\neg p \lor q$ and $p \Rightarrow q$ have the same column, so $\neg p \lor q \sim p \Rightarrow q$:

| $p$ | $q$ | $\neg p \lor q$ | $p \Rightarrow q$ |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 1 | 1 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 1 | 1 | 1 | 1 |

## Connections

- [[2026-10-05 - Propositional Logic - 1]] — truth tables, tautology, equivalence (Discrete structures)
- [[2026-10-11 - Boolean Algebra - 1]] — truth tables of switching functions (Digital circuits)
- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] — DNO/KNO from a truth table, counterexample for non-equivalence, checking whether an argument is valid (Discrete structures)
- [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]] — PDNO and PKNO are read from the truth table (Digital circuits)
- [[2026-10-22 - Veitch Diagrams, Shannon Expansion and Decomposition - 3]] — a Veitch diagram as a rearranged truth table (Digital circuits)
- [[2026-11-09 - Set Equations, Cartesian Product and Relations - 6]] — the 0/1 table of subsets has $2^n$ rows (Discrete structures)
- [[Disjunctive Normal Form]], [[Conjunctive Normal Form]]
- [[De Morgan's Laws]]

## Sources

- `introduction_to_digital_circuits/ODV_skripta.pdf`, chapter 1
- Gordon J. Pace, *Mathematics of Discrete Structures for Computer Science* (`discrete_structures/`)
