---
type: "[[Lectures]]"
course: "[[Discrete structures]]"
date: 2026-10-26
week: "4"
---

# 2026-10-26 - Predicate Formulas, Scope of Quantifiers and Laws of Predicate Logic

## Main Idea

Continuation of [[Predicate Logic|predicate logic]] (*predikatni račun*). Predicates describe properties and relations; we turn them into propositions by plugging in constants or by binding variables with [[Quantifier|quantifiers]], and the order of quantifiers matters. Then the formal language: terms, atoms and the inductive definition of predicate formulas (*izjavne formule*), the scope of a quantifier (*doseg*) with [[Free and Bound Variables|free and bound variables]] (*proste in vezane spremenljivke*), substitution $W(x/a)$, interpretation, and [[Equivalence of Formulas|equivalent formulas]]. At the end, the laws of predicate logic (*zakoni predikatnega računa*): [[De Morgan's Laws|De Morgan's laws]] for quantifiers, swapping quantifiers of the same kind, distributivity, renaming bound variables, and moving a quantifier past a formula that does not contain $x$.

## Notes

### Predicates, properties and relations

Domain of discourse $\mathbb{N}$:

- $P(x)$ … $x$ is a prime number (*je praštevilo*)
- $D(x, y)$ … $x$ divides $y$ (*deli*)
- $V(x, y, z)$ … $x + y = z$

Truth values (as marked in the notebook):

| | | |
|---|---|---|
| $P(3) = 1$ | $P(4) = 0$ | $P(5) = 1$ |
| $D(2, 4) = 1$ | $D(4, 2) = 0$ | |
| $3 + 5 = 9$ → $0$ | $5 + 4 = 9$ → $1$ | |
| $\forall x\, P(x) = 0$ | $\exists x\, P(x) = 1$ | |

- one-place predicates such as $P$ correspond to properties (*ustreza lastnosti*),
- predicates with several places such as $D$ correspond to connections / relations (*zveze / relacije*).

### Turning $P(x, y)$ into a proposition

Domain of discourse: people (*ljudje*). $P(x, y)$ … $x$ knows $y$ (*x pozna y*).

In which ways can $P(x, y)$ be turned into a proposition (*na katere načine lahko $P(x, y)$ spremenimo v izjavo*)?

1. Plug in 2 concrete elements (*vstavimo 2 konkretna elementa*): $P(\text{Jože}, \text{Tone})$ … Jože knows Tone.
2. Plug in one element and quantify the other variable:

| | |
|---|---|
| $\exists y\, P(\text{Jože}, y)$ | Jože knows somebody (*Jože nekoga pozna*). |
| $\forall y\, P(\text{Jože}, y)$ | Jože knows all people (*Jože pozna vse ljudi*). |
| $\exists x\, P(x, \text{Tone})$ | Somebody knows Tone (*Nekdo pozna Toneta*). |
| $\forall x\, P(x, \text{Tone})$ | All people know Tone (*Toneta poznajo vsi ljudje*). |

3. Quantify both variables:

| | | |
|:-:|---|---|
| 1 | $\exists x\, \exists y\, P(x, y)$ | Somebody knows somebody (*Nekdo nekoga pozna*). |
| 2 | $\exists x\, \forall y\, P(x, y)$ | Somebody knows everyone (*Nekdo pozna vse*). |
| 3 | $\forall x\, \exists y\, P(x, y)$ | Everybody knows somebody (*Vsakdo pozna nekoga*). |
| 4 | $\forall x\, \forall y\, P(x, y)$ | Every person knows all people (*Vsak človek pozna vse ljudi*). |
| 5 | $\exists y\, \exists x\, P(x, y)$ | Somebody is known by somebody (*Nekoga nekdo pozna*). |
| 6 | $\exists y\, \forall x\, P(x, y)$ | There is a person whom everyone knows (*Obstaja človek, ki ga vsi poznajo*). |
| 7 | $\forall y\, \exists x\, P(x, y)$ | Everybody is known by somebody (*Vsakega nekdo pozna*). |
| 8 | $\forall y\, \forall x\, P(x, y)$ | Everybody is known by everyone (*Vsakega poznajo vsi*). |

Comparing the two groups:

$$1 \sim 5, \qquad 4 \sim 8, \qquad 2 \not\sim 6, \qquad 3 \not\sim 7$$

The arrows represent the relation of knowing (*puščice predstavljajo relacijo poznavanja*):

![[Discrete structures 4 knows relation.svg]]

### Predicate formulas (*izjavne formule*)

The language of predicate logic:

- variables (*spremenljivke*) $x, y, z, \dots$ and constants (*konstante*) $a, b, c, \dots$ — together called **terms** (*termi*); compare $ax^2 + bx + c = 0$,
- predicates (*predikati*) $P, Q, R, \dots$,
- connectives (*izjavni vezniki*),
- quantifiers (*kvantifikatorji*),
- parentheses (*oklepaja*).

**Atoms** (*atomi*) — we get them by plugging terms into predicates (*če terme vstavimo v predikate*): $P(x)$, $P(a)$, $Q(x, y)$.

**Predicate formulas** are defined inductively:

1. Atoms are predicate formulas.
2. If $W$ and $V$ are predicate formulas and $x$ is a variable, then $(\neg W)$, $(W \land V)$, $(W \Rightarrow V)$, $(\exists x\, W)$ and $(\forall x\, W)$ are also predicate formulas.

### Scope of quantifiers (*doseg kvantifikatorjev*)

In $\forall x\, P(x) \land Q(x, y)$ the quantifier $\forall x$ reaches only to the end of the nearest predicate formula (*dosega samo do konca najbližje izjavne formule*), here $P(x)$:

- the $x$ in $P(x)$ is a **bound variable** (*vezana spremenljivka*) — we can no longer plug anything into it (*ne moremo nič več vstavljati*),
- $x$ and $y$ in $Q(x, y)$ are **free variables** (*prosti spremenljivki*).

Analogy: in $x + 5$, $x$ is a real number and we can plug in a value: $1 + 5 = 6$. In $\int_1^2 (x + 5)\, dx$ we can't — the $\int_1^2 \dots dx$ acts like a quantifier (*kot kvantifikator*).

- In atoms all variables are free (*v atomih so vse spremenljivke proste*).
- Quantifiers have the same precedence as negation (*kvantifikatorji imajo isto prednost kot negacija*).

### Scope, bound and free variables (*doseg, vezane in proste spremenljivke*)

![[Discrete structures 4 scope of quantifiers.svg]]

- $\exists x\, P(x) \Rightarrow \forall x\, Q(x) \lor P(x) \land R(x) \lor S(y)$: the $x$ in $\exists x\, P(x)$ and in $\forall x\, Q(x)$ are bound variables; the $x$ in $P(x)$ and $R(x)$ and the $y$ in $S(y)$ are free variables.
- $\exists x\, \neg P(x, y) \Rightarrow Q(x) \land R(y)$: $\exists x$ binds only $x$ (*samo x*); $y$ in $P(x, y)$ and $Q(x)$, $R(y)$ are free.
- $\forall x\, \neg \exists x\, \forall z\, P(x, y, z)$: $y$ is free; $x$ is bound by $\exists x$ and $z$ by $\forall z$, so there are no free $x$ left for the outer $\forall x$ (*ni prostih x*). You have to go from right to left (*moraš iti iz desne proti levi*).

### Interpretation of a predicate formula (*interpretacija izjavne formule*)

An interpretation $\mathcal{I}$ of a formula $W$ is from a non-empty set $D$ (the domain of discourse — *področje pogovora*) → to every predicate corresponds a 0/1 logic function on $D$ (*vsakemu predikatu ustreza 0/1 logična funkcija v D*).

Later in the lecture (proof below): an interpretation consists of $D$, the meaning of the predicates (*pomen predikatov*) and the choice of the free variables (*izbira prostih*).

### Meaning of quantifiers (*pomen kvantifikatorjev*)

$$W = P(x) \lor \exists x\, Q(x, y) \land R(b, x)$$

The $x$ in $P(x)$, the $y$ in $Q(x, y)$ and the $x$ in $R(b, x)$ are free.

$W(x/a)$ — instead of the free $x$ we plug in $a$ (*namesto prostih x vstavim a*):

$$W(x/a) = P(a) \lor \exists x\, Q(x, y) \land R(b, a)$$

We don't touch the bound ones, nor $y$ (*ne dotikamo se vezanih, y*). This is **substitution** (*substitucija*).

- $\forall x\, W$ … $W$ (may have free $x$ — *ima (morda) proste x*) … $W(x/d)$
- $\exists x\, W$ … $W$ … $W(x/d)$

Meaning (*pomen*): —

### Equivalent predicate formulas (*enakovredne izjavne formule*)

Equivalent = equal in all possible interpretations (*v vseh možnih interpretacijah*): all of $\mathbb{N}$, $\mathbb{N} - \{0\}$, $\mathbb{N} - \{0, 1\}$, … We don't have to check all interpretations (*ne moramo preveriti vseh interpretacij*).

1. **Valid** (*splošno veljavna*):

$$
\begin{aligned}
p \Rightarrow (q \Rightarrow p) &\sim 1 \\
\forall x\, P(x) \Rightarrow (\exists y\, Q(y) \Rightarrow \forall x\, P(x)) &\sim 1 \\
\forall x\, P(x) \lor \neg \forall x\, P(x) &\sim 1
\end{aligned}
$$

2. **Unsatisfiable** (*neizpolnljiva*):

$$\forall x\, P(x) \land \neg \forall x\, P(x) \sim 0$$

**Example:** $\neg \forall x\, W$ and $\exists x\, \neg W$ are equivalent.

> [!check] Proof (*dokaz*)
> Say $\neg \forall x\, W$ is true … then $\forall x\, W$ is false …

From this:

$$
\exists x\, W \sim \exists x\, \neg\neg W \sim \neg \forall x\, \neg W
\qquad\qquad
\forall x\, \neg W \sim \neg \exists x\, W
$$

### Laws of predicate logic (*zakoni predikatnega računa*)

The laws from before still hold (+ some new ones — *zakoni od prej veljajo (+ še novi)*).

1. **De Morgan's laws** for quantifiers:

$$\neg \forall x\, W \sim \exists x\, \neg W \qquad \neg \exists x\, W \sim \forall x\, \neg W$$

2. Quantifiers of the same kind can be swapped (*istovrstne kvantifikatorje lahko zamenjamo*):

$$\forall x\, \forall y\, W \sim \forall y\, \forall x\, W \qquad \exists x\, \exists y\, W \sim \exists y\, \exists x\, W$$

3. **Distributivity** (*distributivnost*):

$$\forall x\, (W \land V) \sim \forall x\, W \land \forall x\, V \qquad \exists x\, (W \lor V) \sim \exists x\, W \lor \exists x\, V$$

The existential quantifier can't be distributed over a conjunction (and the universal not over a disjunction — *eksistenčnega ne moremo preko konjunkcije, in univerzalnega preko disjunkcije*). Example on $\mathbb{N}$ with $S(x)$ … $x$ is even (*sodo*), $L(x)$ … $x$ is odd (*liho*):

$$
\begin{aligned}
\exists x\, S(x) \land \exists x\, L(x) &\sim 1 \\
\exists x\, (S(x) \land L(x)) &\sim 0 \qquad \text{(not possible to distribute over a conjunction)}
\end{aligned}
$$

$$\forall x\, S(x) \lor \forall x\, L(x) \quad \text{vs.} \quad \forall x\, (S(x) \lor L(x)) \qquad \text{(not possible either — } \textit{tudi ni mogoče}\text{)}$$

#### Renaming variables (*preimenovanje spremenljivk*)

$$\forall x\, (P(w) \Rightarrow P(x)) \sim \forall y\, (P(w) \Rightarrow P(y))$$

For the bound $x$ I can use a new name (only not $w$ — *za vezan x lahko uporabim novo ime, samo ne w*).

**Claim** (*trditev*): if $y$ does not appear in $W$:

$$\forall x\, W \sim \forall y\, (W(x/y)) \qquad \exists x\, W \sim \exists y\, (W(x/y))$$

($\forall x\, W$ … $W$ … $W(x/y)$ … $\forall y\, (W(x/y))$.)

We don't rename free variables (but we do rename bound ones — *proste spremenljivke ne preimenujemo, vezane pa*).

**Example:**

$$\forall x\, \exists y\, (P(x, y) \Rightarrow \exists x\, Q(x, y) \lor \forall y\, R(x, y))$$

In the notebook the arrows mark which quantifier binds which occurrence: $\forall x$ binds the $x$ in $P(x, y)$ and $R(x, y)$, $\exists y$ binds the $y$ in $P(x, y)$ and $Q(x, y)$, $\exists x$ the $x$ in $Q$, $\forall y$ the $y$ in $R$. Renamed:

$$\forall u\, \exists v\, (P(u, v) \Rightarrow \exists x\, Q(x, v) \lor \forall y\, R(u, y))$$

This is the same as above (*to je isto kot zgoraj*).

**Example:**

$$\exists x\, P(x) \Rightarrow \forall x\, Q(x) \lor P(x) \land R(x) \lor S(y)$$

Don't touch the free $P(x)$, $R(x)$, $S(y)$ (*ne dotikaj se*); the bound ones get new variables (*novi spremenljivki*):

$$\sim \exists u\, P(u) \Rightarrow \forall z\, Q(z) \lor P(x) \land R(x) \lor S(y)$$

#### Quantifier and a formula without $x$

If $x$ does not appear, the following holds (*če se x ne pojavi, velja*): take $C$ in which $x$ does not appear free (*x se ne pojavi prosto*) and $W$ in which $x$ appears free (*x nastopa prosto*):

1. $\forall x\, (C \lor W) \sim C \lor \forall x\, W$ and $\exists x\, (C \lor W) \sim C \lor \exists x\, W$
2. $\forall x\, (C \land W) \sim C \land \forall x\, W$ and $\exists x\, (C \land W) \sim C \land \exists x\, W$

If we have $\forall x\, (\exists x\, P(x) \lor W)$ (*če*):

$$\forall x\, (\exists z\, P(z) \lor W)$$

— now $x$ doesn't appear in it at all (*sploh se ne pojavi x*).

$\land$ and $\lor$ are commutative, $\Rightarrow$ is not (*ni komutativna*):

$$
\begin{aligned}
\forall x\, (W \Rightarrow C)
&\sim \forall x\, ((\neg W) \lor C) \\
&\sim (\forall x\, \neg W) \lor C \\
&\sim \neg \exists x\, W \lor C \\
&\sim \exists x\, W \Rightarrow C
\end{aligned}
$$

**Example:** $\forall x\, P(y) \sim P(y)$ — it seems equivalent (*zdi se, kot da je enakovredna*).

**Claim** (*trditev*): if $x$ does not occur in $W$, then $\forall x\, W \sim W$ and $\exists x\, W \sim W$.

> [!check] Proof (*dokaz*)
> Let $\mathcal{I}$ be an interpretation ($D$, the meaning of the predicates, the choice of the free variables) in which $W$ is true for every $x$ ($\forall x$).
>
> Then $W(x/d)$ is true for every $d \in D$. But $W(x/d) = W$ (there is no $x$ here — *tukaj ni x*), so $W$ is true. $\blacksquare$
>
> (The other direction is similar — *v drugo smer je podobno*.)

## Questions

- [ ] What exactly is the meaning (*pomen*) of $\forall x\, W$ and $\exists x\, W$ in terms of $W(x/d)$? (left blank in the notebook)
- [ ] How does the proof that $\neg \forall x\, W \sim \exists x\, \neg W$ continue after "$\forall x\, W$ is false"?

## Connections

- Course: [[Discrete structures]]
- Previous lecture: [[2026-10-19 - Valid Arguments and Inference Rules - 3]] — domain of discourse, predicates, quantifiers and formalisation were introduced there
- [[De Morgan's Laws]]: the same laws in propositional logic and for quantifiers
- [[Propositional Logic]]: $p \Rightarrow (q \Rightarrow p)$ is a [[Tautology|tautology]] there
- [[Logical Equivalence]], [[Contradiction]] — equivalent, valid and unsatisfiable predicate formulas

## Sources

- Handwritten notes: [[Sources/discrete_structures/photoNotes/lectures/lecture4/lecture 4.pdf|lecture 4]]
- G. Fijavž, *Diskretne strukture* (FRI, 2015), sections 2.2–2.4 (pp. 42–51)
