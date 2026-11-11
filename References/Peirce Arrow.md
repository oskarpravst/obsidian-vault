---
type: "[[Concepts]]"
status: developed
aliases:
  - NOR
  - Peircov operator
  - Peirce-Łukasiewiczev veznik
  - Peirce–Łukasiewicz connective
---

# Peirce Arrow

## Definition

The Peirce arrow (NOR, *ne ali*) is negated disjunction:

$$x_1 \downarrow x_2 = \overline{x_1 \lor x_2}$$

It is 1 only when all inputs are 0.

| $x_1$ | $x_2$ | $x_1 \downarrow x_2$ |
|:-:|:-:|:-:|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 0 |

**Logic symbol:** an OR gate with a circle (negation) on the output.

## Explanation

- Named after Charles S. Peirce (the course materials also spell it "Pierce", "Pirce"); in Discrete structures it is the Peirce–Łukasiewicz connective.
- NOR alone is [[Functional Completeness|functionally complete]], like [[Sheffer Stroke|NAND]].
- NOR is **commutative** but **not associative**:
  $$x_1 \downarrow x_2 \downarrow x_3 \neq (x_1 \downarrow x_2) \downarrow x_3 \neq x_1 \downarrow (x_2 \downarrow x_3)$$
- In the list of the 16 functions of two variables, NOR is $f_1$.

## Examples

Expressing the basic operators with NOR only:

- $\bar{x} = x \downarrow x$
- $x \lor y = \overline{x \downarrow y} = (x \downarrow y) \downarrow (x \downarrow y)$
- $xy = \bar{x} \downarrow \bar{y} = (x \downarrow x) \downarrow (y \downarrow y)$ (by [[De Morgan's Laws|De Morgan]])

## Connections

- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] — Peirce–Łukasiewicz connective, $\{\downarrow\}$ is complete (Discrete structures)
- [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]] — $f_1$, logic symbol (Digital circuits)
- [[2026-10-29 - Functionally Complete Systems and Closed Classes - 4]] — Peirce normal form (PPNO) with NOR only (Digital circuits)
- [[Sheffer Stroke]], [[Exclusive Or]], [[Functional Completeness]], [[De Morgan's Laws]]

## Sources

- `introduction_to_digital_circuits/ODV_skripta.pdf`, section 1.3.4
- `introduction_to_digital_circuits/ODV.pdf` (N. Zimic), slides 3-32, 3-34, 4-17
- Wikipedia, "Logical NOR" / "Charles Sanders Peirce" (spelling of the name)
