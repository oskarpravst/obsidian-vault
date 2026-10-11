---
type: "[[Lectures]]"
course: "[[Discrete structures]]"
date: 2026-10-05
week: "1"
---

# 2026-10-05 - Propositional Logic

## Main Idea

Introduction to [[Propositional Logic|propositional logic]] (*izjavni račun*): what a proposition is, how compound propositions are built with logical connectives, how to read a formula through its construction tree, how to evaluate it with a [[Truth Table|truth table]], and the basic laws of logical equivalence.

## Notes

### DS 1.1 — Propositions

A [[Proposition|proposition]] (*izjava*) is a sentence to which we can assign a truth value.

- **Example 1:** *"This sentence is not true."* (*Ta stavek ni resničen.*)
  → It has no truth value → **not a proposition**.
- **Example 2:** *"The Moon is shining outside."* (*Zunaj sveti Luna.*)
  → Its truth value depends on place/time.

| By content (*po vsebini*) | By form (*po obliki*) |
|---|---|
| True (*resnične*, $1$) | Atomic (*osnovne*) |
| False (*neresnične*, $0$) | Compound (*sestavljene*) |

#### Logical connectives (*izjavni vezniki*)

[[Logical Connective|Logical connectives]] are used to build **compound propositions**. They can be:

- Unary (*enomestni*)
- Binary (*dvomestni*)
- Ternary (*tromestni*)

| Connective | Symbol |
|---|---|
| Negation (*negacija*) | $\neg$ |
| Conjunction (*konjunkcija*) | $\land$ |
| Disjunction (*disjunkcija*) | $\lor$ |
| Implication (*implikacija*) | $\Rightarrow$ |
| Equivalence (*ekvivalenca*) | $\Leftrightarrow$ |

- Conjunction: $A \land B \sim B \land A$ — **commutativity**
- Implication: $A \Rightarrow B$, where $A$ is the **antecedent** and $B$ is the **consequent**.

#### Convention for omitting parentheses (*dogovor o dopuščanju oklepajev*)

Precedence of connectives:

$$\neg \;>\; \land \;>\; \lor \;>\; \Rightarrow \;>\; \Leftrightarrow$$

> **Watch out!** Implications associate to the left:
> $A \Rightarrow B \Rightarrow C \Rightarrow D$ means $((A \Rightarrow B) \Rightarrow C) \Rightarrow D$.

#### Propositional formulas (*izjavni izrazi*)

1. $0$ and $1$ are propositional formulas.
2. Propositional variables are propositional formulas.
3. If $A$ is a propositional formula, then $\neg A$ is also a propositional formula.
4. If $A$ and $B$ are propositional formulas, then $A \land B$, $A \lor B$, $A \Rightarrow B$, $A \Leftrightarrow B$ are propositional formulas.

#### Construction tree (*konstrukcijsko drevo*)

**Example 1:** $p \land q$

```
p     q
 \   /
 p ∧ q
```

**Example 2:** $\neg p \Rightarrow p$

```
p
|
¬p      p
  \    /
 ¬p ⇒ p
```

**Example 3:** $q \land (p \Rightarrow \neg r)$

```
q        p        r
|        |        |
|        |       ¬r
|         \      /
|        (p ⇒ ¬r)
 \        /
q ∧ (p ⇒ ¬r)
```

- **Occurrence** (*nastopanje*): $I$ occurs in $J$ if $I$ can be found as a node in the construction tree of $J$.
- **Depth** (*globina*, here $3$): the longest path from top to bottom.
- **Length** (*dolžina*, here $6$): the number of nodes.

### DS 1.2 — Truth tables (*resničnostna tabela*)

**Example 1:** $p \Rightarrow q \Rightarrow r$

By convention, this is $(p \Rightarrow q) \Rightarrow r$:

```
p     q
 \   /
 p ⇒ q     r
     \    /
 p ⇒ q ⇒ r
```

> **Watch out!** $q \Rightarrow r$ **does not occur** in this formula.
> To check whether a subformula occurs, check the construction tree.

**Example 2:** $q \land (p \Rightarrow \neg r)$

| $p$ | $q$ | $r$ | $\neg r$ | $p \Rightarrow \neg r$ | $q \land (p \Rightarrow \neg r)$ |
|:-:|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 1 | 1 | 0 |
| 0 | 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 | 1 | 1 |
| 0 | 1 | 1 | 0 | 1 | 1 |
| 1 | 0 | 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 | 0 | 0 |
| 1 | 1 | 0 | 1 | 1 | 1 |
| 1 | 1 | 1 | 0 | 0 | 0 |

**Example 3:** $(p \Rightarrow q) \lor (\neg q \Rightarrow p)$

| $p$ | $q$ | $p \Rightarrow q$ | $\neg q$ | $\neg q \Rightarrow p$ | $(p \Rightarrow q) \lor (\neg q \Rightarrow p)$ |
|:-:|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 1 | 1 | 0 | **1** |
| 0 | 1 | 1 | 0 | 1 | **1** |
| 1 | 0 | 0 | 1 | 1 | **1** |
| 1 | 1 | 1 | 0 | 1 | **1** |

→ **[[Tautology]]** (*tavtologija*): always true.

**Example 4:** $p \Rightarrow (q \Rightarrow p)$

| $p$ | $q$ | $q \Rightarrow p$ | $p \Rightarrow (q \Rightarrow p)$ |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 1 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 1 | 1 |

→ Tautology.

- **[[Contradiction]]** (*protislovje*) — a negated tautology (always false).
- **Neutral** (*nevtralno*) — neither a tautology nor a contradiction.

**Example 5:** $\neg p \lor q$

| $p$ | $q$ | $\neg p \lor q$ | $p \Rightarrow q$ |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 1 | 1 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 1 | 1 | 1 | 1 |

The two columns are identical → the formulas are **[[Logical Equivalence|logically equivalent]]** (*enakovredna*): $A \sim B$.

#### Theorem (*izrek*)

Propositional formulas $A$ and $B$ are equivalent if and only if the formula $A \Leftrightarrow B$ is a tautology.

$$A \sim B \quad \text{iff} \quad A \Leftrightarrow B \text{ is a tautology.}$$

**Proof:**

$A \sim B$
… $A$ and $B$ "always" have the same truth value
… $A \Leftrightarrow B$ is "always" true
… $A \Leftrightarrow B$ is a tautology. $\blacksquare$

#### Properties of $\sim$ (*zveze*)

- $A \sim A$ (reflexivity)
- If $A \sim B$, then $B \sim A$ (symmetry)
- If $A \sim B$ and $B \sim C$, then $A \sim C$ (transitivity)

### DS 1.3 — Laws of propositional logic (*zakoni izjavnega računa*)

1. **Double negation** (*zakon dvojne negacije*):
   - $\neg\neg A \sim A$

2. **Idempotence** (*idempotenca*):
   - $A \land A \sim A$
   - $A \lor A \sim A$

3. **Commutativity** (*komutativnost*):
   - $A \land B \sim B \land A$
   - $A \lor B \sim B \lor A$
   - $A \Leftrightarrow B \sim B \Leftrightarrow A$

4. **Associativity** (*asociativnost*):
   - $(A \land B) \land C \sim A \land (B \land C)$
   - $(A \lor B) \lor C \sim A \lor (B \lor C)$
   - $(A \Leftrightarrow B) \Leftrightarrow C \sim A \Leftrightarrow (B \Leftrightarrow C)$

5. **Absorption** (*absorpcija*):
   - $A \land (A \lor B) \sim A$
   - $A \lor (A \land B) \sim A$

6. **Distributivity** (*distributivnost*):
   - $(A \lor B) \land C \sim (A \land C) \lor (B \land C)$
   - $(A \land B) \lor C \sim (A \lor C) \land (B \lor C)$

7. **[[De Morgan's Laws]]** (*De Morganova zakona*):
   - $\neg(A \lor B) \sim \neg A \land \neg B$
   - $\neg(A \land B) \sim \neg A \lor \neg B$

## Questions

- [ ] 

## Connections

- Course: [[Discrete structures]]
- Exercises: [[Discrete structures 1 exercises.pdf]]

## Sources

- Handwritten notes (photos): [[Discrete structures 1 notes 1.jpeg|1]], [[Discrete structures 1 notes 2.jpeg|2]], [[Discrete structures 1 notes 3.jpeg|3]], [[Discrete structures 1 notes 4.jpeg|4]], [[Discrete structures 1 notes 5.jpeg|5]], [[Discrete structures 1 notes 6.jpeg|6]]
