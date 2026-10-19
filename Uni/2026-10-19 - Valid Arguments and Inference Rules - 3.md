---
type: "[[Lectures]]"
course: "[[Discrete structures]]"
date: 2026-10-19
week: "3"
---

# 2026-10-19 - Valid Arguments and Inference Rules

## Main Idea

Continuation of reasoning in [[Propositional Logic|propositional logic]] (*sklepanje v izjavnem računu*): an argument is valid exactly when the implication "conjunction of premises ⇒ conclusion" is a tautology. Instead of truth tables we prove validity with a sequence of formulas built from [[Inference Rule|inference rules]] (*pravila sklepanja*) — modus ponens, modus tollens, disjunctive and hypothetical syllogism, conjunction, simplification, addition — and three auxiliary arguments (*pomožni sklepi*): [[Conditional Proof|conditional proof]] (PS), [[Proof by Contradiction|proof by contradiction]] (RA) and [[Proof by Cases|proof by cases]] (AP). At the end: why propositional logic is not enough and the start of [[Predicate Logic|predicate logic]] (*predikatni račun*) — domain of discourse, predicates, [[Quantifier|quantifiers]] and formalising sentences.

## Notes

### Valid argument (*pravilen sklep*)

| $A_1$ | $A_2$ | $A_3$ | … | $A_n$ | $B$ | |
|:-:|:-:|:-:|:-:|:-:|:-:|---|
| 0 | 1 | 1 | … | 0 | | |
| → 1 | 1 | 1 | … | 1 | **1** | the argument is valid (*sklep je pravilen*) |
| → 1 | 1 | 1 | … | 1 | **0** | counterexample (*protiprimer*) → the argument is invalid (*sklep je nepravilen*) |
| ⋮ | | | | | | |
| 1 | 1 | 1 | … | 0 | | |

Only the rows where all premises are 1 (marked with →) matter.

**Theorem** (*izrek*): $A_1, A_2, \dots, A_n \models B$ if and only if (*natanko tedaj, ko*) the formula

$$(A_1 \land A_2 \land A_3 \land \dots \land A_n) \Rightarrow B$$

is a [[Tautology|tautology]].

> [!check] Proof (*dokaz*)
> $A_1, \dots, A_n \models B$ means:
> - $B$ is true in all the cases where all of $A_1, \dots, A_n$ are true,
> - i.e. $B$ is true in all the cases where $A_1 \land A_2 \land \dots \land A_n$ is true,
> - so it cannot happen that $(A_1 \land A_2 \land \dots \land A_n) \Rightarrow B$ is false (*laž*),
> - so $(A_1 \land A_2 \land \dots \land A_n) \Rightarrow B$ is a tautology. $\blacksquare$

**Example** (*zgled*):

- Premises (*predpostavki*): 1. If it rains, it is cloudy. (*Če dežuje, je oblačno.*) 2. It is raining. (*Dežuje.*)
- Conclusion (*zaključek*): 3. It is cloudy. (*Oblačno je.*)

With $d$ … it is raining, $o$ … it is cloudy:

$$
\begin{array}{ll}
1. & d \Rightarrow o \\
2. & d \\
\hline
3. & o
\end{array}
$$

| $d$ | $o$ | $d \Rightarrow o$ | $d$ | $o$ |
|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 1 | 0 | |
| 0 | 1 | 1 | 0 | |
| 1 | 0 | 0 | 1 | |
| 1 | 1 | **1** | **1** | **1** |

Only in the last row are both premises true → check the truth value of the conclusion there (*preveri logično vrednost zaključka*): it is 1.

The same with the theorem:

$$
\begin{aligned}
((d \Rightarrow o) \land d) \Rightarrow o
&\sim \neg((\neg d \lor o) \land d) \lor o \\
&\sim \neg(\neg d \lor o) \lor \neg d \lor o \\
&\sim (d \land \neg o) \lor \neg d \lor o \\
&\sim \underbrace{(d \lor \neg d \lor o)}_{1} \land \underbrace{(\neg o \lor \neg d \lor o)}_{1} \sim 1
\end{aligned}
$$

### Inference rules (*pravila sklepanja*)

| Rule | | Abbr. |
|---|---|:-:|
| $A,\ A \Rightarrow B \models B$ | modus ponens | MP |
| $A \Rightarrow B,\ \neg B \models \neg A$ | modus tollens | MT |
| $A \lor B,\ \neg B \models A$ | disjunctive syllogism (*disjunktivni silogizem*) | DS |
| $A \Rightarrow B,\ B \Rightarrow C \models A \Rightarrow C$ | hypothetical syllogism (*hipotetični silogizem*) | HS |
| $A,\ B \models A \land B$ | conjunction (*združitev*) | Zd |
| $A \land B \models A$ | simplification (*poenostavitev*) | Po |
| $A \models A \lor B$ | addition (*pridružitev*) | Pr |

**Modus ponens** — see the previous example (*glej prejšnji primer*).

**Modus tollens** — one and the same thing (*ena in ista reč*) written three ways:

$$
\begin{array}{lr}
A \Rightarrow B,\ \neg B \models \neg A & \text{MT} \\
\neg B \Rightarrow \neg A,\ \neg B \models \neg A & \text{MP} \\
\neg A \lor B,\ \neg B \models \neg A & \text{DS}
\end{array}
$$

(using [[Contraposition|contraposition]] and $A \Rightarrow B \sim \neg A \lor B$).

**Hypothetical syllogism** — truth table:

| $A$ | $B$ | $C$ | $A \Rightarrow B$ | $B \Rightarrow C$ | $A \Rightarrow C$ |
|:-:|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | **1** | **1** | **1** |
| 0 | 0 | 1 | **1** | **1** | **1** |
| 0 | 1 | 0 | 1 | 0 | |
| 0 | 1 | 1 | **1** | **1** | **1** |
| 1 | 0 | 0 | 0 | 1 | |
| 1 | 0 | 1 | 0 | 1 | |
| 1 | 1 | 0 | 1 | 0 | |
| 1 | 1 | 1 | **1** | **1** | **1** |

In every row where both premises are true, $A \Rightarrow C$ is true → the argument is valid.

**Conjunction (Zd)** — $A, B \models A \land B$: we need to check that $A \land B \Rightarrow A \land B$ is a tautology. This is always true (*to je vedno res*).

### Proof of validity (*dokaz pravilnosti sklepanja*)

A proof is a sequence of formulas $C_1, C_2, \dots$ ending with the conclusion, where each $C_i$:

- a) is one of the premises (*je ena od predpostavk*),
- b) is a tautology,
- c) is equivalent to one of the previous formulas in the sequence (*enakovreden enemu od predhodnih izrazov*),
- d) logically follows from previous formulas by one of the basic valid arguments (inference rules).

**Example:** $p \Rightarrow q,\ p \lor r,\ q \Rightarrow s,\ r \Rightarrow t,\ \neg s$ — does $t$ follow?

| | | |
|---|---|---|
| 1. | $p \Rightarrow q$ | premise (*predpostavka*) |
| 2. | $p \lor r$ | premise |
| 3. | $q \Rightarrow s$ | premise |
| 4. | $r \Rightarrow t$ | premise |
| 5. | $\neg s$ | premise |
| 6. | $p \Rightarrow s$ | HS(1, 3) |
| 7. | $\neg p$ | MT(5, 6) |
| 8. | $r$ | DS(2, 7) |
| 9. | $t$ | MP(4, 8) |

**Example:** $p \lor \neg q,\ \neg q \Rightarrow r \land s,\ \neg s \land r$ — does $p \land r$ follow?

| | | |
|---|---|---|
| 1. | $p \lor \neg q$ | premise |
| 2. | $\neg q \Rightarrow r \land s$ | premise |
| 3. | $\neg s \land r$ | premise |
| 4. | $r$ | Po(3) |
| 5. | $\neg s$ | Po(3) |
| 6. | $\neg r \lor \neg s$ | Pr(5) |
| 7. | $\neg(r \land s)$ | ∼ 6 |
| 8. | $q$ | MT(2, 7) |
| 9. | $p$ | DS(1, 8) |
| 10. | $p \land r$ | Zd(4, 9) |

**Example:**

1. I will go to the cinema, and in the evening I will do my homework. (*Šel bom v kino, zvečer pa bom naredil domačo nalogo.*)
2. If I go to the match and then also to the cinema, I won't be able to do my homework in the evening. (*Če grem na tekmo in nato še v kino, zvečer ne bom mogel narediti domače naloge.*)
3. I can't go to the match. (*Ne morem iti na tekmo.*) — conclusion

With $t$ … I go to the match, $k$ … I go to the cinema, $d$ … I do my homework; conclusion $\neg t$:

| | | |
|---|---|---|
| 1. | $k \land d$ | premise |
| 2. | $(t \land k) \Rightarrow \neg d$ | premise |
| 3. | $d$ | Po(1) |
| 4. | $\neg(t \land k)$ | MT(2, 3) |
| 5. | $\neg t \lor \neg k$ | ∼ 4 |
| 6. | $k$ | Po(1) |
| 7. | $\neg t$ | DS(5, 6) |

**Example:** does $q$ follow from $p, \neg p$? If I believe in nonsense, I can validly conclude anything (*če verjamem v neumnosti, lahko pravilno sklepam karkoli*).

| | | |
|---|---|---|
| 1. | $p$ | premise |
| 2. | $\neg p$ | premise |
| 3. | $p \land \neg p$ | Zd(1, 2) |
| 4. | $0$ | ∼ 3 |
| 5. | $0 \lor q$ | Pr(4) |
| 6. | $q$ | ∼ 5 |

### Auxiliary arguments (*pomožni sklepi*)

#### Conditional proof — PS (*pogojni sklep*)

Used when the conclusion of the argument has the form of an implication.

**Theorem:** $A_1, A_2, \dots, A_k \models B \Rightarrow C$ if and only if $A_1, A_2, \dots, A_k, B \models C$ ($B$ moves over to the premises).

> [!check] Proof
> $A_1, \dots, A_k \models B \Rightarrow C$ iff $(A_1 \land \dots \land A_k) \Rightarrow (B \Rightarrow C)$ is a tautology.
>
> $A_1, \dots, A_k, B \models C$ iff $(A_1 \land \dots \land A_k \land B) \Rightarrow C$ is a tautology.
>
> $$
> \begin{aligned}
> (A_1 \land \dots \land A_k) \Rightarrow (B \Rightarrow C)
> &\sim (\neg(A_1 \land \dots \land A_k) \lor \neg B) \lor C \\
> &\sim \neg(A_1 \land \dots \land A_k \land B) \lor C \\
> &\sim (A_1 \land A_2 \land \dots \land A_k \land B) \Rightarrow C \qquad \blacksquare
> \end{aligned}
> $$
>
> In the second step we factor out the negation (*izpostavimo negacijo*).

**Example:** $p \Rightarrow q \lor r$ and $\neg r$ — does $p \Rightarrow q$ logically follow?

| | | |
|---|---|---|
| 1. | $p \Rightarrow q \lor r$ | premise |
| 2. | $\neg r$ | premise |
| 3.1. | $p$ | premise PS (*pred. PS*) |
| 3.2. | $q \lor r$ | MP(3.1, 1) |
| 3.3. | $q$ | DS(2, 3.2) |
| 3. | $p \Rightarrow q$ | PS(3.1, 3.3) |

The same without PS (*isto brez PS*):

| | | |
|---|---|---|
| 1. | $p \Rightarrow q \lor r$ | premise |
| 2. | $\neg r$ | premise |
| 3. | $\neg p \lor q \lor r$ | ∼ 1 |
| 4. | $\neg p \lor q$ | DS(2, 3) |
| 5. | $p \Rightarrow q$ | ∼ 4 |

**Wrong example** (*napačen zgled*): once we return from the PS (lines 3.1–3.3), we may no longer use those lines for reasoning.

#### Proof by contradiction — RA (*sklep s protislovjem*, reductio ad absurdum)

Can be used whenever (*kadarkoli*), whatever the form of the conclusion.

**Theorem:** $A_1, A_2, \dots, A_k \models B$ if and only if $A_1, A_2, \dots, A_k, \neg B \models 0$.

> [!check] Proof
> $A_1, \dots, A_k \models B$ iff $(A_1 \land \dots \land A_k) \Rightarrow B$ is a tautology.
>
> $A_1, \dots, A_k, \neg B \models 0$ iff $(A_1 \land \dots \land A_k) \land \neg B \Rightarrow 0$ is a tautology.
>
> $$
> \begin{aligned}
> (A_1 \land \dots \land A_k) \land \neg B \Rightarrow 0
> &\sim \neg((A_1 \land \dots \land A_k) \land \neg B) \qquad (\text{"}p \Rightarrow 0 \sim \neg p\text{"}) \\
> &\sim \neg(A_1 \land \dots \land A_k) \lor B \\
> &\sim (A_1 \land \dots \land A_k) \Rightarrow B \qquad \blacksquare
> \end{aligned}
> $$

**Example:** $p \Rightarrow \neg(q \Rightarrow r),\ s \land q \Rightarrow r,\ s$ — does $\neg p$ follow?

**Searching for a counterexample** (*iskanje protiprimera*): we want all premises 1 and the conclusion $\neg p = 0$:

- $\neg p = 0$ → $p = 1$, and $s = 1$ (third premise);
- the first premise $p \Rightarrow \neg(q \Rightarrow r)$ with $p = 1$ needs $\neg(q \Rightarrow r) = 1$, i.e. $q \Rightarrow r = 0$ → $q = 1$, $r = 0$;
- then the second premise is $s \land q \Rightarrow r = 1 \Rightarrow 0 = 0$, not 1.

I didn't manage to find a counterexample (*nisem uspel najti protiprimera*) → this failure is exactly the contradiction that proves validity with proof by contradiction (*ta neuspeh je tisto protislovje, ki dokazuje veljavnost s sklepanjem s protislovjem*).

| | | |
|---|---|---|
| 1. | $p \Rightarrow \neg(q \Rightarrow r)$ | premise |
| 2. | $s \land q \Rightarrow r$ | premise |
| 3. | $s$ | premise |
| 4.1. | $\neg\neg p$ | premise RA |
| 4.2. | $p$ | ∼ 4.1 |
| 4.3. | $\neg(q \Rightarrow r)$ | MP(1, 4.2) |
| 4.4. | $q \land \neg r$ | ∼ 4.3 |
| 4.5. | $q$ | Po(4.4) |
| 4.6. | $\boxed{\neg r}$ | Po(4.4) |
| 4.7. | $s \land q$ | Zd(3, 4.5) |
| 4.8. | $\boxed{r}$ | MP(2, 4.7) |
| 4.9. | $r \land \neg r \sim 0$ | Zd(4.8, 4.6) |
| 4. | $\neg p$ | RA(4.1, 4.9) |

An unsuccessful search for a counterexample leads us to a valid argument (*neuspešno iskanje protiprimera nas pripelje do pravilnega sklepanja*).

#### Comparison (*primerjava*)

$$
\begin{array}{lll}
A_1, \dots, A_k \models B \Rightarrow C & ? & \\
A_1, \dots, A_k, B \models C & ? & \text{PS} \\
A_1, \dots, A_k, B, \neg C \models 0 & ? & \text{RA}
\end{array}
$$

In RA we write $B, \neg C$ (a comma instead of the conjunction $B \land \neg C$ — *namesto konjunkcije*). RA is the stronger tool (*močnejše orodje*).

#### Proof by cases — AP (*analiza primerov*)

Used when a premise has the form of a disjunction.

**Theorem:** $A_1, \dots, A_k, B_1 \lor B_2 \models C$ if and only if $A_1, \dots, A_k, B_1 \models C$ **and** $A_1, \dots, A_k, B_2 \models C$.

### Predicate logic (*predikatni račun*)

- Premises (simple propositions — *enostavni izjavi*): All computer science students can reason logically. (*Vsi študentje računalništva znajo logično sklepati.*) Kuzma the dwarf can't reason logically. (*Škrat Kuzma ne zna logično sklepati.*)
- Conclusion: Kuzma the dwarf is not a computer science student. (*Škrat Kuzma ni študent rač.*)

In propositional logic this argument is invalid (*v izjavnem računu je sklep napačen*): each sentence is just a separate variable. Predicate logic deals with the internal structure of propositions (*se ukvarja z notranjo zgradbo izjav*).

#### Domain of discourse and predicates (*področje pogovora in predikati*)

- **Domain of discourse** (*področje pogovora*, p.p.): what are we talking about (*o čem se pogovarjamo?*) — people, animals, $\mathbb{N}$, people and dwarves and other fairy-tale creatures …
- **Predicates** (*predikati*): logic functions that take constants from the domain of discourse as arguments.

![[Discrete structures 3 predicate as function.svg]]

One-place predicates $p(x)$:

- $x$ is bald (*je plešast*)
- $x$ is a prime number (*je praštevilo*)
- $x$ is a reptile (*je plazilec*)

Predicates can have several places (*predikati so lahko večmestni*): $p(x_1, x_2)$, e.g. $D(x, y)$:

- $x$ is the grandfather of $y$ (*je dedek od*)
- $x$ divides $y$ (*deli*)

#### Variables and formulas (*spremenljivke in formule*)

$V(x, y, z)$ … $z$ is the sum of $x$ and $y$ (*je vsota*) $\sim (x + y = z)$ — a three-place predicate (*tromestni predikat*).

#### Quantifiers (*kvantifikatorja*)

- $\forall$ — universal (*univerzalni*)
- $\exists$ — existential (*eksistenčni*)

We use them to turn a formula into a proposition (*da formulo spremenimo v izjavo*). Another way to get a proposition from a predicate is to plug in a constant: $p(x)$ → $p(\text{Gašper})$.

With $p(x)$ … $x$ is bald:

- $\forall x\, p(x)$ → every person is bald (*vsak človek je plešast*)
- $\exists x\, p(x)$ → there exists a person who is bald (*obstaja človek, ki je plešast*)

These are propositions (they have a truth value — *imata logično vrednost*).

#### Formalisation (*formalizacija*)

1. "Some politicians are dishonest." (*Nekateri politiki so nepošteni.*)
2. "No politician is dishonest." (*Noben politik ni nepošten.*)
3. "All politicians are dishonest." (*Vsi politiki so nepošteni.*)
4. "All politicians are honest." (*Vsi politiki so pošteni.*)

Domain of discourse: people.

- $p(x)$ … $x$ is a politician, $\neg p(x)$ … $x$ is not a politician
- $N(x)$ … $x$ is dishonest (*nepošten*), $\neg N(x)$ … $x$ is honest

$$
\begin{array}{ll}
1. & \exists x\,(p(x) \land N(x)) \\
2. & \neg \exists x\,(p(x) \land N(x)) \\
3. & \forall x\,(p(x) \Rightarrow N(x)) \\
4. & \forall x\,(p(x) \Rightarrow \neg N(x))
\end{array}
$$

Typically (*tipično*): existential statements go with conjunctions, universal statements with implications.

## Questions

- [ ] 

## Connections

- Course: [[Discrete structures]]
- Previous lecture: [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]] — valid arguments and counterexamples were introduced there
- Laws used in the proofs: [[De Morgan's Laws]], [[Contraposition]]

## Sources

- Handwritten notes: [[Sources/discrete_structures/photoNotes/lectures/lecture3/lecture 3.pdf|lecture 3]]
- G. Fijavž, *Diskretne strukture* (FRI, 2015), sections 1.7–1.8 and 2.1 (pp. 28–41)
