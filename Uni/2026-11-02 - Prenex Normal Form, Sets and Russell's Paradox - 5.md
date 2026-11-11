---
type: "[[Lectures]]"
course: "[[Discrete structures]]"
date: 2026-11-02
week: "5"
---

# 2026-11-02 - Prenex Normal Form, Sets and Russell's Paradox

## Main Idea

The end of [[Predicate Logic|predicate logic]]: every predicate formula can be rewritten into an equivalent [[Prenex Normal Form|prenex normal form]] (*preneksna normalna oblika*, PNO) with all quantifiers at the beginning, and a short proof by contradiction in predicate logic (*sklepanje v predikatnem računu*). Then the start of [[Set|set theory]] (*teorija množic*): membership, giving sets with a formula $\{x;\, \varphi(x)\}$, and why this does not work for every formula — [[Russell's Paradox|Russell's paradox]] (*Russllova antinomija*). After that: equality and inclusion (*enakost in vsebovanost*), the set operations and their properties, the universal set and the complement, set equalities proved with the laws of propositional logic, and systems of equations with sets (*sistemi enačb*). At the end, the resolution of Russell's paradox with classes (*razredi*).

## Notes

### Prenex normal form (*preneksna normalna oblika*)

$$W_{PNO} \sim W$$

$W_{PNO}$ has all quantifiers at the beginning (*ima vse kvantifikatorje na začetku*).

**Theorem** (*izrek*): every predicate formula $W$ has a $W_{PNO}$.

How do we get to the prenex normal form?

1. Rename the variables so that each one has its own role (*da ima vsaka svojo vlogo*).
2. Avoid $\Rightarrow$, $\Leftrightarrow$, $\veebar$ and the arrow connectives (the last symbol is unclear in the notebook).

**Example:**

$$\forall x\, A(x) \lor \exists x\, B(x) \Rightarrow D(x) \land \exists x\, D(x)$$

In the notebook, brackets mark the scope of each quantifier: $\forall x$ binds the $x$ in $A(x)$, $\exists x$ the $x$ in $B(x)$, the last $\exists x$ the $x$ in the last $D(x)$; the $x$ in the first $D(x)$ is free.

① Renaming:

$$\forall y\, A(y) \lor \exists z\, B(z) \Rightarrow D(x) \land \exists w\, D(w)$$

② Getting rid of the implication and moving the quantifiers to the front:

$$
\begin{aligned}
&\neg(\forall y\, A(y) \lor \exists z\, B(z)) \lor (D(x) \land \exists w\, D(w)) \\
\overset{*}{\sim}\; &(\exists y\, \neg A(y) \land \forall z\, \neg B(z)) \lor (D(x) \land \exists w\, D(w)) \\
\sim\; &\exists y\, (\neg A(y) \land \forall z\, \neg B(z)) \lor \exists w\, (D(x) \land D(w)) \\
\sim\; &\exists y\, \forall z\, (\neg A(y) \land \neg B(z)) \lor \exists w\, (D(x) \land D(w)) \\
\sim\; &\exists w\, (\exists y\, \forall z\, (\neg A(y) \land \neg B(z)) \lor (D(x) \land D(w))) \\
\sim\; &\exists w\, \exists y\, (\forall z\, (\neg A(y) \land \neg B(z)) \lor (D(x) \land D(w))) \\
\sim\; &\exists w\, \exists y\, \forall z\, ((\neg A(y) \land \neg B(z)) \lor (D(x) \land D(w)))
\end{aligned}
$$

\* Here I could still have decided (*tukaj sem se še lahko odločil*) which quantifier to move out first.

The last line is the prenex normal form. The rest of the formula — without quantifiers — can be transformed as we like (*preostanek formule brez kvantifikatorjev lahko kakor želimo preoblikujemo*).

The order of the quantifiers is not uniquely determined (*vrstni red kvantifikatorjev ni enolično določen*).

### Reasoning in predicate logic (*sklepanje v predikatnem računu*)

(Written in the textbook — *piše v učbeniku*.)

**Example:** $\neg \exists y\, \forall x\, (P(x, y) \Leftrightarrow \neg P(x, x))$

| | | |
|---|---|---|
| 1.1. | $\exists y\, \forall x\, (P(x, y) \Leftrightarrow \neg P(x, x))$ | premise RA (*pred. RA*) |
| 1.2. | $\forall x\, (P(x, c) \Leftrightarrow \neg P(x, x))$ | ES(1.1) $(y/c)$ |
| 1.3. | $P(c, c) \Leftrightarrow \neg P(c, c)$ | US(1.2) $(x/c)$ |
| 1.4. | $0$ | $\sim$ (1.3) |
| 1. | $\neg \exists y\, \forall x\, (P(x, y) \Leftrightarrow \neg P(x, x))$ | RA(1.1, 1.4) |

The formula is true in every interpretation (*resnična v vsaki interpretaciji*). (ES = existential specification, US = universal specification, RA = [[Contradiction|proof by contradiction]].)

### Sets (*operacije z množicami — teorija množic*)

The membership relation (*relacija pripadnosti*): $x \in A$ … $x$ belongs to $A$ (*x pripada A*); $x \notin A$ … does not belong (*ne pripada*).

**Giving sets** (*podajanje množic*): "$0 \in A$ and $1 \in A$ and $2 \in A$":

$$A = \{1, 2, 0\} = \{0, 2, 1\} = \{0, 0, 1, 2, 2, 2\}$$

The order does not matter because of the commutativity of conjunction (*komutativnost konjunkcije*), and repeated elements do not matter because of idempotence (*idempotentnost*).

**With a predicate formula** (*z izjavno formulo*):

$$A = \{x;\, \varphi(x)\} \qquad \boxed{x \in A \Leftrightarrow \varphi(x)}$$

Examples (*zgledi*):

- $A = \{x;\, x \neq x\} = \emptyset$ — it has no element (*ni nobenega elementa*).
- $B = \{x;\, x = 0 \lor x = 1 \lor x = 2\} = \{0, 1, 2\}$

We have to choose an interpretation (the domain of discourse is a set — *področje govora je množica*). If I want to define sets, I need sets (*če želim def. množice, potrebujem množice*).

$$R = \{x;\, x \notin x\}$$

— with this you will have a problem (*s tem boš imel težavo*). (Frege, *Grundlagen der Arithmetik*.)

### Russell's antinomy (*Russllova antinomija*)

Is $R \in R$?

$$R \in R \Leftrightarrow R \notin R$$

— this cannot be true (*ne more bit res*).

Domain of discourse (*p. g.*): sets and their elements, $P(x, y)$ … $x \in y$. Then the formula proved above, $\neg \exists y\, \forall x\, (P(x, y) \Leftrightarrow \neg P(x, x))$, says that $R$ does not exist!!! (*ne obstaja*)

**Russell's paradox — the library** (*knjižnica*): every library has a catalogue (*katalog*). Are there exactly those books in the library that are written in the catalogue? A catalogue can have an entry about itself (*zapis v samem sebi*).

- **good catalogues** (*dobri katalogi*): have an entry about themselves (they stay in the library),
- **bad catalogues** (*slabi katalogi*): have no entry about themselves (they must not be in the library).

The bad library (*slaba knjižnica*) is the library of bad catalogues; it also needs a catalogue $R$. Is $R$ bad or good (*slab ali dober*)?

- bad: it must not be in its own library (and with that it has to be in the bad library — *in s tem mora biti v slabi knjižnici*),
- good: it stays in the library (*ostane v knjižnicah*) — and with that this catalogue is bad (*in s tem je ta katalog slab*).

**Lesson** (*nauk*): we have to be careful when choosing the formula $\varphi(x)$. The set $\{x;\, \varphi(x)\}$ does not exist for every predicate $\varphi(x)$ (*množica ne obstaja pri čisto vsakem predikatu*).

### Equality and inclusion (*enakost in vsebovanost*)

$$A = B \Leftrightarrow \forall x\, (x \in A \Leftrightarrow x \in B)$$

The first $\Leftrightarrow$ is the equivalence of natural language (*ekvivalenca naravnega jezika*); the formula says: exactly when they have exactly the same elements (*natanko, če imata natanko iste elemente*).

$$A \subseteq B \Leftrightarrow \forall x\, (x \in A \Rightarrow x \in B) \qquad \text{subset (\textit{podmnožica})}$$

$$A \subset B \Leftrightarrow A \subseteq B \land A \neq B \qquad \text{proper subset (\textit{prava podmnožica})}$$

$\subset$ and $\subseteq$ are like $3 < 5$ and $5 \le 5$ (the second one is convenient to believe — *je ugodno to verjet*). Does a triangle with sides 2, 3, 5 exist (*ali obstaja $\Delta$ s stranicami 2, 3, 5*)?

### Set operations (*operacije z množicami*)

Each operation corresponds to a connective:

- intersection (*presek*) $A \cap B$ — $\land$
- union (*unija*) $A \cup B$ — $\lor$
- difference (*razlika*) $A \setminus B$
- symmetric difference (*simetrična razlika*) $A + B$ — $\veebar$ ([[Exclusive Or|exclusive or]])

![[Discrete structures 5 set operations.svg]]

### Properties of the operations (*lastnosti operacij*)

$$A = B \Leftrightarrow A \subseteq B \land B \subseteq A$$

> [!check] Proof (*dokaz*)
> $$
> \begin{aligned}
> A = B \;\dots\; &\forall x\, (x \in A \Leftrightarrow x \in B) \\
> &\forall x\, ((x \in A \Rightarrow x \in B) \land (x \in B \Rightarrow x \in A)) \\
> &\forall x\, (x \in A \Rightarrow x \in B) \land \forall x\, (x \in B \Rightarrow x \in A) \\
> &A \subseteq B \land B \subseteq A
> \end{aligned}
> $$

$$
\begin{aligned}
&A \subseteq B \Rightarrow A \cup C \subseteq B \cup C \\
&A \subseteq B \Rightarrow A \cap C \subseteq B \cap C \\
&A \cap B \subseteq A \subseteq A \cup B
\end{aligned}
$$

$A$ and $B$ are **disjoint** (*disjunktni*) if $A \cap B = \emptyset$.

Negation is hard to introduce into set theory (*negacija se težavno upelje v teorijo množic*).

### Universal set and complement (*univerzalna množica, komplement*)

The **universal set** $S$ (with it we avoid Russell's paradox — *s tem se izognemo Russlovem paradoksu*): something so big that anything we can think of is inside (*karkoli nas pade na pamet je notri*). All sets we deal with are contained in the universal set (*vse obravnavane množice so vsebovane v univerzalni množici*).

**Complement** (*komplement*):

$$A^c = S \setminus A$$

![[Discrete structures 5 complement.svg]]

$$(A^c)^c = A$$

$$(A \cap B)^c = A^c \cup B^c \qquad (A \cup B)^c = A^c \cap B^c$$

— the two [[De Morgan's Laws|De Morgan laws]] (*dva De Morganova zakona*).

$$
\begin{aligned}
&A \setminus B = A \cap B^c \\
&A \subseteq B \sim B^c \subseteq A^c \\
&A \cap B = \emptyset \Leftrightarrow A \subseteq B^c \Leftrightarrow B \subseteq A^c
\end{aligned}
$$

### Set equalities (*enakosti z množicami*)

$$A \cup (A \cap B) = A, \quad \text{i.e.} \quad \forall x\, (x \in A \cup (A \cap B) \Leftrightarrow x \in A)$$

We pick an arbitrary $x$ (*izberemo poljuben x*) and show $x \in A \cup (A \cap B) \sim x \in A$. With $x \in A$ … $a$ and $x \in B$ … $b$:

$$
\begin{aligned}
&x \in A \cup (A \cap B) \\
&x \in A \lor x \in (A \cap B) \\
&x \in A \lor (x \in A \land x \in B) \\
&a \lor (a \land b) \overset{\text{abs.}}{\sim} a \\
&x \in A \qquad \text{(absorption — \textit{absorpcija})}
\end{aligned}
$$

All laws of propositional logic can be transferred into set equalities (*vse zakone izjavnega računa se lahko premika v enakost množic*).

More set equalities (from the textbook — *iz učbenika*):

$$(A + B) \cap C = (A \cap C) + (B \cap C)$$

**(11)** $A \subseteq B \sim A \cup B = B \sim A \cap B = A \sim A \setminus B = \emptyset$ — each of these should trigger "inclusion" (*to naj sproži vsebovanost!*).

> [!check] Proof (*dokaz*)
> $A \subseteq B \Rightarrow A \cup B = B$: $B \subseteq A \cup B \subseteq B \cup B = B$, so $B = A \cup B$.
>
> The other direction (*druga smer*): $A \subseteq A \cup B = B$.
>
> $A \subseteq B \sim A \setminus B = \emptyset$:
>
> If $A \subseteq B$: $A \setminus B = A \cap B^c \subseteq B \cap B^c = \emptyset$.
>
> If $A \setminus B = \emptyset$:
> $$
> \begin{aligned}
> A = A \cap S &= A \cap (B \cup B^c) \\
> &= (A \cap B) \cup (A \cap B^c) \\
> &= (A \cap B) \cup \underbrace{(A \setminus B)}_{\emptyset} = A \cap B
> \end{aligned}
> $$

**Precedence of set operations** (*operacije z množicami po prednosti*):

$$^c \;/\; \cap, \setminus \;/\; \cup, +$$

### Systems of equations (*sistem enačb*)

Task: determine the conditions under which the system has a solution if the parameters are suitable, and what $X$ must be so that the system is solvable (*določiti pogoje, da bo sistem imel rešitev … kakšen X mora biti, da bo sistem rešljiv*).

**Example 1:**

$$\text{I.}\;\; X \cup A = A \setminus X \qquad \text{II.}\;\; X \cup A = X$$

II: think of inclusion (*pomislimo na vsebovanost*) … $A \subseteq X$.

From I: $A \subseteq X \cup A = A \setminus X \subseteq A$, so $A = X \cup A$, i.e. $X \subseteq A$. If both inclusions hold (*če veljata obe vsebovanosti*): $X = A$ (if a solution exists, this equality must hold — *če rešitev obstaja, mora veljati ta enakost*).

Is $X = A$ a solution?

- I: $A = A \cup A = A \setminus A = \emptyset$ — true only if $A = \emptyset$ (*res samo, če $A = \emptyset$*).
- II: $A \cup A = A$ ✓

Condition for solvability (*pogoj za rešljivost*): $A = \emptyset$. The solution is unique (*rešitev je ena sama*): $X = \emptyset \;(= A)$.

**Example 2:**

$$\text{I.}\;\; A \cup X = B \qquad \text{II.}\;\; A \cap X = C$$

From I:

$$B \cap A^c = (A \cup X) \cap A^c = \underbrace{(A \cap A^c)}_{\emptyset} \cup (X \cap A^c) = X \cap A^c$$

Then, with II:

$$X = X \cap S = X \cap (A \cup A^c) = (X \cap A) \cup (X \cap A^c) = C \cup (B \setminus A)$$

Condition: $\boxed{C \subseteq A \text{ and } A \subseteq B}$

![[Discrete structures 5 nested sets.svg]]

### Resolving Russell's paradox with classes (*razrešitev z razredi*)

A top-down approach. Classes (*razredi*) are the basic objects here (*to so osnovni objekti tukaj*): some classes are sets, some are not (proper classes — *pravi razredi*).

**Definition:** a class $A$ is a set if $\exists B: A \in B$; otherwise it is a proper class (*sicer je pravi razred*).

Notation (*oznaka*): $M(x)$ … $x$ is a set (*x je množica*).

Classes are described with a formula like this (*razredi so opisani s formulo takole*):

$$A = \{x;\, \varphi(x) \land M(x)\}$$

Then (*velja*):

$$x \in A \Leftrightarrow \varphi(x) \land M(x)$$

$$R = \{x;\, x \notin x \land M(x)\}$$

Is $R \in R$?

$$
\begin{aligned}
R \in R &\Leftrightarrow R \notin R \land M(R) \\
&\sim \underbrace{(R \in R \land R \notin R \land M(R))}_{0} \lor (R \notin R \land \neg(R \in R \land M(R))) \\
&\sim R \notin R \land (R \in R \lor \neg M(R)) \qquad \text{(distributive law)} \\
&\sim \underbrace{(R \notin R \land R \in R)}_{0} \lor (R \notin R \land \neg M(R)) \\
&\sim R \notin R \land \neg M(R)
\end{aligned}
$$

$R$ is not an element of itself and not a set, but a proper class (*ni element samega sebe, ni množica, ampak pravi razred*).

## Questions

- [ ] Does a triangle with sides 2, 3, 5 exist, and what does this have to do with $\subset$ vs. $\subseteq$?
- [ ] How is $A \subseteq B \sim A \cap B = A$ (the middle part of law 11) proved? (not proved in the notebook)

## Connections

- Course: [[Discrete structures]]
- Previous lecture: [[2026-10-26 - Predicate Formulas, Scope of Quantifiers and Laws of Predicate Logic - 4]] — renaming variables and moving quantifiers, used here for the PNO
- [[Prenex Normal Form]], [[Predicate Logic]], [[Contradiction|Proof by contradiction]] (RA, from [[2026-10-19 - Valid Arguments and Inference Rules - 3|lecture 3]])
- [[Set]], [[Russell's Paradox]], [[Venn Diagram]]
- [[De Morgan's Laws]], [[Contraposition]], [[Exclusive Or]]: the same laws for sets as in propositional logic
- [[2026-10-22 - Veitch Diagrams, Shannon Expansion and Decomposition - 3]] — Venn diagrams also appear in Digital circuits
- Exercises: [[Sources/discrete_structures/photoNotes/vaje/vaje 5.pdf|vaje 5]]

## Sources

- Handwritten notes: [[Sources/discrete_structures/photoNotes/lectures/lecture5/lecture 5.pdf|lecture 5]]
- G. Fijavž, *Diskretne strukture* (FRI, 2015): 2.5 Prenex normal form (pp. 52–54), 2.6 Reasoning in predicate logic (pp. 54–59), 3 Sets with Russell's paradox (pp. 61–63), 3.1–3.4 Equality and inclusion, operations, set equalities, systems of equations (pp. 63–74)
