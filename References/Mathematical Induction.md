---
type: "[[Concepts]]"
status: developed
aliases:
  - Induction
  - Matematična indukcija
  - Indukcija
  - Popolna indukcija
---

# Mathematical Induction

## Definition

**Principle of induction** (*princip indukcije*): let $A \subseteq \mathbb{N}$ satisfy

- $m \in A$,
- $\forall k \in \mathbb{N}: k \in A \implies k + 1 \in A$.

Then $\{m, m+1, \dots\} \subseteq A$. For $m = 1$ this is Peano's axiom P5 (*aksiom o popolni (matematični) indukciji*): such a set contains all natural numbers.

To prove a statement $T(n)$ for all $n \in \mathbb{N}$:

1. **Base case** (*baza indukcije*, BI): prove $T(1)$.
2. **Induction step** (*indukcijski korak*, IK): assume $T(k)$ (the *induction hypothesis*, I.H. — *indukcijska predpostavka*) and derive $T(k+1)$.
3. **Conclusion** (*indukcijski sklep*): $T(n)$ holds for all $n \in \mathbb{N}$.

## Explanation

Think of dominoes: the base case knocks over the first one, and the step guarantees that every falling domino knocks over the next one.

- The step is an implication $T(k) \Rightarrow T(k+1)$; you **use** $T(k)$, you do not prove it. A proof that never uses the I.H. is usually not an induction proof.
- Both parts are needed. Without the base case the step proves nothing (e.g. "$n = n + 1$" passes the step but is never true).
- **Strong induction** (*krepka indukcija*): in the step assume $T(1), T(2), \dots, T(n)$ all hold, not only $T(n)$. Useful when $T(n+1)$ splits into smaller cases of arbitrary size.
- **Induction on the structure** of a formula (its depth): prove the claim for variables and constants, then show that each connective preserves it. Predicate formulas are defined inductively in exactly this way.

## Examples

**Sum of the first $m$ numbers** (Calculus 1):

$$1 + 2 + \dots + m = \frac{m(m+1)}{2}$$

- Base: $L(1) = 1 = D(1)$.
- Step: $L(m+1) = L(m) + (m+1) \overset{\text{I.H.}}{=} \dfrac{m(m+1)}{2} + \dfrac{2(m+1)}{2} = \dfrac{(m+1)(m+2)}{2} = D(m+1)$.

**Exclusive or of $n$ terms** (Discrete structures 2, strong induction): $A_1 \veebar \dots \veebar A_n$ is true exactly when an odd number of the $A_i$ are true. In the step the last connective splits the formula into two parts with at most $n$ terms each, so the I.H. applies to both, and odd + even = odd.

**Sets that preserve 0** (Discrete structures 2, induction on depth): if every connective gives 0 when all inputs are 0, then every formula built from them is 0 when all variables are 0. So $\{\land, \lor\}$ cannot express $\neg p$.

## Connections

- [[2026-10-11 - Numbers - 1]] — principle, procedure, sum $1 + \dots + m$ (Calculus)
- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] — strong induction for $\veebar$, induction on depth (Discrete structures)
- [[2026-10-26 - Predicate Formulas, Scope of Quantifiers and Laws of Predicate Logic - 4]] — predicate formulas are defined inductively (Discrete structures)
- [[2026-10-28 - Limits of Sequences - 4]] — proving a recursive sequence is monotone and bounded (Calculus)
- [[2026-10-29 - Methods and Recursion - 4]] — recurrence relation of the Fibonacci numbers (Programming 1)
- [[Exclusive Or]], [[Functional Completeness]]
- [[Recursion]] — the programming counterpart: a base case and a step that reduces to a smaller case

## Sources

- J. Globevnik, M. Brojan, *Analiza I* (2012), section 1.5 Peano's axioms, P5: [[Sources/calculus/skripta.pdf#page=28|skripta p. 18]]
- Handwritten notes: [[Sources/calculus/photoNotes/lectures/lecture1.pdf|Calculus lecture 1]]
- [Mathematical induction — Wikipedia](https://en.wikipedia.org/wiki/Mathematical_induction)
