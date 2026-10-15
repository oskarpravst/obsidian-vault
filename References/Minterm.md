---
type: "[[Concepts]]"
status: developed
aliases:
  - Mintermi
---

# Minterm

## Definition

A minterm of $n$ variables is a conjunction in which **every** variable appears once, negated or not:

$$m_i = x_1^{w_{1i}} x_2^{w_{2i}} \cdots x_n^{w_{ni}}, \qquad i = 0, 1, \dots, 2^n - 1$$

where $x^1 = x$, $x^0 = \bar{x}$, and $(w_{1i}, w_{2i}, \dots, w_{ni})$ are the binary digits of $i$ — the input vector of row $i$ of the truth table.

## Explanation

- $m_i$ equals 1 in **exactly one row** of the truth table — row $i$ — and 0 everywhere else.
- Therefore two different minterms are never 1 together, and together they cover every row:
  $$m_i m_j = 0 \;\; (i \neq j), \qquad \bigvee_{i=0}^{2^n-1} m_i = 1$$
- The negation of a minterm is a [[Maxterm|maxterm]] (by [[De Morgan's Laws|De Morgan]]):
  $$\overline{m_i} = M_{2^n-1-i}$$
- Minterms are the building blocks of the **PDNO** (complete disjunctive normal form): disjunction of the minterms of the rows where $f = 1$.
  $$f(x_1, \dots, x_n) = \bigvee_{i=0}^{2^n-1} m_i f(\tilde{w}_i)$$

## Examples

$n = 4$, $i = 9 = 1001_2$:

$$m_9 = x_1^1 x_2^0 x_3^0 x_4^1 = x_1 \bar{x}_2 \bar{x}_3 x_4$$

PDNO from a truth table with $f = 1$ in rows 1, 2, 4, 7:

$$f = m_1 \lor m_2 \lor m_4 \lor m_7 = \lor(1, 2, 4, 7)$$

## Connections

- [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]] — definition, properties, PDNO (Digital circuits)
- [[Maxterm]], [[Switching Function]], [[Truth Table]], [[De Morgan's Laws]]
- [[Disjunctive Normal Form]] — the same idea for propositional formulas (Discrete structures)

## Sources

- `introduction_to_digital_circuits/ODV_skripta.pdf`, sections 2.2.1, 2.2.3
- `introduction_to_digital_circuits/ODV.pdf` (N. Zimic), PDNO slides (chapter 3)
