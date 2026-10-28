---
type: "[[Concepts]]"
status: developed
aliases:
  - Protislovje
  - Unsatisfiable formula
  - Neizpolnljiva formula
---

# Contradiction

## Definition

A **contradiction** (*protislovje*) is a propositional formula that is **false for every** assignment of truth values to its variables: the last column of its [[Truth Table|truth table]] contains only 0s. We write $A \sim 0$.

## Explanation

- A contradiction is a negated [[Tautology|tautology]]: $A$ is a contradiction iff $\neg A$ is a tautology.
- Typical contradictions: $0$, $p \land \neg p$, $\neg p \Leftrightarrow p$.
- In predicate logic the corresponding notion is an **unsatisfiable** formula (*neizpolnljiva*): false in every interpretation, e.g. $\forall x\, P(x) \land \neg \forall x\, P(x) \sim 0$.
- **Proof by contradiction** (*sklep s protislovjem*, RA): to show $A_1, \dots, A_k \models B$, add $\neg B$ to the premises and derive $0$ (a contradiction). This works because

$$(A_1 \land \dots \land A_k) \land \neg B \Rightarrow 0 \;\sim\; (A_1 \land \dots \land A_k) \Rightarrow B$$

- **Do not confuse** with a counterexample (*protiprimer*): a counterexample is one row that shows an argument is invalid; a contradiction is a formula that is never true.

## Examples

**DNO of a contradiction** (Discrete structures 2): $0 \sim p \land \neg p$ (one basic conjunction is enough).

**Proof by contradiction** (Discrete structures 3): from $p \Rightarrow \neg(q \Rightarrow r)$, $s \land q \Rightarrow r$, $s$ and the added $\neg\neg p$, the derivation ends in

$$r \land \neg r \sim 0$$

so $\neg p$ follows.

**In circuits:** a [[Switching Function|switching function]] that is a contradiction is the constant $f = 0$; its output never changes, whatever the inputs.

## Connections

- [[2026-10-05 - Propositional Logic - 1]] — definition, neutral formulas (Discrete structures)
- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] — $A \land \neg A \sim 0$, DNO of a contradiction (Discrete structures)
- [[2026-10-19 - Valid Arguments and Inference Rules - 3]] — proof by contradiction, RA (Discrete structures)
- [[2026-10-26 - Predicate Formulas, Scope of Quantifiers and Laws of Predicate Logic - 4]] — unsatisfiable predicate formulas (Discrete structures)
- [[Tautology]], [[Logical Equivalence]], [[Disjunctive Normal Form]], [[Proof by Contradiction]]

## Sources

- G. Fijavž, *Diskretne strukture* (FRI, 2015), section 1.3.2: [[Sources/discrete_structures/ds.pdf#page=16|ds p. 16]]
- [Contradiction — Wikipedia](https://en.wikipedia.org/wiki/Contradiction)
