---
type: "[[Lectures]]"
course: "[[Discrete structures]]"
date: 2026-11-16
week: "7"
---

# 2026-11-16 - Graph of a Relation, Operations, Closures and Equivalence Relations

## Main Idea

A [[Relation|relation]] $R \subseteq A \times A$ can be drawn as a graph (*grafična predstavitev relacije*), and its properties can be read from the graph: loops, two-way arrows, shortcuts and obstacles (*ovire*). Then operations on relations (*operacije z relacijami*): the set operations, the complement, the [[Inverse Relation|inverse relation]] (*inverzna relacija*) and the [[Composition of Relations|product of relations]] (*produkt relacij*), shown on family relations (*sorodstvene relacije*), together with their laws and powers of relations (*potence relacij*). From powers we get the [[Transitive Closure|transitive closure]] $R^+$ and the transitive-reflexive closure $R^*$ (*ovojnice*), and the algebraic characterisation of the properties of relations. At the end the [[Equivalence Relation|equivalence relation]] (*ekvivalenčna relacija*), its [[Equivalence Class|equivalence classes]] (*ekvivalenčni razredi*) and the theorem that the factor set is a [[Partition|partition]] (*razbitje*).

## Notes

### Graph of a relation (*grafična predstavitev relacije*)

$R \subseteq A \times A$.

Example (*zgled*): $A = \{a, b, c, d\}$, $R = \{(a, b), (b, c), (c, d), (c, a)\}$ (the same relation as in the previous lecture). Every element is a point, every pair $(x, y) \in R$ an arrow from $x$ to $y$:

![[Discrete structures 7 graph of R.svg]]

The properties of a relation can be read from the graph (*lastnosti relacije lahko preberemo iz grafa*):

1. **reflexive** (*refleksivna*) — if all loops (*zanke*) are present;
2. **symmetric** (*simetrična*) — all arrows go both ways (*vse puščice so dvosmerne*); a two-way arrow can be drawn as one line without arrowheads;
3. **antisymmetric** (*antisimetrija*) — a pair of opposite arrows between two points is the forbidden structure for antisymmetry (*prepovedana struktura za antisimetrijo, ovira*);
4. **transitive** (*tranzitivnost*) — if all shortcuts (*bližnjice*) are present: for every two consecutive arrows there is also the direct arrow;
5. **connected** (*sovisnost*) — there is an arrow between every two (distinct) elements (*med vsakima elementoma je puščica*), in either direction or both; two points with no arrow between them are the obstacle to connectedness;
6. **functional** (*enolična*) — at most one arrow leaves each point (*iz vsake točke gre največ ena puščica*); two arrows from the same point (also a loop plus an arrow) are the obstacles to functionality.

![[Discrete structures 7 graph properties.svg]]

### Operations on relations (*operacije z relacijami*)

If $R, S$ are relations in the set $A$, then

$$R \cup S, \quad R \cap S, \quad R \setminus S, \quad R + S$$

are relations in $A$ too.

**Complement** (*komplement*):

$$R^c := (A \times A) \setminus R = U_A \setminus R$$

In $\mathbb{N}$: $\le^c \;=\; >$.

#### Inverse relation (*inverzna relacija*)

$$R^{-1} := \{(y, x);\, (x, y) \in R\}$$

(we swap the coordinates — *zamenjamo koordinate*). It holds:

$$xRy \Leftrightarrow yR^{-1}x$$

$R^{-1}$ for the relation from before (*od prej*) — all arrows are reversed:

![[Discrete structures 7 inverse relation.svg]]

$$\subseteq^{-1} \;=\; \supseteq \qquad \subset^{-1} \;=\; \supset \qquad \subseteq^c \;=\; ? \text{ (homework — \textit{doma})}$$

#### Product of relations (*produkt relacij*)

$R, S$ relations in the set $A$:

$$x \,R * S\, z \;\ldots\; \exists y:\, xRy \text{ and } ySz$$

— between $x$ and $z$ we insert some $y$ (*nekaj vmes vstavimo $y$*).

#### Family relations (*sorodstvene relacije med ljudmi*)

$x$ *oče* $y$ $\Leftrightarrow$ $x$ is the father of $y$ (*$x$ je oče $y$-ona*).

- Elementary (*elementarne*): father, mother, son, daughter, husband, wife, … (*oče, mati, sin, hči, mož, žena*)
- Task (*naloga*): parent, son-in-law, daughter-in-law, grandfather, grandson, mother-in-law, brother-in-law (*roditelj, zet, snaha, ded, vnuk, tašča, svak*)

$$\text{roditelj} = \text{oče} \cup \text{mati} \qquad \text{oče} = \text{roditelj} \setminus \text{mati}$$

$x$ *roditelj* $y$, i.e. $(x, y) \in$ *roditelj*.

**Grandfather** (*ded*):

$$\text{ded} = \text{oče} * \text{oče} \cup \text{oče} * \text{mati} = \text{oče} * (\text{oče} \cup \text{mati}) = \text{oče} * \text{roditelj}$$

— fathers of fathers, fathers of mothers (*očetje od očetov, očetje od mati*). The word "of" (*od*) works like multiplication: $\frac{2}{3}$ of $\frac{4}{5}$ $= \frac{2}{3} \cdot \frac{4}{5}$ (*"od" prepisalo v množenje*).

$$x \,\text{oče} * \text{oče}\, z \;\ldots\; \exists y:\, x \text{ oče } y \text{ and } y \text{ oče } z$$

**Grandson** (*vnuk*, must be a boy — *mora biti fant*):

$$\text{vnuk} = \text{sin} * \text{sin} \cup \text{sin} * \text{hči} = \text{sin} * (\text{sin} \cup \text{hči}) = \text{sin} * \text{otrok}$$

**Son-in-law, daughter-in-law, mother-in-law** (*zet, snaha, tašča*):

$$
\begin{aligned}
\text{zet} &= \text{mož} * \text{hči} \cup \text{mož} * \text{sin} = \text{mož} * \text{otrok} \\
\text{snaha} &= \text{žena} * \text{sin} \cup \text{žena} * \text{hči} = \text{žena} * \text{otrok} \\
\text{tašča} &= \text{mati} * \text{žena} \cup \text{mati} * \text{mož} = \text{mati} * (\text{žena} \cup \text{mož}) = \text{mati} * \text{zakonec}
\end{aligned}
$$

**Brother-in-law** (*svak*):

$$
\begin{aligned}
\text{svak} &= \text{brat} * \text{žena} \cup \text{mož} * \text{sestra} \\
&\quad \cup\; \text{brat} * \text{mož} \cup \text{mož} * \text{brat} \\
&= \text{brat} * \text{zakonec} \cup \text{mož} * \text{sorojenec}
\end{aligned}
$$

The terms written in red in the notebook hold only if we allow same-sex marriages (*z rdečo, če dovolimo istospolne poroke*).

Inverses:

$$\text{roditelj}^{-1} = \text{otrok} \qquad \text{zakonec}^{-1} = \text{zakonec} \qquad \text{sorojenec}^{-1} = \text{sorojenec}$$

### Properties of operations with relations (*lastnosti operacij z relacijami*)

$R, S, T$ relations on $A$.

1. $(R^{-1})^{-1} = R$
2. $(R * S)^{-1} = S^{-1} * R^{-1}$
3. $(R * S) * T = R * (S * T) =: R * S * T$ — associative (*asociativen*)
4. $R * (S \cup T) = (R * S) \cup (R * T)$ — the product is not commutative (*ni komutativno*)
5. (not written in the notebook; textbook p. 85: $(R \cup S) * T = (R * T) \cup (S * T)$)
6. $R * \mathrm{id}_A = \mathrm{id}_A * R = R$
7. $R \subseteq S \Rightarrow R * T \subseteq S * T$ and $T * R \subseteq T * S$

4. and 5. do not hold for intersection (*ne velja za presek*).

For numbers, $(a \cdot b)^{-1} = b^{-1} \cdot a^{-1}$ is the more correct form (*bolj pravilno*); it is also $= a^{-1} \cdot b^{-1}$, but only because $\cdot$ is commutative.

**Proof of 2.**

$$
\begin{aligned}
x\,(R * S)^{-1}\,y \;&\ldots\; y\,(R * S)\,x \\
&\ldots\; \exists z\,(yRz \text{ and } zSx) \\
&\ldots\; \exists z\,(xS^{-1}z \text{ and } zR^{-1}y) \\
&\ldots\; x\,(S^{-1} * R^{-1})\,y
\end{aligned}
$$

(The same kind of formula as for inverse matrices — *takšno formulo pri inverznih matrik*.)

**Proof of 3** (with [[Quantifier|quantifiers]]):

$$
\begin{aligned}
x\,(R * S) * T\,y \;&\ldots\; \exists z\,(x\,R * S\,z \text{ and } zTy) \\
&\ldots\; \exists z\,\big(\exists w\,(xRw \text{ and } wSz) \text{ and } zTy\big) \\
&\ldots\; \exists z \exists w\,(xRw \text{ and } wSz \text{ and } zTy) \\
&\ldots\; \exists w \exists z\,\big(xRw \text{ and } (wSz \text{ and } zTy)\big) \\
&\ldots\; \exists w\,\big(xRw \text{ and } \exists z\,(wSz \text{ and } zTy)\big) \\
&\ldots\; \exists w\,\big(xRw \text{ and } w\,(S * T)\,y\big) \\
&\ldots\; x\,R * (S * T)\,y
\end{aligned}
$$

**Counterexample for intersection:** $A = \{a, b, c, d\}$ with relations $R$, $S$, $T$:

![[Discrete structures 7 product and intersection.svg]]

$a\,R * T\,d$ and $a\,S * T\,d$, so (*torej*) $a\,(R * T \cap S * T)\,d$, but (*toda*) $\neg\, a\,(R \cap S) * T\,d$, since $R \cap S = \emptyset$.

### Powers of relations (*potence relacij*)

Powers need associativity of multiplication (*asociativnost množenja*): for a non-associative product $(a \cdot a) \cdot a \ne a \cdot (a \cdot a)$, i.e. $a^2 \cdot a^1 \ne a^1 \cdot a^2$, and $a^3$ would not be well defined. Associativity is needed for a meaningful definition of powers (*asociativnost potrebujem za smiselno definicijo potenc*).

The identity relation does not change anything under multiplication (*relacija identitete ne pokvari ob množenju*):

$$R^0 := \mathrm{id}_A \qquad R^{n+1} := R^n * R, \text{ if } n \ge 0$$

$$
\begin{aligned}
R^1 &= R^0 * R = \mathrm{id}_A * R = R \\
R^2 &= R^1 * R = R * R \\
R^3 &= R^2 * R = (R * R) * R = R * R * R \\
&\;\;\vdots
\end{aligned}
$$

Can we define powers with negative exponents (*ali lahko definiramo potence z negativnimi eksponenti*)?

$$R^{-n} := (R^{-1})^n$$

We must not add exponents with different signs (*ne moremo seštevati eksponentov z različnimi znaki*): $R^n * R^m$ is not necessarily $R^{n+m}$.

Meaning in the graph (with $R$ from the first example):

- $aRb$ and $bRc$, so $a\,R * R\,c$, i.e. $aR^2c$ — from $a$ to $c$ we can get in 2 steps (*od $a$ do $c$ se da priti po 2 korakih*).
- $bR^2d$, $cR^2b$, $bR^2a$
- $R^3$ — in 3 ways (*na 3 načine*): $aR^3d$, $aR^3a$, …
- $R^5$ — in 5 steps (*v 5 korakih*).
- $R^{-7}$ — 7 steps, where I walk in the opposite direction (*7 korakov, kjer hodim v nasprotno smer*).

Relation *roditelj*:

$$\text{roditelj}^3 = \text{roditelj} * \text{roditelj} * \text{roditelj} \;\text{(great-grandparents — \textit{pra pra starš})} \qquad \text{roditelj}^2 = \text{roditelj} * \text{roditelj} \;\text{(grandparents — \textit{pra starš})}$$

**Task** (*naloga*): define ancestor, descendant, relative (*prednik, potomec, sorodnik*).

$$\text{prednik} = \text{roditelj} \cup \text{roditelj}^2 \cup \text{roditelj}^3 \cup \dots$$

$$\text{potomec} = \text{otrok}^1 \cup \text{otrok}^2 \cup \text{otrok}^3 \cup \dots$$

$x$ *sorodnik* $y$ … $x$ and $y$ have a common ancestor (*imata istega prednika*):

$$
\begin{aligned}
&\ldots\; \exists z\,(z \text{ prednik } x \text{ and } z \text{ prednik } y) \\
&\ldots\; \exists z\,(x \text{ prednik}^{-1}\, z \text{ and } z \text{ prednik } y)
\end{aligned}
$$

$$\text{sorodnik} = \text{prednik}^{-1} * \text{prednik} = \text{potomec} * \text{prednik}, \qquad \text{prednik}^{-1} = \text{potomec}$$

Exponents with different signs cannot be added (*eksponentov z različnimi znaki ne moremo sešteti*):

$$\text{prednik}^{-1} * \text{prednik} \ne \mathrm{id}_{\text{ljudi}} = \text{prednik}^0$$

### Closures (*ovojnice*)

**Transitive closure** (*tranzitivna ovojnica*) $R^+$:

- $R \subseteq R^+$
- $R^+$ is transitive
- $R^+$ is the smallest (with respect to inclusion — *glede na vsebovanost*) among all relations that satisfy the first two conditions.

**Claim** (*trdim*): $R^+$ is a transitive relation, where

$$R^+ = R \cup R^2 \cup R^3 \cup \dots = \bigcup_{k=1}^{\infty} R^k$$

**Proof** (*dokaz*): let $xR^+y$ and $yR^+z$.

$$
\begin{aligned}
&\exists k:\, xR^ky \text{ and } \exists l:\, yR^lz \\
&\ldots\; x\,R^k * R^l\,z \\
&\ldots\; x\,R^{k+l}\,z \\
&\ldots\; xR^+z \;\to\; \text{transitivity}
\end{aligned}
$$

**Transitive-reflexive closure** (*tranzitivno-refleksivna ovojnica*):

$$R^* = R^0 \cup R^1 \cup R^2 \cup \dots = \bigcup_{k=0}^{\infty} R^k, \qquad R^0 = \mathrm{id}_A$$

- $xR^+y$ … from $x$ I can get to $y$ in the graph of $R$ in some ($> 0$) steps (*po nekaj korakih*).
- $xR^*y$ … from $x$ I can get to $y$ in the graph in some (possibly also 0) steps.

For $R$ from the first example:

$$aR^+a, \quad aR^+b, \quad aR^+c, \quad aR^+d, \quad bR^+b, \quad cR^+c, \quad \neg\, dR^+d, \quad dR^*d$$

### Algebraic characterisation of the properties of relations (*algebraična karakterizacija lastnosti relacij*)

1. reflexive $\Leftrightarrow \mathrm{id}_A \subseteq R$
2. symmetric $\Leftrightarrow R^{-1} = R$
3. antisymmetric $\Leftrightarrow R^{-1} \cap R \subseteq \mathrm{id}_A$
4. transitive $\Leftrightarrow R^2 \subseteq R$
5. connected — left empty in the notebook; textbook p. 90: $\Leftrightarrow \mathrm{id}_A \cup R \cup R^{-1} = U_A$
6. (functional — not in the notebook; textbook p. 90: $\Leftrightarrow R^{-1} * R \subseteq \mathrm{id}_A$)

### Equivalence relation (*ekvivalenčna relacija*)

$R \subseteq A \times A$. (A relation is an equivalence relation if it is reflexive, symmetric and transitive — textbook p. 93; the definition is not written out in the notebook.)

Examples (*zgled*):

1. The relation $\parallel$ of parallelism (*vzporednosti*) in the set of all lines in the plane.
2. $A = \{\text{people}\}$, $xRy \Leftrightarrow x$ has the same eye colour as $y$ (*ima enako barvo oči kot*).
3. Let $m \in \mathbb{N}$, $m \ge 2$. Define the relation $R$ in $\mathbb{Z}$:
   $$xRy \Leftrightarrow m \text{ divides } |x - y|$$
   — [[Congruence Modulo m|congruence modulo]] $m$ (*kongruenca po modulu $m$*).
   $a$ divides $b$ (*$a$ deli $b$*) … $a \cdot x = b$ has an integer solution (*ima celoštevilsko rešitev*).
   $m \mid |x - y|$ iff (*ntk*) $m \mid (x - y)$. Transitivity: from $m \mid (x - y)$ and $m \mid (y - z)$ follows $m \mid (x - z)$.
4. The relation $\sim$ of [[Logical Equivalence|equivalence]] (*enakovrednosti*) in the set of propositional expressions/formulas (*izjavnih izrazov/formul*).

A pile of euro change (*kup evrskega drobiža*), relations:

- "are from the same country" (*sta iz iste države*)
- "has the same value as" (*ima enako vrednost kot*)
- "is minted from the same metal as" (*je skovan iz iste kovine kot*)
- "are from the same country and have the same value" (*sta iz iste države in imata isto vrednost*)
- "were minted in the same year" (*sta bila skovana istega leta*)

#### Equivalence classes (*ekvivalenčni razredi*)

$R[x]$ is the set of all $y$ that are in relation with $x$:

$$R[x] = \{y;\, yRx\}$$

- $x \in R[x]$ ← equivalence classes are non-empty (*neprazni*)
- every element $x \in A$ belongs to some equivalence class (*pripada kakemu ekvivalenčnemu razredu*): $x \in R[x]$

**Claim:**

$$R[x] = R[y] \Leftrightarrow xRy$$

($\Rightarrow$) $R[x] = R[y]$: $x \in R[x] = R[y]$ … $x \in R[y]$ … $xRy$.

($\Leftarrow$) $xRy$. How do we show that two sets are equal (*kako pokažemo, da sta dve množici enaki*)? We have to show both inclusions (*pokazati je treba obe vsebovanosti*):

$$R[x] \subseteq R[y] \quad \text{and} \quad R[y] \subseteq R[x]$$

Choose an arbitrary (*izberimo poljuben*) $z \in R[x]$:

$$zRx \text{ and } xRy \;\overset{T}{\ldots}\; zRy \;\ldots\; z \in R[y]$$

The same for (*—||—*) $z \in R[y]$: $zRy$ and $xRy \overset{S}{\ldots}$ $yRx$, then

$$zRy \text{ and } yRx \;\overset{T}{\ldots}\; zRx \;\ldots\; z \in R[x]$$

($T$ = transitivity, $S$ = symmetry.) ∎

#### Theorem (*izrek*): the factor set is a partition

The **factor set** (*faktorska množica*) $A/R$ represents a partition (*predstavlja razbitje*):

- $\bigcup_{x \in A} R[x] = A$ ✓ — a cover of the set $A$ (*pokritje množice $A$*)
- the $R[x]$ are non-empty ✓
- different equivalence classes are pairwise disjoint (*različni ekvivalenčni razredi so paroma disjunktni*).

Suppose (*denimo*) $R[x] \cap R[y] \ne \emptyset$, so $\exists z \in R[x] \cap R[y]$:

$$zRx \text{ and } zRy \;\overset{S}{\ldots}\; xRz \text{ and } zRy \;\overset{T}{\ldots}\; xRy \;\ldots\; R[x] = R[y]$$

So what the hell does this mean (*kaj pa to za vraga pomeni*)? The factor set forms a partition of the set (*faktorska množica sestavlja razbitje množice*). I split the set of euro change by country (*razbijem množico evrskega drobiža po državah*), …, we split everything into finer piles (*razbijemo vse na bolj fine kupčke*).

Equivalence relation → partition: two different views of the same concept (*dva različna pogleda na isti koncept*).

An equivalence relation = a rough equality (*groba enakost*).

Examples of factor sets:

1. lines in the plane / parallel lines $= \{\{\text{vertical}\}, \{\text{horizontal}\}, \{\text{at an angle of } 45°\}, \dots\} \simeq$ "the set of all directions in the plane" $\simeq [-\pi/2, \pi/2)$
2. people / eye colours $= \{\{\text{brown}\}, \{\text{green}\}, \{\text{blue}\}\}$ (*rjave, zelene, modre*)
3. $\mathbb{Z}$ / same remainder when divided by 5 (*isti ostanek pri deljenju s 5*)
   $$= \{\{\dots, 0, 5, 10, \dots\}, \{\dots, 1, 6, 11, \dots\}, \dots\} = \{R[0], R[1], R[2], R[3], R[4]\} \simeq \{0, 1, 2, 3, 4\}$$
4. $[p \Rightarrow q] = \{p \Rightarrow q,\; \neg q \Rightarrow \neg p,\; \neg p \lor q,\; \neg p \lor q \lor 0,\; \neg p \lor q \lor (r \land \neg r), \dots\}$

#### Relations that are not equivalences (*relacije, ki niso ekvivalenčne*)

1. "have a banknote of the same value in their wallet" (*imata bankovec z isto vrednostjo v denarnici*) in the set of people — transitivity does not hold (*tranzitivnost ne velja*).
2. The empty relation on a (non-empty) set $A$.
3. "is divisible by the same prime as" (*je deljiv z istim praštevilom kot*) in the set of natural numbers.
4. "is approximately equal" (*je približno enak*) in the set of real numbers: reflexive ✓, transitive ✗, symmetric ✓.

## Questions

- [ ] What is $\subseteq^c$, the complement of the inclusion relation? (homework — *doma*)
- [ ] Why are 4. and 5. (distributivity of the product over union) false for intersection — is there also a counterexample for the left version $R * (S \cap T)$?
- [ ] Why can't exponents with different signs be added, i.e. when exactly is $R^n * R^m = R^{n+m}$?
- [ ] Why is "divisible by the same prime" not an equivalence relation in $\mathbb{N}$ — which property fails, and for which numbers?

## Connections

- Course: [[Discrete structures]]
- Previous lecture: [[2026-11-09 - Set Equations, Cartesian Product and Relations - 6]] — definition of a relation, domain and range, the six properties and the table of examples
- [[Relation]], [[Inverse Relation]], [[Composition of Relations]], [[Transitive Closure]], [[Equivalence Relation]], [[Equivalence Class]], [[Partition]], [[Congruence Modulo m]]
- [[Partition]]: cover and partition were defined in lecture 6; here every equivalence relation gives a partition
- [[Quantifier]], [[Predicate Logic]]: the proof of associativity swaps $\exists z \exists w$ and moves a quantifier into a conjunction ([[2026-10-26 - Predicate Formulas, Scope of Quantifiers and Laws of Predicate Logic - 4]])
- [[Logical Equivalence]]: the class $[p \Rightarrow q]$ is a class of equivalent formulas ([[2026-10-05 - Propositional Logic - 1]])

## Sources

- Handwritten notes: [[Sources/discrete_structures/photoNotes/lectures/lecture7/lecture 7.pdf|lecture 7]]
- G. Fijavž, *Diskretne strukture* (FRI, 2015): 4.2 Operations on relations (pp. 84–87), 4.3 Graph of a relation and powers (pp. 87–90), 4.4 Closures of relations (pp. 90–92), 4.5 Equivalence relation (pp. 93–95) — [[Sources/discrete_structures/ds.pdf#page=84|ds.pdf]]
