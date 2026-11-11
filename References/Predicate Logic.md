---
type: "[[Concepts]]"
status: developed
aliases:
  - Predikatni račun
  - First-order logic
---

# Predicate Logic

## Definition

**Predicate logic** (*predikatni račun*) extends [[Propositional Logic|propositional logic]] with the internal structure of propositions. Its building blocks are:

- a **domain of discourse** (*področje pogovora*): a non-empty set of things we talk about
- **predicates** (*predikati*): logic functions with arguments from the domain, e.g. $p(x)$ … "$x$ is bald", $D(x, y)$ … "$x$ divides $y$"
- the **[[Quantifier|quantifiers]]** $\forall$ and $\exists$

## Explanation

- **Why we need it:** "All CS students can reason logically. Kuzma can't. So Kuzma is not a CS student." In propositional logic each sentence is a separate variable, so the argument looks invalid. Predicate logic sees the shared predicate.
- A predicate becomes a proposition by **plugging in a constant** ($p(\text{Gašper})$) or by **binding the variable** with a quantifier ($\forall x\, p(x)$).
- **Interpretation** (*interpretacija*): a domain $D$, a meaning (0/1 function on $D$) for every predicate, and values for the free variables.
- **Equivalent formulas** (*enakovredne*) have the same value in **all** interpretations. A formula true in every interpretation is **valid** (*splošno veljavna*); one false in every interpretation is **unsatisfiable** (*neizpolnljiva*, see [[Contradiction]]).
- **Laws:** all propositional laws still hold, plus [[De Morgan's Laws|De Morgan]] for quantifiers, swapping quantifiers of the same kind, and distributivity of $\forall$ over $\land$ and of $\exists$ over $\lor$.
- **[[Prenex Normal Form|Prenex normal form]]** (PNO): every formula is equivalent to one with all quantifiers at the beginning.
- **Reasoning** uses the inference rules of propositional logic plus rules for quantifiers (e.g. ES = existential specification, US = universal specification).
- **Sets** are built on it: $A = \{x;\, \varphi(x)\}$ means $x \in A \Leftrightarrow \varphi(x)$, and a binary [[Relation|relation]] is the set view of a two-place predicate.

## Examples

**Formalisation** (Discrete structures 3), domain: people, $p(x)$ … politician, $N(x)$ … dishonest:

| sentence | formula |
|---|---|
| Some politicians are dishonest. | $\exists x\,(p(x) \land N(x))$ |
| No politician is dishonest. | $\neg\exists x\,(p(x) \land N(x))$ |
| All politicians are dishonest. | $\forall x\,(p(x) \Rightarrow N(x))$ |
| All politicians are honest. | $\forall x\,(p(x) \Rightarrow \neg N(x))$ |

Typically $\exists$ goes with $\land$ and $\forall$ goes with $\Rightarrow$.

## Connections

- [[2026-10-19 - Valid Arguments and Inference Rules - 3]] — domain, predicates, quantifiers, formalisation (Discrete structures)
- [[2026-10-26 - Predicate Formulas, Scope of Quantifiers and Laws of Predicate Logic - 4]] — scope, free and bound variables, interpretation, laws (Discrete structures)
- [[2026-11-02 - Prenex Normal Form, Sets and Russell's Paradox - 5]] — prenex normal form, reasoning, sets defined by formulas (Discrete structures)
- [[2026-11-09 - Set Equations, Cartesian Product and Relations - 6]] — relations as two-place predicates (Discrete structures)
- [[Propositional Logic]], [[Quantifier]], [[Tautology]], [[Contradiction]], [[De Morgan's Laws]], [[Prenex Normal Form]], [[Set]]

## Sources

- G. Fijavž, *Diskretne strukture* (FRI, 2015), 2.1–2.6: [[Sources/discrete_structures/ds.pdf#page=41|pp. 41–59]]
