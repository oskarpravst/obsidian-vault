---
type: "[[Concepts]]"
status: developed
aliases:
  - De Morganova zakona
  - De Morganov izrek
  - De Morgan's theorem
---

# De Morgan's Laws

## Definition

The negation of a conjunction is the disjunction of the negations, and the negation of a disjunction is the conjunction of the negations.

In [[Propositional Logic|propositional logic]]:

$$\neg(A \land B) \sim \neg A \lor \neg B$$
$$\neg(A \lor B) \sim \neg A \land \neg B$$

In [[Boolean Algebra|Boolean algebra]] notation:

$$\overline{xy} = \bar{x} \lor \bar{y}$$
$$\overline{x \lor y} = \bar{x}\,\bar{y}$$

## Explanation

Pushing a negation inside a bracket **negates every operand and swaps the operator**: conjunction becomes disjunction and vice versa.

The two laws are [[Duality|duals]] of each other: swapping $\land \leftrightarrow \lor$ in one gives the other.

They generalise to any number of variables:

$$\overline{x_1 \lor x_2 \lor \dots \lor x_n} = \bar{x}_1\,\bar{x}_2 \cdots \bar{x}_n$$
$$\overline{x_1 x_2 \cdots x_n} = \bar{x}_1 \lor \bar{x}_2 \lor \dots \lor \bar{x}_n$$

## Examples

Check of $\neg(A \land B) \sim \neg A \lor \neg B$ with a [[Truth Table|truth table]]:

| $A$ | $B$ | $A \land B$ | $\neg(A \land B)$ | $\neg A$ | $\neg B$ | $\neg A \lor \neg B$ |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 1 | 1 | 1 | 1 |
| 0 | 1 | 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 | 1 | 1 |
| 1 | 1 | 1 | 0 | 0 | 0 | 0 |

The 4th and 7th columns are identical, so the formulas are [[Logical Equivalence|equivalent]].

In everyday language: "not (rain and cold)" means "not rain **or** not cold".

**Common mistake:** $\overline{xy} \neq \bar{x}\,\bar{y}$. Negating the operands alone is not enough; the operator must also be swapped.

## Connections

- [[2026-10-05 - Propositional Logic - 1]] — law 7 of propositional logic (Discrete structures)
- [[2026-10-11 - Boolean Algebra - 1]] — rule 4 of Boolean algebra (Digital circuits)
- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] — used in the proof of law 11b and in showing $\{\neg, \lor\}$ and $\{\neg, \land\}$ are complete (Discrete structures)
- [[Functional Completeness]]
- [[Duality]]
- [[Truth Table]]

## Sources

- `introduction_to_digital_circuits/ODV_skripta.pdf`, section 1.1.2 (De Morgan's rule for $n$ variables)
- Gordon J. Pace, *Mathematics of Discrete Structures for Computer Science* (`discrete_structures/`)
