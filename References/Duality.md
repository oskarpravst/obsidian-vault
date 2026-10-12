---
type: "[[Concepts]]"
status: developed
aliases:
  - Dualnost
  - Dual function
---

# Duality

## Definition

In [[Boolean Algebra|Boolean algebra]], the **dual** of an expression is obtained by swapping

- conjunction $\leftrightarrow$ disjunction, and
- $0 \leftrightarrow 1$,

while leaving variables and negations unchanged.

For a function, the dual function is

$$f^d(x_1, \dots, x_n) = \overline{f(\bar{x}_1, \dots, \bar{x}_n)}$$

## Explanation

- Every postulate of Boolean algebra comes as a pair: the original (P1–P5) and its dual (P1\*–P5\*). Only P6 (at least two distinct elements) has no dual form.
- **Duality principle:** because the postulates are closed under taking duals, the dual of any rule proven from them is also a valid rule. Proving one half of a pair is enough.
- Negation has no dual: it stays as it is.
- Taking the dual twice gives back the original function: $(f^d)^d = f$.

## Examples

| Original | Dual |
|---|---|
| $x \lor 0 = x$ | $x \cdot 1 = x$ |
| $x \lor \bar{x} = 1$ | $x\bar{x} = 0$ |
| $x \lor yz = (x \lor y)(x \lor z)$ | $x(y \lor z) = xy \lor xz$ |
| $x \lor xy = x$ | $x(x \lor y) = x$ |
| $\overline{x \lor y} = \bar{x}\,\bar{y}$ | $\overline{xy} = \bar{x} \lor \bar{y}$ |

The same pairs appear in propositional logic, e.g. the two [[De Morgan's Laws]] and the two absorption laws.

**Common mistake:** the dual of an expression is not the same as its negation. The negation also negates the variables; the dual does not.

## Connections

- [[2026-10-11 - Boolean Algebra - 1]] — postulates and their duals (Digital circuits)
- [[2026-10-05 - Propositional Logic - 1]] — laws of propositional logic come in dual pairs (Discrete structures)
- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] — the KNO is built by the dual recipe of the DNO (Discrete structures)
- [[Disjunctive Normal Form]], [[Conjunctive Normal Form]]
- [[De Morgan's Laws]]

## Sources

- `introduction_to_digital_circuits/ODV.pdf` (N. Zimic, slides 2-21, 2-22: Dualnost)
- `introduction_to_digital_circuits/ODV_skripta.pdf`, section 1.1.1
