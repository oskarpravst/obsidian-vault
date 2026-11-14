---
type: "[[Lectures]]"
course: "[[Discrete structures]]"
date: 2026-11-09
week: "6"
---

# 2026-11-09 - Set Equations, Cartesian Product and Relations

## Main Idea

A general method for solving systems of set equations with one unknown set (*reševanje sistemov enačb z eno neznano množico*): two lemmas rewrite the system as one equation with $\emptyset$ on the right, the equation is brought into the form $(X \cap P) \cup (X^c \cap Q) = \emptyset$, and from it we read the condition for solvability and all solutions. Then families of sets (*družine množic*): the [[Power Set|power set]] (*potenčna množica*), the union and intersection of a family with examples of intervals, and covers and partitions (*pokritje in razbitje*). After that the [[Ordered Pair|ordered pair]] (*urejeni par*), the [[Cartesian Product|Cartesian product]] (*kartezični produkt*) and its properties. At the end the start of [[Relation|relations]] (*relacije*): examples, domain and range, and the properties of relations with a table of examples.

## Notes

### Solving systems of equations with one unknown set (*reševanje sistemov enačb z eno neznano množico*)

Two lemmas:

- **T1:** $A \cup B = \emptyset$ iff (*natanko tedaj, ko*) $A = \emptyset$ and $B = \emptyset$.
- **T2:** $A + B = \emptyset$ iff $A = B$.

**Proof of T1.**
($\Leftarrow$) Assume $A = \emptyset$ and $B = \emptyset$. Then $A \cup B = \emptyset \cup \emptyset = \emptyset$.
($\Rightarrow$) Assume $A \cup B = \emptyset$. Then $A \subseteq A \cup B = \emptyset \leadsto A = \emptyset$ and $B \subseteq A \cup B = \emptyset \leadsto B = \emptyset$. ∎

**Proof of T2.**
($\Leftarrow$) Assume $A = B$:

$$A + B = (A \cup B) \setminus (A \cap B) = (A \cup A) \setminus (A \cap A) = A \setminus A = \emptyset$$

($\Rightarrow$) Assume $A + B = \emptyset$:

$$\emptyset = A + B = (A \setminus B) \cup (B \setminus A) \overset{T1}{\leadsto} A \setminus B = \emptyset \text{ and } B \setminus A = \emptyset$$

so $A \subseteq B$ and $B \subseteq A \leadsto A = B$. ∎

#### Example

$$\text{I.}\;\; A \cap X = B \setminus X \qquad \text{II.}\;\; C \cup X = X \setminus A$$

With T2 we rewrite the system so that $\emptyset$ is on the right (*sistem prepišemo tako, da je na desni $\emptyset$*):

$$\text{I.}\;\; (A \cap X) + (B \setminus X) = \emptyset \qquad \text{II.}\;\; (C \cup X) + (X \setminus A) = \emptyset$$

and with T1 into one equation:

$$\emptyset = \big((A \cap X) + (B \setminus X)\big) \cup \big((C \cup X) + (X \setminus A)\big)$$

Differences → intersection with the complement (*razlike → presek s komplementom*):

$$
\begin{aligned}
= \;&(A \cap X) \cap (B \cap X^c)^c \;\cup\; (B \cap X^c) \cap (A \cap X)^c \;\cup \\
&(C \cup X) \cap (X \cap A^c)^c \;\cup\; (X \cap A^c) \cap (C \cup X)^c
\end{aligned}
$$

[[De Morgan's Laws|De Morgan]]:

$$
\begin{aligned}
&(A \cap X) \cap (B^c \cup X) \;\cup\; (B \cap X^c) \cap (A^c \cup X^c) \;\cup \\
&(C \cup X) \cap (X^c \cup A) \;\cup\; (X \cap A^c) \cap (C^c \cap X^c)
\end{aligned}
$$

[[Disjunctive Normal Form|DNO]] — brackets joined by unions (*z disjunkcijami vezani oklepaji*), multiplying out each with each (*vsak z vsakim*):

$$
\begin{aligned}
&\cancel{(A \cap X \cap B^c)} \cup (A \cap X \cap \cancel{X}) \;\cup \\
&\cancel{(B \cap X^c \cap A^c)} \cup (B \cap X^c \cap \cancel{X^c}) \;\cup \\
&(C \cap X^c) \cup (C \cap A) \cup \underbrace{(X \cap X^c)}_{\emptyset} \cup (X \cap A) \;\cup \\
&\cancel{(X \cap A^c \cap C^c \cap X^c)}
\end{aligned}
$$

$A \cap X \cap B^c$ and $B \cap X^c \cap A^c$ drop out by absorption (*abs*, $A \cup (A \cap B) = A$): they are contained in $A \cap X$ and $B \cap X^c$. $X \cap X = X$ and $X^c \cap X^c = X^c$; the terms with $X \cap X^c$ are empty. What remains:

$$(B \cap X^c) \cup (C \cap X^c) \cup (C \cap A) \cup (X \cap A)$$

We sort the terms (*razvrsti*): each one should contain exactly one of $X$ and $X^c$. The term $C \cap A$ contains neither, so we intersect it with the universal set (*univerzalna množica*) $S$:

$$C \cap A = C \cap A \cap S = C \cap A \cap (X \cup X^c) = (C \cap A \cap X) \cup (C \cap A \cap X^c)$$

$$(X \cap A) \cup \underbrace{(C \cap A \cap X)}_{\text{abs}} \cup \underbrace{(C \cap A \cap X^c)}_{\text{abs}} \cup (B \cap X^c) \cup (C \cap X^c)$$

$C \cap A \cap X$ is absorbed by $X \cap A$, and $C \cap A \cap X^c$ by $C \cap X^c$. So:

$$(X \cap A) \cup \big(X^c \cap (B \cup C)\big) = \emptyset$$

#### The general equation

In general (*splošno*):

$$(X \cap P) \cup (X^c \cap Q) = \emptyset \;\overset{T1}{\leadsto}\; X \cap P = \emptyset \text{ and } X^c \cap Q = \emptyset$$

- $Q \cap X^c = Q \setminus X = \emptyset$, so $Q \subseteq X$;
- $X \cap P^{cc} = X \setminus P^c = \emptyset$, so $X \subseteq P^c$.

It must hold (*veljati mora*): $Q \subseteq X \subseteq P^c$.

- **Condition for solvability** (*pogoj za rešljivost*): $Q \subseteq P^c$.
- **All solutions** (*vse rešitve*): all $X$ for which $Q \subseteq X \subseteq P^c$ holds.

In the example ($P = A$, $Q = B \cup C$):

$$B \cup C \subseteq X \subseteq A^c$$

Condition for solvability: $B \cup C \subseteq A^c$, i.e.

$$(B \cup C) \setminus A^c = \emptyset \qquad (B \cup C) \cap A = \emptyset$$

![[Discrete structures 6 solution of the system.svg]]

At the colloquium, use the "sharp look" method (*na kolokviju uporabi metodo ostrega pogleda*).

### Power set (*potenčna množica*)

$$\mathcal{P}A = \{B;\, B \subseteq A\}$$

$\emptyset$ and $A$ belong to $\mathcal{P}A$ (*pripadata*).

For $\mathcal{P}\{1, 2, 3\}$, every subset is a choice of 0/1 for each element (*vsak element vzamemo ali ne*):

| 1 | 2 | 3 | subset |
|---|---|---|---|
| 0 | 0 | 0 | $\emptyset$ |
| 0 | 0 | 1 | $\{3\}$ |
| 0 | 1 | 0 | $\{2\}$ |
| 0 | 1 | 1 | $\{2, 3\}$ |
| 1 | 0 | 0 | $\{1\}$ |
| 1 | 0 | 1 | $\{1, 3\}$ |
| 1 | 1 | 0 | $\{1, 2\}$ |
| 1 | 1 | 1 | $\{1, 2, 3\}$ |

$$\mathcal{P}\{1, 2, 3\} = \{\emptyset, \{1\}, \{2\}, \{3\}, \{1, 2\}, \{1, 3\}, \{2, 3\}, \{1, 2, 3\}\}$$

$\{1\}$ is a set with one element, a **singleton**; $\{1, 2\}$ is a **pair** (*par*).

**Claim** (*trditev*): if $A$ has $n$ elements, then $\mathcal{P}A$ has $2^n$ elements, i.e. $A$ has $2^n$ subsets (*podmnožic*).

$$\mathcal{P}\emptyset = \{\emptyset\} \qquad \mathcal{P}\{\emptyset\} = \{\emptyset, \{\emptyset\}\}$$

$\mathcal{P}\{\emptyset, \{\emptyset\}\}$, with the same table over the elements $\emptyset$ and $\{\emptyset\}$:

| $\emptyset$ | $\{\emptyset\}$ | subset |
|---|---|---|
| 0 | 0 | $\emptyset$ |
| 0 | 1 | $\{\{\emptyset\}\}$ |
| 1 | 0 | $\{\emptyset\}$ |
| 1 | 1 | $\{\emptyset, \{\emptyset\}\}$ |

$$\mathcal{P}\{\emptyset, \{\emptyset\}\} = \{\emptyset, \{\{\emptyset\}\}, \{\emptyset\}, \{\emptyset, \{\emptyset\}\}\}$$

### Families of sets (*družine množic*)

A family of sets is a set of sets (*množica množic*):

$$\mathcal{A} = \{A_1, A_2, \dots\} = \{A_i;\, i \in I\}$$

**Union of a family** (*unija družine*):

$$\bigcup \mathcal{A} = \bigcup_{i \in I} A_i = \{x;\, \exists i\, (i \in I \land x \in A_i)\}$$

**Intersection of a family:**

$$\bigcap \mathcal{A} = \bigcap_{i \in I} A_i = \{x;\, \forall i\, (i \in I \Rightarrow x \in A_i)\}$$

#### Intervals

$$[a, b] = \{x \in \mathbb{R};\, a \le x \le b\} \qquad (a, b) = \{x \in \mathbb{R};\, a < x < b\} \qquad (a, \infty) = \{x \in \mathbb{R};\, a < x\}$$

**Example 1:** $A_i = [i, i + 1)$, $i \in \mathbb{Z}$.

$$\bigcup_i A_i = \mathbb{R} \qquad \bigcap_i A_i = \emptyset$$

For $x \in \mathbb{R}$ we have $\lfloor x \rfloor \in \mathbb{Z}$ (we round down — *zaokrožimo navzdol*), and $x \in A_{\lfloor x \rfloor}$.

![[Discrete structures 6 intervals A_i.svg]]

**Example 2:** $B_i = (i, \infty)$, $i \in \mathbb{N}$, with $B_0 \supseteq B_1 \supseteq B_2 \supseteq \dots$

![[Discrete structures 6 intervals B_i.svg]]

$$\bigcup_{i \in \mathbb{N}} B_i = (0, \infty) = B_0 \qquad \bigcap_i B_i = \emptyset$$

Proof (*dokaz*): $x \in B_0$, $\lfloor x \rfloor \in \mathbb{N}$, $x \notin B_{\lfloor x \rfloor + 7}$. (Already $x \notin B_{\lfloor x \rfloor + 1}$, since $x < \lfloor x \rfloor + 1$; any larger index works too.)

**Example 3:** $C_i = (2^{-i}, \infty)$, $i \in \mathbb{N}$, with $C_0 \subseteq C_1 \subseteq C_2 \subseteq \dots$

![[Discrete structures 6 intervals C_i.svg]]

$$\bigcup_{i \in \mathbb{N}} C_i = (0, \infty) \qquad \bigcap_{i \in \mathbb{N}} C_i = (1, \infty) = C_0$$

**Example 4:** $D_i = \left(\frac{1}{i}, 2 + \frac{1}{i}\right]$, $i \in \mathbb{N} \setminus \{0\}$.

![[Discrete structures 6 intervals D_i.svg]]

$$\bigcup_{i \in \mathbb{N} \setminus \{0\}} D_i = (0, 3] \qquad \bigcap_{i \in \mathbb{N} \setminus \{0\}} D_i = (1, 2]$$

**Example 5:** $A'_i = [i, i + 1)$, $i \in \mathbb{Z}$ — a partition (*razbitje*) of $\mathbb{R}$. (The cloud above is drawn in the notebook as "nimbus tratus".)

![[Discrete structures 6 partition A'_i.svg]]

### Cover and partition (*pokritje in razbitje*)

$\mathcal{A} = \{A_i;\, i \in I\}$ is a **cover** (*pokritje*) of the set $B$ if

$$B = \bigcup_{i \in I} A_i$$

$\mathcal{A}$ is a **partition** (*razbitje*) of $B$ if:

1. $\mathcal{A}$ is a cover of $B$,
2. $\mathcal{A}$ has no empty members (*nima praznih členov*),
3. the elements of $\mathcal{A}$ are pairwise disjoint (*paroma disjunktni*).

### Ordered pair (*urejeni par*)

$\{a, b\} = \{b, a\}$ is a **pair** (*par*); $(a, b)$ is an **ordered pair** (*urejeni par*): for one element we know that it is in the first place, for the other that it is in the second.

It can be defined with sets only (*lahko definiramo samo z množicami*, with priority — *prioriteto*):

$$(a, b) = \{\{a\}, \{a, b\}\}$$

**Claim:**

$$(a, b) = (c, d) \Leftrightarrow a = c \text{ and } b = d$$

$$\{\{a\}, \{a, b\}\} = \{\{c\}, \{c, d\}\} \text{ iff } a = c \text{ and } b = d$$

Bottom line: we will not see this definition again (*ne bomo več videli te definicije*).

### Cartesian product (*kartezični produkt*)

$$A \times B = \{(a, b);\, a \in A \land b \in B\}$$

$$[1, 3] \times [2, 4] = \{(a, b);\, 1 \le a \le 3,\; 2 \le b \le 4\}$$

The name comes from Descartes. $A \times B \ne B \times A$:

![[Discrete structures 6 cartesian product not commutative.svg]]

A **tuple** (*terka*) is the generalisation (*nadpomenka*) of the ordered pair (an ordered $n$-tuple — *urejena $n$-terica*).

$$(A \times B) \times C = A \times (B \times C) = A \times B \times C$$

We say that it is associative (but not commutative) (*rečemo, da je asociativen (ne pa komutativen)*). Strictly, $((a, b), c)$ and $(a, (b, c))$ are different objects; we identify both with the ordered triple $(a, b, c)$, and only then are the two products equal.

$$A \times A \times A = A^3 \qquad A^n = A \times A \times \dots \times A$$

#### Properties of the Cartesian product (*lastnosti kartezičnega produkta*)

$$
\begin{aligned}
&\text{I.} && A \times (B \cup C) = (A \times B) \cup (A \times C) \\
&\text{II.} && (A \cup B) \times C = (A \times C) \cup (B \times C)
\end{aligned}
$$

Precedence (*prednost*): whether $A \times B \cup C$ means $(A \times B) \cup C$ or $A \times (B \cup C)$ depends on the context (*odvisno od konteksta*).

$$\text{III.}\quad (A \cap B) \times (C \cap D) = (A \times C) \cap (B \times D)$$

It behaves more nicely with intersection (*s presekom se lepše obnaša*). Example: $A = C = [1, 3]$, $B = D = [2, 4]$:

$$(A \cup B) \times (C \cup D) \ne (A \times C) \cup (B \times D)$$

e.g. $(1, 4) \in [1, 4] \times [1, 4]$, but it is neither in $A \times C = [1, 3]^2$ nor in $B \times D = [2, 4]^2$ (the dots in the sketch).

![[Discrete structures 6 cartesian product and union.svg]]

In III. we put $C = D$ and use

$$(A \cap B) \times C = (A \times C) \cap (B \times C)$$

— this is II. written with $\cap$ instead of $\cup$.

$$A \times B = \emptyset \Leftrightarrow A = \emptyset \lor B = \emptyset$$

$$A \subseteq C \land B \subseteq D \Rightarrow A \times B \subseteq C \times D$$

To the left ($\Leftarrow$):

$$A \times B \subseteq C \times D \land A \times B \ne \emptyset \Rightarrow A \subseteq C \land B \subseteq D$$

The condition $A \times B \ne \emptyset$ is necessary. Example: $A \times B = \emptyset$, then $A \times B \subseteq C \times D$ ✓ for every $C, D$. Say $A = \emptyset$, $C = \{c, \bar{c}, s, \bar{s}\}$, $D = \{d, e, f, g\}$. $A \subseteq C$ ✓, but $B$ can be chosen arbitrarily (*poljubno izberemo*): for $B = \mathbb{N}$, $B \subseteq D$ does not hold.

**Basic theorem of combinatorics** (*osnovni izrek kombinatorike*): if $A$ is finite with $m$ elements and $B$ finite with $n$ elements, then $A \times B$ is finite with $m \cdot n$ elements.

### Relations (*relacije*)

Two-place predicates (*dvomestni predikati*) $D(x, y)$: a connection between pairs in $\mathbb{N}$ (*zveza med pari*) — for some ordered pair it is valid, for another not.

A set $R$ is a **binary relation** (*dvomestna relacija*) if each of its elements is an ordered pair:

$$R \text{ is a relation} \Leftrightarrow \forall x \in R\; \exists u, v:\; x = (u, v)$$

A set $R$ is a **relation in $A$** if $R \subseteq A \times A$ (completed from the textbook, p. 81; missing in the notebook — *manjka*).

**Examples:**

1. $A = \{a, b, c, d\}$, $R = \{(a, b), (b, c), (c, d), (c, a)\}$; $D_R = \{a, b, c\}$, $Z_R = \{a, b, c, d\}$.
2. $A = \mathbb{N}$, $R = \{(x, y);\, x, y \in \mathbb{N} \land x \le y\}$:
   $$R = \{(0, 0), (0, 1), (0, 2), (0, 3), \dots, (1, 1), (1, 2), (1, 3), \dots, (2, 2), (2, 3), \dots, (3, 7), \dots\}$$
   This is $\le$ (as a set it is equal — *kot množica je enako*). Also
   $$R = \{(x, y);\, x, y \in \mathbb{N} \land \exists z \in \mathbb{N}:\, (y = x + z)\}$$
   is the relation $\le$. We write $(a, b) \in R$ … $aRb$, e.g. $(3, 5) \in\, \le$ … $3 \le 5$.
3. $\emptyset \subseteq A \times A$ — the **empty relation** (*prazna relacija*).
4. $U_A = A \times A \subseteq A \times A$ — the **universal relation** (*univerzalna relacija*).
5. $\mathrm{id}_A = \{(x, x);\, x \in A\}$ — the **relation of equality** (identity) (*relacija enakosti, identitete*). "$=$" is $\mathrm{id}_{\mathbb{N}} = \{(0, 0), (1, 1), (2, 2), (3, 3), \dots\}$: $0 \;\mathrm{id}_{\mathbb{N}}\; 0 \sim 0 = 0$.

#### Domain and range (*domena in zaloga vrednosti*)

$$D_R = \{x;\, \exists y:\, xRy\} \quad \text{domain (\textit{domena / definicijsko območje})}$$

$$Z_R = \{y;\, \exists x:\, xRy\} \quad \text{range (\textit{zaloga vrednosti})}$$

#### Properties of relations (*lastnosti relacij*)

$R$ is

1. **reflexive** (*refleksivna*) $\Leftrightarrow \forall x \in A:\; xRx$
2. **symmetric** (*simetrična*) $\Leftrightarrow \forall x, y \in A:\; xRy \Rightarrow yRx$
3. **antisymmetric** (*antisimetrična*) $\Leftrightarrow \forall x, y \in A:\; xRy \land yRx \Rightarrow x = y$
4. **transitive** (*tranzitivnost*) $\Leftrightarrow \forall x, y, z \in A:\; xRy \land yRz \Rightarrow xRz$
5. **connected** (*sovisna*) $\Leftrightarrow \forall x, y \in A:\; x \ne y \Rightarrow xRy \lor yRx$
6. **functional** (*enolična*) $\Leftrightarrow \forall x, y, z \in A:\; xRy \land xRz \Rightarrow y = z$ — every $x$ is in relation with at most one element (completed from the textbook, p. 83–84; missing in the notebook — *manjka*)

Examples — which properties they have (*katere lastnosti imajo*):

| relation | refl. | sym. | anti. | trans. | conn. | func. |
|---|---|---|---|---|---|---|
| ① $\mathrm{id}_A$ ($=$) in $A$ | ✓ | ✓ | ✓ | ✓ | ✗ | ✓ |
| ② $\le$ in $\mathbb{N}$ | ✓ | ✗ | ✓ | ✓ | ✓ | ✗ |
| ③ $<$ in $\mathbb{N}$ | ✗ | ✗ | ✓ | ✓ | ✓ | ✗ |
| ④ $\subseteq$ in $\mathcal{P}A$ | ✓ | ✗ | ✓ | ✓ | ✗ | ✗ |
| ⑤ "father" (*oče*) in {people} | ✗ | ✗ | ✓ | ✗ | ✗ | ✗ |

$x$ *oče* $y$ … $x$ is the father of $y$.

## Questions

- [ ] What is the "sharp look" method (*metoda ostrega pogleda*) for set equations, and when is it faster than the general procedure?
- [ ] How is the claim $(a, b) = (c, d) \Leftrightarrow a = c \land b = d$ proved for $(a, b) = \{\{a\}, \{a, b\}\}$? (not proved in the notebook)
- [ ] What does "with priority" (*prioriteto*) mean in the set definition of the ordered pair?

## Connections

- Course: [[Discrete structures]]
- Previous lecture: [[2026-11-02 - Prenex Normal Form, Sets and Russell's Paradox - 5]] — set operations, universal set, set equalities and the first systems of equations
- [[Set]], [[Power Set]], [[Ordered Pair]], [[Cartesian Product]], [[Relation]], [[Venn Diagram]]
- [[De Morgan's Laws]], [[Disjunctive Normal Form]]: the same steps as in propositional logic ([[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]])
- [[Truth Table]]: the 0/1 table of subsets is the table of all assignments for $n$ variables, hence $2^n$
- [[Predicate Logic]]: a binary relation is the set view of a two-place predicate
- Exercises: [[Sources/discrete_structures/photoNotes/vaje/vaje 6(asistentka zbolela).pdf|vaje 6]] (cancelled, self-study), assistant's solutions: [[Sources/discrete_structures/photoNotes/vaje/vaje 6 asistentove resitve.pdf|vaje 6 asistentove rešitve]], my solutions: [DS Vaje 6 · Množice](https://claude.ai/artifact/2pgySyQz7ckV1qHhNzkSKG)

## Sources

- Handwritten notes: [[Sources/discrete_structures/photoNotes/lectures/lecture6/lecture 6.pdf|lecture 6]]
- G. Fijavž, *Diskretne strukture* (FRI, 2015): 3.4 Solving systems of set equations (pp. 71–75), 3.5 Families of sets (pp. 75–77), 3.6 Cartesian product (pp. 77–79), 4 Relations and 4.1 Properties of relations (pp. 81–84) — [[Sources/discrete_structures/ds.pdf#page=71|ds.pdf]]
