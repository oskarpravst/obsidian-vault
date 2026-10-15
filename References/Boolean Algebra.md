---
type: "[[Concepts]]"
status: developed
aliases:
  - Boolova algebra
---

# Boolean Algebra

## Definition

Boolean algebra is the triple $\{X, O, P\}$:

- $X$ — the set of elements (operands),
- $O$ — the set of basic operators: disjunction ($\lor$) and conjunction ($\cdot$),
- $P$ — the set of postulates (axioms) the operators must satisfy.

The postulates come in pairs — each one and its [[Duality|dual]]:

| | Postulate | Dual |
|---|---|---|
| P1 Closure (*zaprtost*) | $x \lor y \in X$ | $x \cdot y \in X$ |
| P2 Neutral element | $x \lor 0 = x$ | $x \cdot 1 = x$ |
| P3 Commutativity | $x \lor y = y \lor x$ | $xy = yx$ |
| P4 Distributivity | $x \lor yz = (x \lor y)(x \lor z)$ | $x(y \lor z) = xy \lor xz$ |
| P5 Inverse element | $x \lor \bar{x} = 1$ | $x\bar{x} = 0$ |
| P6 Number of elements | $\exists x, y \in X: x \neq y$ | — |

## Explanation

Everything else — idempotence, absorption, associativity, [[De Morgan's Laws|De Morgan's laws]], double negation — is **proven from the postulates**. Negation is not a separate basic operator; it enters through P5 (inverse element).

In digital circuits we use the two-element Boolean algebra $X = \{0, 1\}$. Its functions are [[Switching Function|switching functions]], the basis of all data processing in digital circuits.

Unlike ordinary algebra of numbers:

- $\lor$ also distributes over $\cdot$ (P4), not just the other way round.
- There is no "subtraction": the inverse element $\bar{x}$ gives $1$ under $\lor$ and $0$ under $\cdot$.

The same laws appear in [[Propositional Logic|propositional logic]] with $\lor, \land, \neg$ and logical equivalence $\sim$ instead of $=$.

## Examples

Derived properties (script, 1.1.2):

- Idempotence: $x \lor x = x$, $\;xx = x$
- Absorption: $x \lor xy = x$, $\;x(x \lor y) = x$
- Associativity: $(x \lor y) \lor z = x \lor (y \lor z)$, $\;(xy)z = x(yz)$
- De Morgan: $\overline{x_1 \lor \dots \lor x_n} = \bar{x}_1 \cdots \bar{x}_n$, $\;\overline{x_1 \cdots x_n} = \bar{x}_1 \lor \dots \lor \bar{x}_n$

Proof of idempotence using only postulates (from [[2026-10-11 - Boolean Algebra - 1|ODV 1]]):

$$
\begin{aligned}
a \lor a &= (a \lor a)1 && \text{P2*} \\
&= (a \lor a)(a \lor \bar{a}) && \text{P5} \\
&= a \lor a\bar{a} && \text{P4} \\
&= a \lor 0 && \text{P5*} \\
&= a && \text{P2}
\end{aligned}
$$

## Connections

- [[2026-10-11 - Boolean Algebra - 1]] — postulates, rules, proofs (Digital circuits)
- [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]] — De Morgan used for minterms ↔ maxterms (Digital circuits)
- [[2026-10-05 - Propositional Logic - 1]] — the same laws in propositional logic (Discrete structures)
- [[Duality]], [[De Morgan's Laws]], [[Switching Function]], [[Truth Table]]

## Sources

- `introduction_to_digital_circuits/ODV_skripta.pdf`, sections 1.1–1.1.2
