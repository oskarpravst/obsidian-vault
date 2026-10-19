---
type: "[[Lectures]]"
course: "[[Discrete structures]]"
date: 2026-10-12
week: "2"
---

# 2026-10-12 - Normal Forms and Complete Sets of Connectives

## Main Idea

Continuation of [[Propositional Logic|propositional logic]]: the remaining laws (8–12), how to show two formulas are *not* equivalent (counterexample), how to build a formula from a given truth table ([[Disjunctive Normal Form|DNO]] and [[Conjunctive Normal Form|KNO]]), [[Functional Completeness|complete sets of connectives]] (*polni nabori izjavnih veznikov*), three more connectives (⊻, ↑, ↓) with an application to RAID 5, and the start of reasoning (*sklepanje*) — when a conclusion logically follows from premises.

## Notes

### Laws of propositional logic (continued)

Continues the list from [[2026-10-05 - Propositional Logic - 1|lecture 1]] (laws 1–7).

8. **[[Contraposition]]** (*kontrapozicija*):
   - $A \Rightarrow B \sim \neg B \Rightarrow \neg A$

> [!check] Proof (*dokaz*) — truth table
> | $A$ | $B$ | $\neg A$ | $\neg B$ | $A \Rightarrow B$ | $\neg B \Rightarrow \neg A$ |
> |:-:|:-:|:-:|:-:|:-:|:-:|
> | 0 | 0 | 1 | 1 | **1** | **1** |
> | 0 | 1 | 1 | 0 | **1** | **1** |
> | 1 | 0 | 0 | 1 | **0** | **0** |
> | 1 | 1 | 0 | 0 | **1** | **1** |
>
> The last two columns are identical in every row → $A \Rightarrow B \sim \neg B \Rightarrow \neg A$. $\blacksquare$

9. **Properties of 0 and 1** (*lastnosti 0 in 1*):
   - $A \Rightarrow A \sim 1$
   - $A \Leftrightarrow A \sim 1$
   - $A \lor \neg A \sim 1$
   - $A \land \neg A \sim 0$

10. **More properties of 0 and 1** (*še lastnosti 0 in 1*):
    - $A \land 0 \sim 0$
    - $A \lor 0 \sim A$
    - $A \land 1 \sim A$
    - $A \lor 1 \sim 1$
    - $A \Rightarrow 0 \sim \neg A$
    - $0 \Rightarrow A \sim 1$
    - $A \Rightarrow 1 \sim 1$
    - $1 \Rightarrow A \sim A$

    (In my notes only the first and the fifth law were written down (*manjka*); the rest are taken from the script, p. 20.)

11. **Properties of implication**:
    - a) $A \Rightarrow B \sim \neg A \lor B$
    - b) $\neg(A \Rightarrow B) \sim A \land \neg B$

> [!check] Proof of 11a — truth table
> | $A$ | $B$ | $\neg A$ | $A \Rightarrow B$ | $\neg A \lor B$ |
> |:-:|:-:|:-:|:-:|:-:|
> | 0 | 0 | 1 | **1** | **1** |
> | 0 | 1 | 1 | **1** | **1** |
> | 1 | 0 | 0 | **0** | **0** |
> | 1 | 1 | 0 | **1** | **1** |
>
> The last two columns are identical in every row → $A \Rightarrow B \sim \neg A \lor B$. $\blacksquare$

> [!check] Proof of 11b — using 11a
> $$
> \neg(A \Rightarrow B) \;\overset{\text{11a}}{\sim}\; \neg(\neg A \lor B) \;\overset{\text{De Morgan}}{\sim}\; \neg\neg A \land \neg B \;\overset{\text{double neg.}}{\sim}\; A \land \neg B \qquad \blacksquare
> $$
>
> (see [[De Morgan's Laws]])

12. **Properties of equivalence** (*lastnosti ekvivalence*):
    - $A \Leftrightarrow B \sim (A \Rightarrow B) \land (B \Rightarrow A)$
    - $A \Leftrightarrow B \sim (A \land B) \lor (\neg A \land \neg B)$
    - $\neg(A \Leftrightarrow B) \sim \neg A \Leftrightarrow B$

### How to show that two formulas are *not* equivalent

*Kako pokazati, da $I$ in $J$ nista enakovredna?*

It is enough to find **a single row** of the truth table where they differ — a **counterexample** (*protiprimer*).

**Example:** $(p \Rightarrow q) \Rightarrow r$ vs. $p \Rightarrow (q \Rightarrow r)$

| $p$ | $q$ | $r$ | $(p \Rightarrow q) \Rightarrow r$ | $p \Rightarrow (q \Rightarrow r)$ |
|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | **0** | **1** |

→ not equivalent (*nista enakovredna*).

### Normal forms (*normalni obliki*)

**Task** (*naloga*): find a propositional formula with a prescribed truth table.

| row | $p$ | $q$ | $r$ | $A$ |
|:-:|:-:|:-:|:-:|:-:|
| 1 | 0 | 0 | 0 | 0 |
| 2 | 0 | 0 | 1 | 1 |
| 3 | 0 | 1 | 0 | 0 |
| 4 | 0 | 1 | 1 | 1 |
| 5 | 1 | 0 | 0 | 1 |
| 6 | 1 | 0 | 1 | 1 |
| 7 | 1 | 1 | 0 | 0 |
| 8 | 1 | 1 | 1 | 1 |

#### Disjunctive normal form — DNO (*disjunktivna normalna oblika*)

Focus on the rows with **1** (*zapičim se v vrstice z 1*).

$A$ is true if we are in row 2 **or** row 4 **or** row 5 **or** row 6 **or** row 8:

- row 2: $p = 0, q = 0, r = 1$ ($p$ false, $q$ false, $r$ true)
- row 4: $p = 0, q = 1, r = 1$
- row 5: $p = 1, q = 0, r = 0$
- row 6: $p = 1, q = 0, r = 1$
- row 8: $p = 1, q = 1, r = 1$

Each row becomes a **basic conjunction** (*osnovna konjunkcija*), and these are joined with disjunctions:

$$
A \sim (\neg p \land \neg q \land r) \lor (\neg p \land q \land r) \lor (p \land \neg q \land \neg r) \lor (p \land \neg q \land r) \lor (p \land q \land r)
$$

This is the **disjunctive normal form** of $A$: $A \sim A_{DNO}$.

The DNO is **full** (*polna*) if every basic conjunction contains all variables of the formula (each either as itself or as its negation), as in this example (script, p. 24).

#### Conjunctive normal form — KNO (*konjunktivna normalna oblika*)

Alternative approach — the [[Duality|dual structure]] (*dualna struktura*). Focus on the rows with **0** (*zapičim se v vrstice z 0*).

$A$ is true iff we are **not** in row 1 **and not** in row 3 **and not** in row 7, i.e. in each of these rows at least one variable must differ (*vsaj ena mora biti res*):

- not row 1: $p = 1$ or $q = 1$ or $r = 1$
- not row 3: $p = 1$ or $q = 0$ or $r = 1$
- not row 7: $p = 0$ or $q = 0$ or $r = 1$

Each row becomes a **basic disjunction** (*osnovna disjunkcija*), and these are joined with conjunctions:

$$
A \sim (p \lor q \lor r) \land (p \lor \neg q \lor r) \land (\neg p \lor \neg q \lor r)
$$

This is the **conjunctive normal form**: $A \sim A_{KNO}$.

Analogously, the KNO is **full** (*polna*) if every basic disjunction contains all variables (script, p. 25).

#### Simplifying further (*še naprej poenostavimo*)

Factor out $\lor r$ (distributive law):

$$
\begin{aligned}
&(p \lor q \lor r) \land (p \lor \neg q \lor r) \land (\neg p \lor \neg q \lor r) \\
&\sim \big((p \lor q) \land (p \lor \neg q) \land (\neg p \lor \neg q)\big) \lor r \\
&\sim \big((p \lor (\underbrace{q \land \neg q}_{0})) \land (\neg p \lor \neg q)\big) \lor r \\
&\sim \big(p \land (\neg p \lor \neg q)\big) \lor r \\
&\sim \big((\underbrace{p \land \neg p}_{0}) \lor (p \land \neg q)\big) \lor r \\
&\sim (p \land \neg q) \lor r
\end{aligned}
$$

It can be simplified even more (double negation, then rule 11a twice):

$$
(p \land \neg q) \lor r \sim \neg\neg(p \land \neg q) \lor r \sim \neg(\neg p \lor q) \lor r \sim (p \Rightarrow q) \Rightarrow r
$$

#### Claim (*trditev*)

- Every propositional formula has a DNO.
- Every propositional formula has a KNO.

DNO of a contradiction and KNO of a tautology:

- $0 \sim (p \land \neg p) \lor (q \land \neg q)$ — the second part is not necessary (*to ni nujno*): $0 \sim p \land \neg p$
- $1 \sim (p \lor \neg p) \lor (q \lor \neg q)$ — you don't need the second part (*ne rabiš*): $1 \sim p \lor \neg p$
  - Note: the version written here is a single basic disjunction, so it is a KNO too. Since a KNO is a *conjunction* of basic disjunctions (script, p. 25), the form dual to the DNO of a contradiction above would be $(p \lor \neg p) \land (q \lor \neg q)$.

**DNO and KNO are not uniquely determined** (*niso enolično določene*):

- $p \Rightarrow q \sim \neg p \lor q$ — a DNO with two very short basic conjunctions ($\neg p$ and $q$), and at the same time a KNO with one basic disjunction.
- The full DNO from the truth table: $p \Rightarrow q \sim (\neg p \land \neg q) \lor (\neg p \land q) \lor (p \land q)$

#### Consequence (*posledica*)

Every propositional formula can be written using only $\neg$, $\land$, $\lor$.

### Complete sets of connectives (*polni nabori izjavnih veznikov*)

$\mathcal{N}$ is a **complete set of connectives** if every formula can be equivalently written using only connectives from $\mathcal{N}$. By the consequence above:

$$\{\neg, \land, \lor\} \text{ is a complete set.}$$

#### $\{\neg, \lor\}$ is complete

> [!check] Proof (*dokaz*) — reduction to $\{\neg, \land, \lor\}$
> 1. Take an arbitrary formula $A$. **Goal:** write it equivalently using only $\neg$ and $\lor$.
> 2. Because $\{\neg, \land, \lor\}$ is complete, there exists $A'$ with $A' \sim A$ that uses only $\{\neg, \land, \lor\}$.
> 3. It is enough to get rid of $\land$ in $A'$:
>    $$p \land q \sim \neg\neg(p \land q) \overset{\text{De Morgan}}{\sim} \neg(\neg p \lor \neg q)$$
> 4. This gives $A''$ with $A'' \sim A' \sim A$, and $A''$ uses only $\{\neg, \lor\}$. $\blacksquare$

→ **Reduction** (*redukcija*) to a known complete set: express every connective of a known complete set with the new set.

#### Other complete sets (*nekaj drugih polnih naborov*)

- $\{\neg, \land\}$ — known complete set $\{\neg, \land, \lor\}$:
  $p \lor q \sim \neg\neg(p \lor q) \sim \neg(\neg p \land \neg q)$
- $\{\neg, \Rightarrow\}$ — known complete set $\{\neg, \lor\}$:
  $p \lor q \sim \neg\neg p \lor q \sim \neg p \Rightarrow q$
- $\{0, \Rightarrow\}$ — here the formulas (*i. i.* = *izjavni izraz*) are defined as:
  1. $0$ is a formula,
  2. $p, q, r, \dots$ are formulas,
  3. if $I$ and $J$ are formulas, then $(I \Rightarrow J)$ is a formula.

  Known complete set $\{\neg, \Rightarrow\}$: $\neg p \sim p \Rightarrow 0$

#### How to show that a set $\mathcal{N}$ is *not* complete?

$\{\land, \lor\}$ is **not** a complete set: both connectives **preserve the value 0** (*ohranjata vrednost 0*):

$$0 \land 0 \sim 0, \qquad 0 \lor 0 \sim 0$$

⟹ the whole set preserves 0. E.g. in $(p \land q) \land (r \lor p) \lor (q \land r)$, if all variables are 0, the result is 0 (by [[Mathematical Induction|induction]] on the depth, the output is always 0). But $\neg p$ is 1 when $p = 0$, so no such formula can be equivalent to $\neg p$.

Also not complete:

- $\{\Rightarrow, \Leftrightarrow\}$ — both connectives **preserve the value 1** ($1 \Rightarrow 1 \sim 1$, $1 \Leftrightarrow 1 \sim 1$), so a formula built from them is 1 when all its variables are 1 and cannot be equivalent to $\neg p$ (script, p. 27).
- $\{\land, \lor, \Rightarrow, \Leftrightarrow\}$ — all four connectives preserve the value 1, so the same argument applies.
- $\{\neg, \Leftrightarrow\}$ — both connectives are **affine** (*afina*): each variable either always or never affects the result. Every formula built from them is therefore affine too, but $p \land q$ is not, so it cannot be expressed ([Functional completeness, Wikipedia](https://en.wikipedia.org/wiki/Functional_completeness) — Post's criterion).

### Three more connectives (*še 3 izjavni vezniki*)

| Connective | Symbol | Name |
|---|:-:|---|
| [[Exclusive Or\|Exclusive disjunction]] (*ekskluzivna disjunkcija*) | $\veebar$ | XOR |
| [[Sheffer Stroke\|Sheffer connective]] (*Shefferjev veznik*) | $\uparrow$ | NAND |
| [[Peirce Arrow\|Peirce–Łukasiewicz connective]] (*Peirce-Łukasiewiczev veznik*) | $\downarrow$ | NOR |

#### Exclusive disjunction

$A \veebar B$ — "*A ekskluzivni ali B*". True when **exactly one** is true (the opposite of equivalence).

| $A$ | $B$ | $A \veebar B$ |
| :-: | :-: | :-----------: |
|  0  |  0  |       0       |
|  0  |  1  |       1       |
|  1  |  0  |       1       |
|  1  |  1  |       0       |

#### Sheffer connective (NAND)

$A \uparrow B$ — false when both are true (the opposite of conjunction).

| $A$ | $B$ | $A \uparrow B$ |
|:-:|:-:|:-:|
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

$$A \uparrow B \sim \neg(A \land B)$$

#### Peirce–Łukasiewicz connective (NOR)

$A \downarrow B$ — true when both are false (the opposite of disjunction).

| $A$ | $B$ | $A \downarrow B$ |
|:-:|:-:|:-:|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 0 |

$$A \downarrow B \sim \neg(A \lor B)$$

#### Precedence (*kam uvrščamo po prednosti*)

- $\veebar$ has the same precedence as disjunction:
  $A \lor B \veebar C \lor D \sim ((A \lor B) \veebar C) \lor D$
- $\uparrow$ and $\downarrow$ have the same precedence as conjunction:
  $A \uparrow B \land C \downarrow D \uparrow E \sim (((A \uparrow B) \land C) \downarrow D) \uparrow E$

Connectives of equal precedence are grouped from left to right.

#### Laws (*zakoni*)

1. Exclusive disjunction:
   - $A \veebar B \sim \neg(A \Leftrightarrow B)$
   - $A \veebar B \sim B \veebar A$
   - $(A \veebar B) \veebar C \sim A \veebar (B \veebar C)$
2. …
3. …

The script also lists, as law (13), the properties of the Sheffer and Peirce–Łukasiewicz connectives (p. 21):

- $A \uparrow B \sim \neg(A \land B)$
- $A \downarrow B \sim \neg(A \lor B)$

#### Claim — XOR of many terms

The formula

$$A_1 \veebar A_2 \veebar A_3 \veebar \dots \veebar A_n$$

is, **regardless of how the parentheses are placed**, true exactly when an **odd number** (*liho mnogo*) of the terms are true.

**Examples:**

- $p \veebar p \veebar p \veebar p \veebar p \veebar p \sim 0$ (6 terms, always an even number of them true)
- $p \veebar q \veebar p \veebar q \veebar p \veebar q \veebar p \sim q$
  - $p$ appears $4\times$ → 0 or 4 true terms — always even
  - $q$ appears $3\times$ → 0 or 3 true terms — odd exactly when $q$ is true
  - if $q$ is false, the formula is false; if $q$ is true, it is true — it does not depend on $p$.

> [!check] Proof (*dokaz*) — induction on $n$, the number of terms
> **Base** (*BI*):
> - $n = 1$: $A_1$ — an odd number out of one means exactly one, i.e. $A_1$ is true. ✓
> - $n = 2$: $A_1 \veebar A_2$ is true when exactly one of the two is true — exactly one = an odd number. ✓
>
> **Inductive step** (*IK*): assume the claim holds for all natural numbers $1, 2, 3, \dots, n$ (strong induction). Look at an exclusive disjunction with $n+1$ terms. Whatever the parentheses, the last connective splits it into two parts:
>
> $$\underbrace{(A_1 \veebar \dots \veebar A_i)}_{\text{first}} \veebar \underbrace{(A_{i+1} \veebar \dots \veebar A_{n+1})}_{\text{second}}$$
>
> Both parts have at most $n$ terms, so the induction hypothesis applies to each of them:
>
> | first | second | first $\veebar$ second | true terms among $A_1, \dots, A_i$ | true terms among $A_{i+1}, \dots, A_{n+1}$ |
> |:-:|:-:|:-:|:-:|:-:|
> | 1 | 0 | **1** | odd | even |
> | 0 | 1 | **1** | even | odd |
>
> In both rows where the whole formula is true, odd + even = **odd** number of true terms among $A_1, \dots, A_{n+1}$. $\blacksquare$

#### Application (*uporaba*) — $\{\uparrow\}$ and $\{\downarrow\}$ are complete sets

$\{\uparrow\}$: choose the known complete set $\{\neg, \land\}$.

$$
\begin{aligned}
p \uparrow p &\sim \neg(p \land p) \sim \neg p \\
(p \uparrow q) \uparrow (p \uparrow q) &\sim \neg(p \uparrow q) \sim \neg\neg(p \land q) \sim p \land q
\end{aligned}
$$

#### Application — [[RAID]] 5 disk arrays (*diskovna polja*)

We have 4 TB of data on $4 \times 1$ TB disks.

- **Redundancy with a backup** (mirroring every disk): $8 \times 1$ TB → 800 €. A broken disk is restored from its copy.
- **RAID 5**: 5 disks → 500 €. Disks $p_1, \dots, p_4$ hold the data, and the extra disk is chosen so that

  $$p_1 \veebar p_2 \veebar p_3 \veebar p_4 \veebar p_5 \sim 0$$

  If disk $p_2$ breaks, XOR both sides with $p_2$ (the order does not matter — *vseeno*):

  $$p_1 \veebar p_2 \veebar p_3 \veebar p_4 \veebar p_5 \veebar p_2 \sim 0 \veebar p_2 \sim p_2$$

  and since $p_2 \veebar p_2 \sim 0$, the left side is $p_1 \veebar p_3 \veebar p_4 \veebar p_5$. So

  $$p_2 \sim p_1 \veebar p_3 \veebar p_4 \veebar p_5$$

Also mentioned: flash memory (*flash pomnilnik*) of type NOR or type NAND.

### Reasoning in propositional logic (*sklepanje v izjavnem računu*)

**Premises** (*predpostavke*):

1. This animal has wings or it is not a bird. (*Ta žival ima krila ali pa ni ptič.*)
2. If this animal is a bird, then it lays eggs. (*Če je ta žival ptič, potem leže jajca.*)
3. This animal has no wings. (*Ta žival nima kril.*)

**Conclusion** (*zaključek*):

4. This animal does not lay eggs. (*Ta žival ne leže jajc.*)

With $k$ … this animal has wings, $p$ … this animal is a bird, $j$ … this animal lays eggs:

$$
\begin{array}{ll}
1. & k \lor \neg p \\
2. & p \Rightarrow j \\
3. & \neg k \\
\hline
4. & \neg j
\end{array}
$$

#### Valid argument (*pravilen sklep*)

Write the truth table with the premises $A_1, A_2, \dots, A_n$ and the conclusion $B$. Only the rows where **all premises are true** matter; in the other rows the value of $B$ doesn't matter (*vseeno*).

$B$ **logically follows** from the premises (*logično sledi*) — the argument is valid — if $B$ is true in every row where all premises are true. We write

$$A_1, A_2, \dots, A_n \models B$$

$B$ would **not** logically follow if there existed a row (one is enough — *dovolj ena*) where all premises are true but the conclusion is 0 → a **counterexample** (*protiprimer*): a choice of values of the variables where the premises are true and the conclusion is false.

For the animal example:

| $k$ | $p$ | $j$ | $k \lor \neg p$ | $p \Rightarrow j$ | $\neg k$ | $\neg j$ |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 1 | 1 | 1 | 1 | **0** |

→ counterexample, so the argument is **not valid**.

**Example** (*zgled*): premises $(p \Rightarrow q) \Rightarrow (r \Rightarrow s)$, $\neg(r \Rightarrow q)$; conclusion $s$.

| $p$ | $q$ | $r$ | $s$ | $(p \Rightarrow q) \Rightarrow (r \Rightarrow s)$ | $\neg(r \Rightarrow q)$ | $s$ |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| 1 | 0 | 1 | 0 | 1 | 1 | **0** |

Here $p \Rightarrow q \sim 0$ and $r \Rightarrow s \sim 0$, so the first premise is $0 \Rightarrow 0 \sim 1$ → counterexample.

## Questions

- [ ] 

## Connections

- Course: [[Discrete structures]]
- Previous lecture: [[2026-10-05 - Propositional Logic - 1]]
- Exercises: [[Sources/calculus/photoNotes/vaje/vaje 2.pdf|vaja 2]]
- NAND/NOR and normal forms also appear in [[Introduction to Digital Circuits]]

## Sources

- Handwritten notes: [[Sources/discrete_structures/photoNotes/lectures/lecture2/lecture 2.pdf|lecture 2]]
- G. Fijavž, *Diskretne strukture* (FRI, 2015), sections 1.5–1.7
- [Functional completeness — Wikipedia](https://en.wikipedia.org/wiki/Functional_completeness)
