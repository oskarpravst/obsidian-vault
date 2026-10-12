---
type: "[[Concepts]]"
status: developed
aliases:
  - Poln nabor izjavnih veznikov
  - Polni nabori
  - Complete set of connectives
---

# Functional Completeness

## Definition

A set of connectives $\mathcal{N}$ is a **complete set of connectives** (*poln nabor izjavnih veznikov*) if every propositional formula can be equivalently written using only propositional variables and connectives from $\mathcal{N}$.

## Explanation

**Starting point:** $\{\neg, \land, \lor\}$ is complete, because every formula has a [[Disjunctive Normal Form|DNO]].

**Showing a set is complete — reduction** (*redukcija*): if every connective of a known complete set $\mathcal{Z}$ can be expressed using only connectives from $\mathcal{N}$, then $\mathcal{N}$ is complete too. (Write the formula with $\mathcal{Z}$ first, then replace every occurrence of each connective.)

**Showing a set is *not* complete — find a property that all its connectives keep:**

- **Preserving 0:** if every connective gives 0 when all inputs are 0, then (by induction on the depth) every formula built from them is 0 when all variables are 0. Such a set cannot express $\neg p$.
- **Preserving 1:** the same with 1.
- **Affine** (*afin*): each variable either always or never affects the result. $\neg$ and $\Leftrightarrow$ are affine; $\land$ is not.

Post's criterion: a set is complete **iff** it is not contained in any of five classes — preserving 0, preserving 1, monotone, self-dual, affine (Wikipedia).

**Single connectives:** $\{\uparrow\}$ and $\{\downarrow\}$ are the only complete sets consisting of a single binary connective. A single complete connective must not preserve 0 or 1, which leaves only NAND, NOR, and the two connectives equivalent to $\neg p$ or $\neg q$ — and the latter cannot express $p \land q$.

## Examples

**Complete:**

| Set | Known complete set used | Expressing the missing connective |
|---|---|---|
| $\{\neg, \lor\}$ | $\{\neg, \land, \lor\}$ | $p \land q \sim \neg\neg(p \land q) \sim \neg(\neg p \lor \neg q)$ |
| $\{\neg, \land\}$ | $\{\neg, \land, \lor\}$ | $p \lor q \sim \neg\neg(p \lor q) \sim \neg(\neg p \land \neg q)$ |
| $\{\neg, \Rightarrow\}$ | $\{\neg, \lor\}$ | $p \lor q \sim \neg\neg p \lor q \sim \neg p \Rightarrow q$ |
| $\{0, \Rightarrow\}$ | $\{\neg, \Rightarrow\}$ | $\neg p \sim p \Rightarrow 0$ |
| $\{\uparrow\}$ | $\{\neg, \land\}$ | $\neg p \sim p \uparrow p$, $\;p \land q \sim (p \uparrow q) \uparrow (p \uparrow q)$ |

**Not complete:**

| Set | Reason |
|---|---|
| $\{\land, \lor\}$ | preserves 0 (also preserves 1) |
| $\{\Rightarrow, \Leftrightarrow\}$ | preserves 1 |
| $\{\land, \lor, \Rightarrow, \Leftrightarrow\}$ | preserves 1 |
| $\{\land, \Rightarrow\}$ | preserves 1 |
| $\{\neg, \Leftrightarrow\}$ | affine |

## Connections

- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] — complete sets, reduction, $\{\land, \lor\}$ not complete, $\{\uparrow\}$ complete (Discrete structures)
- [[Disjunctive Normal Form]]
- [[Conjunctive Normal Form]]
- [[De Morgan's Laws]] — used in the reductions
- [[Mathematical Induction]] — proof that a set preserving 0 cannot express $\neg p$

## Sources

- G. Fijavž, *Diskretne strukture* (FRI, 2015), section 1.6, pp. 25–28 (lemma 1.9, theorems 1.10 and 1.11)
- [Functional completeness — Wikipedia](https://en.wikipedia.org/wiki/Functional_completeness) (Post's criterion, affine connectives)
