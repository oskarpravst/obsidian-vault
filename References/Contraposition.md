---
type: "[[Concepts]]"
status: developed
aliases:
  - Kontrapozicija
  - Contrapositive
---

# Contraposition

## Definition

An implication is [[Logical Equivalence|equivalent]] to its contrapositive:

$$A \Rightarrow B \;\sim\; \neg B \Rightarrow \neg A$$

It is law 8 of [[Propositional Logic|propositional logic]] (*kontrapozicija*).

## Explanation

"If $A$, then $B$" says the same as "if not $B$, then not $A$". If $B$ fails, $A$ cannot have been true, because $A$ would have forced $B$.

**Proof with a [[Truth Table|truth table]]:**

| $A$ | $B$ | $\neg A$ | $\neg B$ | $A \Rightarrow B$ | $\neg B \Rightarrow \neg A$ |
|:-:|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 1 | 1 | **1** | **1** |
| 0 | 1 | 1 | 0 | **1** | **1** |
| 1 | 0 | 0 | 1 | **0** | **0** |
| 1 | 1 | 0 | 0 | **1** | **1** |

**Proof with the laws:** using $A \Rightarrow B \sim \neg A \lor B$,

$$\neg B \Rightarrow \neg A \;\sim\; \neg\neg B \lor \neg A \;\sim\; B \lor \neg A \;\sim\; \neg A \lor B \;\sim\; A \Rightarrow B$$

**Common mistake:** only the contrapositive is equivalent. Two similar-looking implications are **not** equivalent to $A \Rightarrow B$:

- the converse $B \Rightarrow A$,
- the inverse $\neg A \Rightarrow \neg B$.

Counterexample: $A = 0$, $B = 1$ gives $A \Rightarrow B = 1$ but $B \Rightarrow A = 0$.

## Examples

**Everyday:** "If it rains, it is cloudy" ($d \Rightarrow o$) means the same as "if it is not cloudy, it does not rain" ($\neg o \Rightarrow \neg d$). It does **not** mean "if it is cloudy, it rains".

**Modus tollens is modus ponens on the contrapositive** (Discrete structures 3):

$$
\begin{array}{lr}
A \Rightarrow B,\ \neg B \models \neg A & \text{MT} \\
\neg B \Rightarrow \neg A,\ \neg B \models \neg A & \text{MP}
\end{array}
$$

**Proof technique:** to prove "if $n^2$ is even, then $n$ is even", it is easier to prove the contrapositive "if $n$ is odd, then $n^2$ is odd".

## Connections

- [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]]: law 8, proof with a truth table (Discrete structures)
- [[2026-10-19 - Valid Arguments and Inference Rules - 3]]: modus tollens via contraposition (Discrete structures)
- [[2026-11-02 - Prenex Normal Form, Sets and Russell's Paradox - 5]] — the same law holds for sets (Discrete structures)
- [[Propositional Logic]], [[Inference Rule]], [[Logical Equivalence]], [[De Morgan's Laws]]

## Sources

- G. Fijavž, *Diskretne strukture* (FRI, 2015), section 1.5, law (8) (`discrete_structures/ds.pdf`)
- [Contraposition — Wikipedia](https://en.wikipedia.org/wiki/Contraposition)
