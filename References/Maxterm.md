---
type: "[[Concepts]]"
status: developed
aliases:
  - Maksterm
  - Makstermi
---

# Maxterm

## Definition

A maxterm of $n$ variables is a disjunction in which **every** variable appears once, negated or not:

$$M_{2^n-1-i} = x_1^{\overline{w_{1i}}} \lor x_2^{\overline{w_{2i}}} \lor \dots \lor x_n^{\overline{w_{ni}}}, \qquad i = 0, 1, \dots, 2^n - 1$$

where $x^1 = x$, $x^0 = \bar{x}$, and $(w_{1i}, \dots, w_{ni})$ are the binary digits of $i$.

## Explanation

- A maxterm equals 0 in **exactly one row** of the truth table. The maxterm that is 0 in row $i$ has index $2^n - 1 - i$ — **the indices run in the opposite direction** to the rows.
- Relation to [[Minterm|minterms]] (by [[De Morgan's Laws|De Morgan]]):
  $$M_{2^n-1-i} = \overline{m_i}, \qquad M_i = \overline{m_{2^n-1-i}}$$
  $$m_i \lor M_{2^n-1-i} = 1, \qquad m_i M_{2^n-1-i} = 0$$
- Maxterms are the building blocks of the **PKNO** (complete conjunctive normal form): conjunction of the maxterms of the rows where $f = 0$.
  $$f(x_1, \dots, x_n) = \mathop{\&}_{i=0}^{2^n-1} \left( M_{2^n-1-i} \lor f(\tilde{w}_i) \right)$$

**Common mistake:** taking $M_i$ for row $i$. To find the maxterm for row $i$, first compute $2^n - 1 - i$.

## Examples

$M_5$ for $n = 3$: $2^3 - 1 - i = 5 \Rightarrow i = 2 = 010_2$, so

$$M_5 = x_1^{\bar{0}} \lor x_2^{\bar{1}} \lor x_3^{\bar{0}} = x_1 \lor \bar{x}_2 \lor x_3$$

Check: $M_5 = 0$ only for $(x_1, x_2, x_3) = (0, 1, 0)$ — row 2. ✓

**Converting PDNO → PKNO:** $f = \lor(1, 4, 5, 6, 7)$. The missing minterms are $m_0, m_2, m_3$, so $\bar{f} = m_0 \lor m_2 \lor m_3$ and

$$f = \overline{m_0}\,\overline{m_2}\,\overline{m_3} = M_7 M_5 M_4 = \&(7, 5, 4)$$

## Connections

- [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]] — definition, properties, PKNO, conversions (Digital circuits)
- [[2026-10-22 - Veitch Diagrams, Shannon Expansion and Decomposition - 3]] — Veitch diagrams and Shannon expansion (Digital circuits)
- [[2026-10-29 - Functionally Complete Systems and Closed Classes - 4]] — PKNO and the Peirce normal form (Digital circuits)
- [[Minterm]], [[Switching Function]], [[Truth Table]], [[De Morgan's Laws]]
- [[Conjunctive Normal Form]] — the same idea for propositional formulas (Discrete structures)

## Sources

- `introduction_to_digital_circuits/ODV_skripta.pdf`, sections 2.2.2–2.2.4
- `introduction_to_digital_circuits/ODV.pdf` (N. Zimic), PKNO slides (chapter 3)
