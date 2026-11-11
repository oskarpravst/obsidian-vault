---
type: "[[Concepts]]"
status: developed
aliases:
  - XOR
  - Ekskluzivni ali
  - Ekskluzivna disjunkcija
  - Vsota po modulu 2
  - Sum modulo 2
---

# Exclusive Or

## Definition

Exclusive or (XOR) of two inputs is 1 when **exactly one** of them is 1:

$$x_1 \nabla x_2 = x_1 \bar{x}_2 \lor \bar{x}_1 x_2$$

| $x_1$ | $x_2$ | $x_1 \nabla x_2$ |
|:-:|:-:|:-:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

Notation: $\nabla$ or $\oplus$ in Digital circuits, $\veebar$ in Discrete structures.

**Logic symbol:** an OR gate with an extra curved line on the inputs.

## Explanation

- **Sum modulo 2** (*vsota po modulu 2*): add the inputs and keep the remainder after dividing by 2, e.g. $1 + 1 = 2 \equiv 0$.
- **Many inputs:** $x_1 \nabla x_2 \nabla \dots \nabla x_n$ is 1 exactly when an **odd number** of inputs are 1 — regardless of the parentheses (proven by induction in DS 2).
- XOR is commutative and associative.
- For two inputs XOR is the negation of equivalence: $x_1 \nabla x_2 = \overline{x_1 \equiv x_2}$. The script warns that this equality does **not** hold for more inputs.
- In the list of the 16 functions of two variables, XOR is $f_6$.

**Common mistake (Logisim):** a multi-input XOR gate in Logisim by default is 1 only when exactly one input is 1. For the "odd number of ones" behaviour set *Multiple-Input Behavior* to *When an odd number are on*.

## Examples

$1 \nabla 1 \nabla 1 = 1$ (three ones — odd), $1 \nabla 1 \nabla 0 = 0$ (two ones — even).

## Connections

- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] — exclusive disjunction, laws, odd-number claim (Discrete structures)
- [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]] — $f_6$, sum modulo 2, logic symbol (Digital circuits)
- [[2026-10-22 - Veitch Diagrams, Shannon Expansion and Decomposition - 3]] — sum modulo 2 in the Boolean difference (Digital circuits)
- [[2026-10-29 - Functionally Complete Systems and Closed Classes - 4]] — linear functions are written with the sum modulo 2 (Digital circuits)
- [[2026-11-02 - Prenex Normal Form, Sets and Russell's Paradox - 5]] — symmetric difference of sets (Discrete structures)
- [[Sheffer Stroke]], [[Peirce Arrow]], [[Mathematical Induction]]

## Sources

- `introduction_to_digital_circuits/ODV_skripta.pdf`, sections 1.3.6–1.3.7
- `introduction_to_digital_circuits/ODV.pdf` (N. Zimic), slides 3-32, 3-35
