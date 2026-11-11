---
type: "[[Concepts]]"
status: developed
aliases:
  - Množica
  - Množice
  - Set theory
  - Teorija množic
---

# Set

## Definition

A **set** (*množica*) is given by its elements. $x \in A$ means $x$ belongs to $A$ (*pripada*). A set can be given by listing its elements or by a predicate formula:

$$A = \{x;\, \varphi(x)\} \qquad x \in A \Leftrightarrow \varphi(x)$$

## Explanation

- **Order and repetition do not matter:** $\{1, 2, 0\} = \{0, 0, 1, 2, 2\}$, because conjunction is commutative and idempotent.
- **Equality and inclusion:**

$$A = B \Leftrightarrow \forall x\,(x \in A \Leftrightarrow x \in B) \qquad A \subseteq B \Leftrightarrow \forall x\,(x \in A \Rightarrow x \in B)$$

$A = B \Leftrightarrow A \subseteq B \land B \subseteq A$, and $A \subset B$ is a proper subset ($A \subseteq B$, $A \ne B$).

- **Operations correspond to connectives:**

| operation | | connective |
|---|---|---|
| intersection (*presek*) | $A \cap B$ | $\land$ |
| union (*unija*) | $A \cup B$ | $\lor$ |
| difference (*razlika*) | $A \setminus B = A \cap B^c$ | $\land\neg$ |
| symmetric difference | $A + B$ | $\veebar$ ([[Exclusive Or\|XOR]]) |
| complement | $A^c = S \setminus A$ | $\neg$ |

- Because of this, all laws of [[Propositional Logic|propositional logic]] carry over: [[De Morgan's Laws|De Morgan]] $(A \cap B)^c = A^c \cup B^c$, absorption $A \cup (A \cap B) = A$, [[Contraposition|contraposition]] $A \subseteq B \sim B^c \subseteq A^c$. A set identity is proved by picking an arbitrary $x$ and comparing the propositions $x \in \dots$ (or with a [[Venn Diagram|Venn diagram]] for intuition).
- **Universal set** $S$: all sets considered lie in it. This makes the complement possible and avoids [[Russell's Paradox|Russell's paradox]] ($R = \{x;\, x \notin x\}$).
- **Disjoint** (*disjunktni*): $A \cap B = \emptyset$.
- **Built from sets:** the [[Power Set|power set]] $\mathcal{P}A = \{B;\, B \subseteq A\}$ with $2^n$ elements, the [[Cartesian Product|Cartesian product]] $A \times B$ of [[Ordered Pair|ordered pairs]], and [[Relation|relations]] $R \subseteq A \times B$.

## Examples

**Empty set:** $\{x;\, x \ne x\} = \emptyset$.

**Power set** (Discrete structures 6): the subsets of $\{1, 2, 3\}$ correspond to the 0/1 rows of a [[Truth Table|truth table]] in 3 variables, so $|\mathcal{P}A| = 2^3 = 8$.

**Set equations** (Discrete structures 6): a system of equations with one unknown set $X$ is rewritten into the [[Disjunctive Normal Form|DNF]]-like form and solved for $X$.

## Connections

- [[2026-11-02 - Prenex Normal Form, Sets and Russell's Paradox - 5]] — giving sets, equality and inclusion, operations, complement, set equalities, Russell's paradox (Discrete structures)
- [[2026-11-09 - Set Equations, Cartesian Product and Relations - 6]] — systems of set equations, power set, Cartesian product, relations (Discrete structures)
- [[Predicate Logic]], [[Propositional Logic]], [[De Morgan's Laws]], [[Venn Diagram]], [[Russell's Paradox]], [[Power Set]], [[Cartesian Product]], [[Relation]]

## Sources

- G. Fijavž, *Diskretne strukture* (FRI, 2015), 3 Sets and 3.1–3.6: [[Sources/discrete_structures/ds.pdf#page=61|pp. 61–79]]
