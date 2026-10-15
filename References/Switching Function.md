---
type: "[[Concepts]]"
status: developed
aliases:
  - Preklopna funkcija
  - Logična funkcija
  - Logic function
---

# Switching Function

## Definition

A switching (logic) function is a function of switching variables — variables that take values from $\{0, 1\}$ — whose value is also $0$ or $1$:

$$f : \{0, 1\}^n \to \{0, 1\}, \qquad (x_1, x_2, \dots, x_n) \mapsto f(x_1, x_2, \dots, x_n)$$

The operators, operands and rules are defined by [[Boolean Algebra|Boolean algebra]].

## Explanation

A switching function can be given in several **equivalent** ways (script, 1.2):

- **Logic expression** (*logični izraz*) — analytically, as an equation, e.g. $f = x_1 x_2 \lor \bar{x}_3$.
- **Logic scheme** (*logična shema*) — graphically, with logic gate symbols.
- **[[Truth Table|Truth table]]** (*pravilnostna tabela*) — all $2^n$ input vectors with the function value for each.
- **Veitch diagram** — used later for minimisation.

**How many functions are there?** A truth table has $2^n$ rows and each row can be 0 or 1, so there are

$$2^{2^n}$$

different functions of $n$ variables: 4 for $n = 1$, 16 for $n = 2$, 256 for $n = 3$.

Every switching function can be written in a complete normal form, read directly from the truth table:

- PDNO — disjunction of the [[Minterm|minterms]] where $f = 1$,
- PKNO — conjunction of the [[Maxterm|maxterms]] where $f = 0$.

## Examples

$f(x_1, x_2, x_3) = x_1 x_2 \lor \bar{x}_3$ as a circuit: $x_1, x_2$ → AND; $x_3$ → NOT; both → OR → $f$.

The 16 functions of two variables include the constants 0 and 1, $x_1$, $x_2$, their negations, conjunction, disjunction, implication, [[Sheffer Stroke|NAND]], [[Peirce Arrow|NOR]], [[Exclusive Or|XOR]] and equivalence (see [[2026-10-15 - Complete Normal Forms and Logic Functions - 2|ODV 2]]).

## Connections

- [[2026-10-11 - Boolean Algebra - 1]] — switching functions, truth tables, logic symbols
- [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]] — PDNO, PKNO, number of functions
- [[Boolean Algebra]], [[Truth Table]], [[Minterm]], [[Maxterm]]
- [[Disjunctive Normal Form]], [[Conjunctive Normal Form]] — the same idea for propositional formulas

## Sources

- `introduction_to_digital_circuits/ODV_skripta.pdf`, sections 1.1, 1.2, 2.2
- `introduction_to_digital_circuits/ODV.pdf` (N. Zimic), slides 3-30 – 3-33
