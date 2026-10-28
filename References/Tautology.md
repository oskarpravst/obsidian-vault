---
type: "[[Concepts]]"
status: developed
aliases:
  - Tavtologija
  - Valid formula
  - Splošno veljavna formula
---

# Tautology

## Definition

A **tautology** (*tavtologija*) is a propositional formula that is **true for every** assignment of truth values to its variables: the last column of its [[Truth Table|truth table]] contains only 1s. We write $A \sim 1$.

The opposite is a [[Contradiction|contradiction]] (always 0). A formula that is neither is **neutral** (*nevtralna*); most formulas are neutral.

## Explanation

- Typical tautologies: $1$, $p \lor \neg p$, $p \Rightarrow p$, $p \Leftrightarrow p$, $p \Rightarrow (q \Rightarrow p)$, $(p \Rightarrow q) \Rightarrow (\neg q \Rightarrow \neg p)$.
- $A$ is a tautology exactly when $\neg A$ is a contradiction.
- Tautologies are the bridge to the other key ideas of propositional logic:
  - **[[Logical Equivalence|Equivalence]]:** $A \sim B$ iff $A \Leftrightarrow B$ is a tautology.
  - **Valid argument:** $A_1, \dots, A_n \models B$ iff $(A_1 \land \dots \land A_n) \Rightarrow B$ is a tautology.
- To show that a formula is **not** a tautology, one row with value 0 is enough (a counterexample — *protiprimer*).
- In predicate logic the corresponding notion is a **valid** formula (*splošno veljavna*): true in every interpretation, e.g. $\forall x\, P(x) \lor \neg \forall x\, P(x) \sim 1$.

## Examples

$(p \Rightarrow q) \lor (\neg q \Rightarrow p)$ (Discrete structures 1):

| $p$ | $q$ | $p \Rightarrow q$ | $\neg q \Rightarrow p$ | result |
|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 1 | 0 | **1** |
| 0 | 1 | 1 | 1 | **1** |
| 1 | 0 | 0 | 1 | **1** |
| 1 | 1 | 1 | 1 | **1** |

**Checking an argument without a table** (Discrete structures 3): the argument "$d \Rightarrow o$, $d$, so $o$" is valid because

$$((d \Rightarrow o) \land d) \Rightarrow o \sim \dots \sim (d \lor \neg d \lor o) \land (\neg o \lor \neg d \lor o) \sim 1$$

**KNO of a tautology** (Discrete structures 2): $1 \sim p \lor \neg p$.

## Connections

- [[2026-10-05 - Propositional Logic - 1]] — definition, truth tables, $A \sim B$ iff $A \Leftrightarrow B$ is a tautology (Discrete structures)
- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] — laws $A \lor \neg A \sim 1$, normal form of a tautology (Discrete structures)
- [[2026-10-19 - Valid Arguments and Inference Rules - 3]] — valid argument ⇔ tautology (Discrete structures)
- [[2026-10-26 - Predicate Formulas, Scope of Quantifiers and Laws of Predicate Logic - 4]] — valid predicate formulas (Discrete structures)
- [[Contradiction]], [[Logical Equivalence]], [[Truth Table]], [[Propositional Logic]], [[Conjunctive Normal Form]]

## Sources

- G. Fijavž, *Diskretne strukture* (FRI, 2015), section 1.3.2: [[Sources/discrete_structures/ds.pdf#page=16|ds p. 16]]
- [Tautology (logic) — Wikipedia](https://en.wikipedia.org/wiki/Tautology_(logic))
