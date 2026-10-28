---
type: "[[Concepts]]"
status: developed
aliases:
  - Enakovrednost
  - Enakovredna izraza
  - Equivalent formulas
---

# Logical Equivalence

## Definition

Formulas $A$ and $B$ are **logically equivalent** (*enakovredna*), written $A \sim B$, if they have the **same truth value for every** assignment of the variables — their [[Truth Table|truth table]] columns are identical.

**Theorem:** $A \sim B$ iff $A \Leftrightarrow B$ is a [[Tautology|tautology]].

## Explanation

- $\sim$ is a **relation between formulas** (a statement *about* two formulas), while $\Leftrightarrow$ is a **connective** that builds a new formula. They are linked by the theorem above.
- $\sim$ is reflexive, symmetric and transitive, so a chain $A \sim A' \sim A''$ gives $A \sim A''$. This is how formulas are simplified step by step with the laws (double negation, commutativity, absorption, distributivity, [[De Morgan's Laws|De Morgan]], $A \Rightarrow B \sim \neg A \lor B$, …).
- **To show $A \not\sim B$**, one row where they differ is enough — a counterexample (*protiprimer*).
- In **predicate logic**, formulas are equivalent if they are equal in **all possible interpretations** (*v vseh možnih interpretacijah*). We cannot check them all, so we use laws, e.g. $\neg \forall x\, W \sim \exists x\, \neg W$.
- In **digital circuits** the same idea appears as equal [[Switching Function|switching functions]]: an equation and a truth table are equivalent representations, and Boolean identities are equivalences.

## Examples

$\neg p \lor q \sim p \Rightarrow q$ (Discrete structures 1):

| $p$ | $q$ | $\neg p \lor q$ | $p \Rightarrow q$ |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 1 | 1 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 1 | 1 | 1 | 1 |

**Not equivalent** (Discrete structures 2): $(p \Rightarrow q) \Rightarrow r$ vs. $p \Rightarrow (q \Rightarrow r)$ — the row $p = q = r = 0$ gives $0$ and $1$.

**Simplifying with laws** (Discrete structures 2):

$$\neg(A \Rightarrow B) \sim \neg(\neg A \lor B) \sim \neg\neg A \land \neg B \sim A \land \neg B$$

## Connections

- [[2026-10-05 - Propositional Logic - 1]] — definition, theorem, properties of $\sim$, the laws (Discrete structures)
- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] — laws 8–12, counterexample, normal forms $A \sim A_{DNO}$ (Discrete structures)
- [[2026-10-26 - Predicate Formulas, Scope of Quantifiers and Laws of Predicate Logic - 4]] — equivalent predicate formulas (Discrete structures)
- [[2026-10-11 - Boolean Algebra - 1]] — equation and table are equivalent representations (Introduction to Digital Circuits)
- [[2026-10-15 - Complete Normal Forms and Logic Functions - 2]] — the connective "equivalence" $x_1 \equiv x_2$ as XNOR (Introduction to Digital Circuits)
- [[Tautology]], [[Contradiction]], [[De Morgan's Laws]], [[Contraposition]], [[Boolean Algebra]]

## Sources

- G. Fijavž, *Diskretne strukture* (FRI, 2015), section 1.4: [[Sources/discrete_structures/ds.pdf#page=17|ds p. 17]]
- [Logical equivalence — Wikipedia](https://en.wikipedia.org/wiki/Logical_equivalence)
