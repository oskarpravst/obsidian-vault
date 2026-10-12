---
type: "[[Concepts]]"
status: developed
aliases:
  - KNO
  - CNF
  - Konjunktivna normalna oblika
---

# Conjunctive Normal Form

## Definition

- A **literal** is a propositional variable or its negation: $p, \neg p, q, \neg q, \dots$
- A **basic disjunction** (*osnovna disjunkcija*) is a single literal or a disjunction of several literals, e.g. $p \lor q$, $\neg p \lor q \lor r$, $p$.

The **conjunctive normal form** of a formula $I$ is a formula $I_{KNO}$ such that

1. $I_{KNO} \sim I$, and
2. $I_{KNO}$ is a **conjunction of basic disjunctions** (a conjunction with a single term is allowed).

The KNO is **full** (*polna*) if every basic disjunction contains all variables of $I$, each either as itself or as its negation.

## Explanation

**Recipe — from a [[Truth Table|truth table]] to a full KNO:** focus on the rows where the formula is **0**.

- The formula is true iff we are **not** in any of those rows.
- "Not in this row" means at least one variable differs from that row: write a basic disjunction where a variable that is 0 in the row appears as itself and a variable that is 1 appears negated.
- Join these disjunctions with $\land$.

This is the [[Duality|dual]] of the [[Disjunctive Normal Form|DNO]] recipe: rows with 0 instead of 1, and the roles of $\land$ and $\lor$ swapped.

Properties:

- **Every formula has a KNO.** Every formula that is not a [[Tautology|tautology]] has a full KNO (the recipe needs at least one row with 0). A tautology can be written as $p \lor \neg p$.
- **The KNO is not unique.** $p \Rightarrow q \sim \neg p \lor q$ is also a KNO, with a single basic disjunction.
- A KNO can often be simplified with the laws of propositional logic (e.g. distributivity), see the example.

## Examples

Same table as in [[Disjunctive Normal Form#Examples]]: rows with 0 are 1 ($p,q,r = 0,0,0$), 3 ($0,1,0$) and 7 ($1,1,0$).

| row | values | "not in this row" |
|:-:|:-:|:-:|
| 1 | $0, 0, 0$ | $p \lor q \lor r$ |
| 3 | $0, 1, 0$ | $p \lor \neg q \lor r$ |
| 7 | $1, 1, 0$ | $\neg p \lor \neg q \lor r$ |

$$
A \sim (p \lor q \lor r) \land (p \lor \neg q \lor r) \land (\neg p \lor \neg q \lor r)
$$

Simplified in the lecture (factor out $\lor r$, then $q \land \neg q \sim 0$ and $p \land \neg p \sim 0$):

$$
A \sim (p \land \neg q) \lor r \sim (p \Rightarrow q) \Rightarrow r
$$

## Connections

- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] — KNO from a truth table and its simplification (Discrete structures)
- [[Disjunctive Normal Form]]
- [[Functional Completeness]]
- [[Truth Table]]
- [[Duality]]

## Sources

- G. Fijavž, *Diskretne strukture* (FRI, 2015), section 1.6, pp. 24–25
