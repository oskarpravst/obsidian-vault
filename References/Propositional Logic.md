---
type: "[[Concepts]]"
status: developed
aliases:
  - Izjavni račun
  - Propositional calculus
---

# Propositional Logic

## Definition

Propositional logic (*izjavni račun*) studies [[Proposition|propositions]] and how they are combined. A proposition (*izjava*) is a sentence that is either true ($1$) or false ($0$), not both. Compound propositions are built from atomic ones with [[Logical Connective|logical connectives]].

## Explanation

**Connectives** and their precedence:

$$\neg \;>\; \land \;>\; \lor \;>\; \Rightarrow \;>\; \Leftrightarrow$$

Implications associate to the left: $A \Rightarrow B \Rightarrow C$ means $(A \Rightarrow B) \Rightarrow C$.

**Formulas** (*izjavni izrazi*) are built recursively from $0$, $1$ and variables with the connectives. Their structure is shown by the **construction tree**: a subformula *occurs* in a formula only if it is a node of its tree.

**Truth values:**

- A [[Truth Table|truth table]] gives the value of a formula for every combination of the variables.
- A [[Tautology|tautology]] is always true, a [[Contradiction|contradiction]] always false.
- $A \sim B$ ([[Logical Equivalence|logically equivalent]]) if they always have the same value. This holds exactly when $A \Leftrightarrow B$ is a tautology.

**Laws** (*zakoni izjavnega računa*): double negation, idempotence, commutativity, associativity, absorption, distributivity, [[De Morgan's Laws]], [[Contraposition|contraposition]], properties of $0$ and $1$, and $A \Rightarrow B \sim \neg A \lor B$. They let us transform formulas without truth tables. They mirror the laws of [[Boolean Algebra|Boolean algebra]].

**Normal forms and completeness:** every truth table can be written as a [[Disjunctive Normal Form|DNF]] or [[Conjunctive Normal Form|CNF]]. Sets such as $\{\neg, \lor\}$, $\{\neg, \land\}$, $\{\uparrow\}$ are [[Functional Completeness|complete]].

**Reasoning** (*sklepanje*): $A_1, \dots, A_n \models B$ (a valid argument) holds exactly when $(A_1 \land \dots \land A_n) \Rightarrow B$ is a tautology. Validity is proved with [[Inference Rule|inference rules]] (MP, MT, DS, HS, …) and auxiliary arguments ([[Conditional Proof|conditional proof]], [[Contradiction|proof by contradiction]], [[Proof by Cases|proof by cases]]).

**Limits:** propositional logic treats every sentence as a single variable and cannot see its internal structure. For "all students …" we need [[Predicate Logic|predicate logic]].

## Examples

**Tautology:** $(p \Rightarrow q) \lor (\neg q \Rightarrow p)$ is $1$ in every row of its truth table.

**Equivalence:** $\neg p \lor q \sim p \Rightarrow q$, because the two columns are identical.

**Valid argument:** $p \Rightarrow q,\ p \lor r,\ q \Rightarrow s,\ r \Rightarrow t,\ \neg s \models t$:

| | | |
|---|---|---|
| 6. | $p \Rightarrow s$ | HS(1, 3) |
| 7. | $\neg p$ | MT(5, 6) |
| 8. | $r$ | DS(2, 7) |
| 9. | $t$ | MP(4, 8) |

**Too weak:** "All CS students can reason logically. Kuzma cannot. So Kuzma is not a CS student." This is valid, but in propositional logic it is three unrelated variables, so the argument cannot be shown valid.

## Connections

- [[2026-10-05 - Propositional Logic - 1]]: propositions, connectives, construction tree, truth tables, laws 1–7 (Discrete structures)
- [[2026-10-11 - Boolean Algebra - 1]]: the same laws in Boolean algebra (Digital circuits)
- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]]: laws 8–12, normal forms, complete sets, start of reasoning (Discrete structures)
- [[2026-10-19 - Valid Arguments and Inference Rules - 3]]: valid arguments, inference rules, auxiliary arguments, start of predicate logic (Discrete structures)
- [[2026-10-22 - Loop Examples, break and switch - 3]] — conjunction `&&` in a loop condition (Programming 1)
- [[2026-10-22 - Veitch Diagrams, Shannon Expansion and Decomposition - 3]] — the same normal forms (Digital circuits)
- [[2026-10-26 - Predicate Formulas, Scope of Quantifiers and Laws of Predicate Logic - 4]] — tautologies carry over to predicate logic (Discrete structures)
- [[Truth Table]], [[Boolean Algebra]], [[De Morgan's Laws]], [[Contraposition]], [[Functional Completeness]], [[Predicate Logic]]

## Sources

- G. Fijavž, *Diskretne strukture* (FRI, 2015), chapter 1, sections 1.1–1.8 (`discrete_structures/ds.pdf`)
- Gordon J. Pace, *Mathematics of Discrete Structures for Computer Science* (`discrete_structures/`)
