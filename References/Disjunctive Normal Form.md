---
type: "[[Concepts]]"
status: developed
aliases:
  - DNO
  - DNF
  - Disjunktivna normalna oblika
---

# Disjunctive Normal Form

## Definition

- A **literal** is a propositional variable or its negation: $p, \neg p, q, \neg q, \dots$
- A **basic conjunction** (*osnovna konjunkcija*) is a single literal or a conjunction of several literals, e.g. $p \land q$, $\neg p \land q \land r$, $\neg q$.

The **disjunctive normal form** of a formula $I$ is a formula $I_{DNO}$ such that

1. $I_{DNO} \sim I$, and
2. $I_{DNO}$ is a **disjunction of basic conjunctions** (a disjunction with a single term is allowed).

The DNO is **full** (*polna*) if every basic conjunction contains all variables of $I$, each either as itself or as its negation.

## Explanation

**Recipe — from a [[Truth Table|truth table]] to a full DNO:** focus on the rows where the formula is **1**.

- For each such row write one basic conjunction: a variable that is 1 in that row appears as itself, a variable that is 0 appears negated.
- Join these conjunctions with $\lor$.

Why it works: the formula is true iff we are in one of those rows, and each basic conjunction is true in exactly its own row.

Properties:

- **Every formula has a DNO.** Every formula that is not a [[Contradiction|contradiction]] has a full DNO (the recipe needs at least one row with 1). A contradiction can be written as $p \land \neg p$.
- **The DNO is not unique.** $p \Rightarrow q \sim \neg p \lor q$ is a DNO (with two very short basic conjunctions), and so is the full DNO $(\neg p \land \neg q) \lor (\neg p \land q) \lor (p \land q)$.
- Consequence: every formula can be written using only $\neg, \land, \lor$, so $\{\neg, \land, \lor\}$ is a [[Functional Completeness|complete set of connectives]].
- The [[Duality|dual]] construction (rows with 0, disjunctions joined by $\land$) gives the [[Conjunctive Normal Form]].

## Examples

| $p$ | $q$ | $r$ | $A$ |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | **1** |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | **1** |
| 1 | 0 | 0 | **1** |
| 1 | 0 | 1 | **1** |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | **1** |

Rows with 1: 2, 4, 5, 6, 8. Full DNO:

$$
A \sim (\neg p \land \neg q \land r) \lor (\neg p \land q \land r) \lor (p \land \neg q \land \neg r) \lor (p \land \neg q \land r) \lor (p \land q \land r)
$$

## Connections

- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] — DNO from a truth table (Discrete structures)
- [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]] — PDNO corresponds to the DNF of propositional logic (Digital circuits)
- [[2026-11-05 - Minimisation of Switching Functions - 5]] — minimising a DNF (Digital circuits)
- [[2026-11-09 - Set Equations, Cartesian Product and Relations - 6]] — DNF of a set equation, multiplying out each with each (Discrete structures)
- [[Conjunctive Normal Form]]
- [[Functional Completeness]]
- [[Truth Table]]
- [[Duality]]

## Sources

- G. Fijavž, *Diskretne strukture* (FRI, 2015), section 1.6, pp. 23–25
