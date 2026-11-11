---
type: "[[Concepts]]"
status: developed
aliases:
  - NAND
  - Shefferjev operator
  - Shefferjev veznik
  - Sheffer connective
---

# Sheffer Stroke

## Definition

The Sheffer stroke (NAND, *ne in*) is negated conjunction:

$$x_1 \uparrow x_2 = \overline{x_1 x_2}$$

It is 0 only when all inputs are 1.

| $x_1$ | $x_2$ | $x_1 \uparrow x_2$ |
|:-:|:-:|:-:|
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

**Logic symbol:** an AND gate with a circle (negation) on the output.

## Explanation

- NAND alone is [[Functional Completeness|functionally complete]]: every [[Switching Function|switching function]] can be built from NAND gates only. Together with [[Peirce Arrow|NOR]] it is the only single binary connective with this property.
- NAND is **commutative** but **not associative**:
  $$x_1 \uparrow x_2 \uparrow x_3 \neq (x_1 \uparrow x_2) \uparrow x_3 \neq x_1 \uparrow (x_2 \uparrow x_3)$$
  so with more inputs, $x_1 \uparrow x_2 \uparrow x_3$ means the 3-input gate $\overline{x_1 x_2 x_3}$, not a chain of 2-input gates.
- In the list of the 16 functions of two variables, NAND is $f_7$.

## Examples

Expressing the basic operators with NAND only:

- $\bar{x} = x \uparrow x$
- $xy = \overline{x \uparrow y} = (x \uparrow y) \uparrow (x \uparrow y)$
- $x \lor y = \bar{x} \uparrow \bar{y} = (x \uparrow x) \uparrow (y \uparrow y)$ (by [[De Morgan's Laws|De Morgan]])

The integrated circuit 74LS00 shown on slide 3-44 contains four 2-input NAND gates.

## Connections

- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] — Sheffer connective, $\{\uparrow\}$ is complete (Discrete structures)
- [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]] — $f_7$, logic symbol (Digital circuits)
- [[2026-10-29 - Functionally Complete Systems and Closed Classes - 4]] — Sheffer normal form (PSNO) with NAND only (Digital circuits)
- [[Peirce Arrow]], [[Exclusive Or]], [[Functional Completeness]], [[De Morgan's Laws]]

## Sources

- `introduction_to_digital_circuits/ODV_skripta.pdf`, section 1.3.5
- `introduction_to_digital_circuits/ODV.pdf` (N. Zimic), slides 3-32, 3-34, 3-44, 4-14
- Wikipedia, "List of 7400-series integrated circuits" (7400 = quad 2-input NAND)
