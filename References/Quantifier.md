---
type: "[[Concepts]]"
status: developed
aliases:
  - Kvantifikator
  - Kvantifikatorji
  - Universal quantifier
  - Existential quantifier
---

# Quantifier

## Definition

The two **quantifiers** (*kvantifikatorja*) of [[Predicate Logic|predicate logic]]:

- $\forall x\, W$ — **universal** (*univerzalni*): $W$ holds for every $x$ in the domain
- $\exists x\, W$ — **existential** (*eksistenčni*): $W$ holds for at least one $x$ in the domain

They turn a formula with a free variable into a proposition with a truth value.

## Explanation

- **Scope** (*doseg*): a quantifier reaches only to the end of the nearest formula. In $\forall x\, P(x) \land Q(x, y)$ only the $x$ in $P(x)$ is bound.
- **Bound and free variables** (*vezane / proste*): a bound variable can no longer be substituted. The same happens to $x$ in $\int_1^2 (x + 5)\,dx$. In atoms all variables are free. Read nested quantifiers from right to left.
- **Precedence:** quantifiers bind as strongly as negation.
- **Substitution** $W(x/a)$ replaces only the free occurrences of $x$.
- **Laws:**

$$\neg\forall x\, W \sim \exists x\, \neg W \qquad \neg\exists x\, W \sim \forall x\, \neg W \quad \text{(De Morgan)}$$

$$\forall x\, \forall y\, W \sim \forall y\, \forall x\, W \qquad \exists x\, \exists y\, W \sim \exists y\, \exists x\, W$$

$$\forall x\,(W \land V) \sim \forall x\, W \land \forall x\, V \qquad \exists x\,(W \lor V) \sim \exists x\, W \lor \exists x\, V$$

- $\exists$ does **not** distribute over $\land$, and $\forall$ does **not** distribute over $\lor$. Different quantifiers cannot be swapped: $\forall x\, \exists y$ is not $\exists y\, \forall x$.

## Examples

**Not distributive** (Discrete structures 4), on $\mathbb{N}$ with $S(x)$ … even, $L(x)$ … odd:

$$\exists x\, S(x) \land \exists x\, L(x) \sim 1 \qquad \text{but} \qquad \exists x\,(S(x) \land L(x)) \sim 0$$

**Scope** (Discrete structures 4): in $\forall x\, \neg\exists x\, \forall z\, P(x, y, z)$ the $\exists x$ already binds $x$, so the outer $\forall x$ binds nothing, and $y$ is free.

**In mathematics** (Calculus): the [[Limit of a Sequence|limit]] definition $\forall\varepsilon > 0\ \exists N\ \forall n \ge N: |a - a_n| < \varepsilon$; changing the order of the quantifiers changes its meaning.

## Connections

- [[2026-10-19 - Valid Arguments and Inference Rules - 3]] — $\forall$ and $\exists$ turn formulas into propositions (Discrete structures)
- [[2026-10-26 - Predicate Formulas, Scope of Quantifiers and Laws of Predicate Logic - 4]] — scope, free and bound variables, laws (Discrete structures)
- [[2026-11-02 - Prenex Normal Form, Sets and Russell's Paradox - 5]] — moving all quantifiers to the front (Discrete structures)
- [[Predicate Logic]], [[De Morgan's Laws]], [[Prenex Normal Form]], [[Limit of a Sequence]]

## Sources

- G. Fijavž, *Diskretne strukture* (FRI, 2015), 2.1–2.4: [[Sources/discrete_structures/ds.pdf#page=41|pp. 41–51]]
