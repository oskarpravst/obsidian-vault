---
type: "[[Lectures]]"
course: "[[Discrete structures]]"
date: 2026-11-23
week: "8"
---

# 2026-11-23 - Partial Orders, Functions and Cardinality of Sets

## Main Idea

The lecture finishes relations with **order relations** (*relacije urejenosti*): a [[Partial Order|partial order]] (*delna urejenost*) is reflexive, antisymmetric and transitive, and a [[Linear Order|linear order]] (*linearna urejenost*) is a partial order that is also connected. A finite partial order is drawn as a [[Hasse Diagram|Hasse diagram]] (*Hassejev diagram*), which keeps only the immediate successors (*neposredni nasledniki*). Then **functions** (*preslikave*): a [[Function|function]] is a functional relation defined on the whole set $A$. It can be [[Injective Function|injective]], [[Surjective Function|surjective]] or [[Bijective Function|bijective]]. The [[Inverse Relation|inverse relation]] $f^{-1}$ is a function exactly when $f$ is a bijection, and the [[Composition of Functions|composition]] (*kompozitum*) is the [[Composition of Relations|product of relations]] with the factors swapped. The last part is about the **cardinality of sets** (*moč množic*): formulas for finite sets, the [[Inclusion–Exclusion Principle|principle of inclusion and exclusion]] (*načelo vključitve in izključitve*), the [[Pigeonhole Principle|Dirichlet principle]], comparing infinite sets with injections, the Cantor–Schröder–Bernstein theorem, [[Countable Set|countable]] and uncountable sets, and [[Cantor's Theorem|Cantor's theorem]] $|A| < |\mathcal{P}A|$. The goal is to show that there are real numbers that no program can compute (*neizračunljiva realna števila*).

## Notes

### Order relations (*relacije urejenosti*)

If $R$ is

1. reflexive (*refleksivnost*),
2. antisymmetric (*antisimetričnost*),
3. transitive (*tranzitivnost*),

then $R$ **partially orders** $A$ (*$R$ delno ureja $A$*).

$R$ **linearly orders** $A$ (*linearno ureja $A$*) if it partially orders $A$ and is connected (*je sovisna*).

Examples (*zgledi*):

- Inclusion ($\subseteq$) partially orders every family of sets (*vsebovanost delno ureja vsako družino množic*).
- Divisibility ($\mid$) partially orders $\{1, 2, 3, \dots\}$.
  $a \mid b$ … $a$ divides $b$ … the equation $ax = b$ has an integer solution (*ima celoštevilsko rešitev*). We do not talk about quotients (*ne pogovarjamo se o kvocientih*).
  Why is divisibility not a partial order on the integers (*zakaj deljivost ni pri celih številih*)? $5 \mid -5$ and $-5 \mid 5$, so antisymmetry does not work (*antisimetričnost ne dela*).
  In $\{1, 2, 3, \dots\}$: if $a \mid b$ and $b \mid a$, then $a$ and $b$ are equal (*sta enaka*):
  $$a \cdot x = b, \quad b \cdot y = a \;\Rightarrow\; b \cdot y \cdot x = b$$
- $\le$ linearly orders $\mathbb{N}, \mathbb{Z}, \mathbb{Q}, \mathbb{R}$.
- $\subseteq$ and $\mid$ are not connected relations (*nista sovisni relaciji*): $\{a\}$ and $\{b\}$ are incomparable (*neprimerljivi*) for $\subseteq$, and so are $3$ and $5$ for $\mid$. On the set $\{1, 2, 2^2, 2^3, 2^4, 2^5, \dots\}$, however, divisibility is connected.
- $\mathrm{id}_A$ partially orders $A$.

#### Notation (*Hassejev diagram*)

$\preceq$ is the generic sign for a partial order (*generični znak za delno urejenost*); the notebook also writes it as $\trianglelefteq$. If $\preceq$ is a partial order in $A$:

- $a \preceq b$ — "$a$ is below $b$" (*"$a$ je pod $b$"*)
- $a \prec b$ … $a \preceq b$ and $a \ne b$ — "$a$ is strictly below $b$" (*"$a$ je strogo pod $b$"*)
- $a \prec b \preceq c$ … $a \prec b$ and $b \preceq c$

$y$ is an **immediate predecessor** of $x$ (*neposredni predhodnik*), $x$ an **immediate successor** of $y$ (*neposredni naslednik*):

$$x \prec\!\!\cdot\; y \Leftrightarrow x \prec y \text{ and } \forall z \in A:\, (x \preceq z \preceq y \Rightarrow z = x \lor z = y)$$

- $\le$ in $\mathbb{N}$: $3 \prec\!\!\cdot\; 4$ … $3 < 4$ and for every $n$ with $3 \le n \le 4$ we have $n = 3$ or $n = 4$.
- $\le$ in $\mathbb{Q}$: $a \prec\!\!\cdot\; b$ … $a < b$ and for every $q$ with $a \le q \le b$ we have $q = a$ or $q = b$. There are no such pairs (*takih parov ni*), since
  $$a < \frac{a + b}{2} < b$$

#### Hasse diagram (*diagram delne urejenosti*)

$A$ is partially ordered by $\preceq$. The elements of $A$ are points in the plane (*točke v ravnini*). If $a \prec\!\!\cdot\; b$, $a$ is drawn lower than $b$, … (the rest is missing in the notebook — *manjka*; textbook p. 100: for every such pair we draw a rising line between $a$ and $b$, and $a \preceq b$ exactly when we can get from $a$ to $b$ along a rising path).

Examples (*zgledi*):

$\mid$ in $\{1, 2, 3, 4, 5, 6\}$ — the numbers are arranged by levels (*števila so porazdeljena po nivojih*); level 1 are the primes (*so praštevila*). Multiplying by 2, 3 and 5 goes in different directions (*množenje z 2, množenje s 3, množenje s 5*):

![[Discrete structures 8 Hasse divisibility 1 to 6.svg]]

$\subseteq$ in the set $\mathcal{P}\{1, 2, 3\}$: $\{1\}$ is not an immediate predecessor of $\{1, 2, 3\}$, since $\{1\} \subset \{1, 2\} \subset \{1, 2, 3\}$.

![[Discrete structures 8 Hasse power set.svg]]

$\le$ in the set of natural numbers:

![[Discrete structures 8 Hasse natural numbers.svg]]

"Divides" in the set of divisors of 60 (*deli v množici deliteljev št. 60*), $\{1, 2, 3, 4, 5, 6, 10, 12, 15, 20, 30, 60\}$. The level says how many primes there are in the product (*koliko praštevil imam pri produktu*). The arrows ↑ are the relations, i.e. the graph of the relation (*z ↑ so relacije, graf relacije*); the notebook draws only a few of them:

![[Discrete structures 8 Hasse divisors of 60.svg]]

An algorithm can be more time-efficient (*časovno učinkovitejši*) or use as little space as possible (*čim manj prostora*) → then it needs more time (*več časa*). How fast can I determine whether two elements are in relation (*kako hitro lahko določim, ali sta dva elementa v relaciji*)? The Hasse diagram has little data, but queries take more time (*Hassejev diagram z malo podatki, poizvedbe so časovno potratnejše*); the graph of the relation uses more space (*graf relacije potratnejši*).

#### Equivalence relation vs. partial order on formulas

Equivalence relation (*ekvivalenčna relacija*), relation of partial order (*relacija delne urejenosti*). An equivalence class from the last lecture:

$$[p \Rightarrow q] = \{p \Rightarrow q,\; \neg q \Rightarrow \neg p,\; \neg p \lor q,\; \neg p \lor q \lor (s \land \neg s), \dots\}$$

$\vdash$: $I \vdash J$ iff (*ntk.*) $I \Rightarrow J$ is a [[Tautology|tautology]] (*je tavtologija*). Is this relation a partial order (*ali je ta relacija delna urejenost*)? It is reflexive, transitive by the hypothetical syllogism (*hipotetični silogizem*), but antisymmetry fails (*antisimetrija crkne*):

$$p \Rightarrow q \vdash \neg q \Rightarrow \neg p, \quad \text{but (\textit{toda})} \quad \neg q \Rightarrow \neg p \vdash p \Rightarrow q, \quad p \Rightarrow q \ne \neg q \Rightarrow \neg p$$

So it is not antisymmetric (*ni antisimetrična*) and not a partial order in the set of propositional expressions (*ni delna urejenost v množici izjavnih izrazov*). It is, however, a partial order of the equivalence classes (*je pa delna urejenost ekvivalentnih razredov*).

### Functions (*preslikave*)

A relation $f \subseteq A \times B$ is a **function from $A$ to $B$** (*preslikava iz $A$ v $B$*) if:

1. $f$ is functional (*enolična*),
2. $D_f = A$,
3. ($Z_f \subseteq B$).

$R$ is functional … $\forall x, y, z:\, xRy$ and $xRz \Rightarrow y = z$.

We also write $f: A \to B$, where $D_f = A$ (the whole set $A$ — *cela množica $A$*). Instead of $(x, y) \in f$ or $x f y$ we write $y = f(x)$ whenever $f$ is a function (*kadar bo $f$ preslikava*).

$$f: \underset{D_f}{A} \to \underset{\text{codomain of } f}{B}$$

$Z_f$ … the range of $f$ (*zaloga vrednosti*). The set of functions from $A$ to $B$ — missing in the notebook (*manjka*); textbook p. 104: $B^A = \{f \mid f: A \to B\}$.

#### Properties of functions (*lastnosti preslikav*)

$f: A \to B$.

1. $f$ is **injective** (*injektivna*) if $\forall x, y \in A:\, (f(x) = f(y) \Rightarrow x = y)$, or $x \ne y \Rightarrow f(x) \ne f(y)$.
2. $f$ is **surjective** (*surjektivna*) if $Z_f = B$ (we also say that $f$ is a function from $A$ **onto** $B$ — *preslikava iz $A$ na $B$*).
3. $f$ is **bijective** (*bijektivna*) if it is injective and surjective.

Notation and display (*zapis in prikaz*), all equivalent (*enakovredni*):

| | |
|---|---|
| extensional (*ekstenzionalni*) | $(x, y) \in f$ |
| relational (*relacijski*) | $x f y$ |
| functional (*funkcijski*) | $y = f(x)$ |

![[Discrete structures 8 maps to.svg]]

Examples (*zgledi*):

- $\exp: \mathbb{R} \to \mathbb{R}$ is an injective function from $\mathbb{R}$ to $\mathbb{R}$. It can be seen from the graph, since it is strictly increasing (*iz grafa se vidi, ker strogo narašča*).
- $\sin: \mathbb{R} \to \mathbb{R}$ is a function from $\mathbb{R}$ to $\mathbb{R}$. $2$ does not belong to $Z_f$ (so it is not surjective). It is periodic → not injective (*periodična → ni injektivna*).
- $\log: (0, \infty) \to \mathbb{R}$ is a bijective function from $(0, \infty)$ to $\mathbb{R}$. Strictly increasing — injective.
- **Careful** (*pazi!*): in DS we do not write $\log: \mathbb{R} \to \mathbb{R}$ or $\tan: \mathbb{R} \to \mathbb{R}$ (they are not defined on the whole of $\mathbb{R}$).

More examples:

- $\mathrm{id}_A: A \to A$, the identity on $A$ (*identiteta na $A$*), $\mathrm{id}_A(x) = x$, is bijective.
- $p_i: A_1 \times \dots \times A_n \to A_i$, the projection onto the $i$-th component (*projekcija na $i$-to komponento*), $p_i((a_1, \dots, a_n)) = a_i$, is surjective.

  ![[Discrete structures 8 projection.svg]]

- $A_1 \subseteq A$, $i = \mathrm{id}_A|_{A_1}$: $i: A_1 \hookrightarrow A$, $i(x) = x$ is injective — the embedding of $A_1$ in $A$ (*vložitev $A_1$ v $A$*).
- $R \subseteq A \times A$ an [[Equivalence Relation|equivalence relation]], $p: A \to A/R$, $p(x) = R[x]$ is surjective — the natural projection (*naravna projekcija*).
- $A \subseteq B$, $\chi_A: B \to \{0, 1\}$,
  $$\chi_A(x) = \begin{cases} 1, & x \in A \\ 0, & x \notin A \end{cases}$$
  the characteristic function of the set $A$ (in $B$) (*karakteristična funkcija množice $A$*).

  ![[Discrete structures 8 characteristic function.svg]]

- $\emptyset$, the empty function (*prazna preslikava*): $\emptyset: \emptyset \to B$.

#### Inverse function (*inverzna preslikava*)

We know $f^{-1}$ as a relation (*poznamo kot relacijo*): $f: A \to B$, $f \subseteq A \times B$, so $f^{-1} \subseteq B \times A$. When is $f^{-1}: B \to A$ (*kdaj je*)?

**Claim** (*trditev*): $f: A \to B$.

1. $f^{-1}$ is functional when (iff) $f$ is injective (*$f^{-1}$ je enolična, ko je $f$ injektivna*).

   $$
   \begin{aligned}
   f^{-1} \text{ functional} \;&\ldots\; \forall x \in B\, \forall y, z \in A:\, x f^{-1} y \text{ and } x f^{-1} z \Rightarrow y = z \\
   &\ldots\; \forall y, z \in A\, \forall x \in B:\, y f x \text{ and } z f x \Rightarrow y = z \\
   &\ldots\; \forall y, z \in A\, \forall x \in B:\, x = f(y) \text{ and } x = f(z) \Rightarrow y = z \\
   &\ldots\; \forall y, z:\, f(y) = f(z) \Rightarrow y = z
   \end{aligned}
   $$

   This is injectivity ($f$ is injective): $f(x) = f(y) \Rightarrow x = y$.

2. $f^{-1}: B \to A$ exactly when $f$ is bijective (*natanko tedaj, ko je $f$ bijektivna*).

   $$
   \begin{aligned}
   f \text{ bijective} \;&\ldots\; f \text{ injective and } f \text{ surjective} \\
   &\ldots\; f^{-1} \text{ functional and } Z_f = B \\
   &\ldots\; f^{-1} \text{ functional and } D_{f^{-1}} = B \\
   &\ldots\; f^{-1}: B \to A
   \end{aligned}
   $$

#### Composition of functions (*kompozitum preslikav*)

$f \subseteq A \times B$ and $g \subseteq B \times C$ (what we want — *to želimo*: $f: A \to B$, $g: B \to C$), so $f * g \subseteq A \times C$.

$$g \circ f = f * g$$

$$
\begin{aligned}
z = (g \circ f)(x) \;&\ldots\; x\,(g \circ f)\,z \;\ldots\; x\,(f * g)\,z \\
&\ldots\; \exists y:\, (x f y \text{ and } y g z) \quad (f, g \text{ are functions — \textit{preslikavi}}) \\
&\ldots\; \exists y:\, (y = f(x) \text{ and } z = g(y)) \\
&\ldots\; z = g(f(x))
\end{aligned}
$$

#### Properties of the composition (*lastnosti kompozituma*)

**Claim:** let $f: A \to B$. Then

$$f \circ \mathrm{id}_A = \mathrm{id}_B \circ f = f$$

The composition is associative (*kompozitum je asociativen*): $f: A \to B$, $g: B \to C$, $h: C \to D$; $h \circ (g \circ f): A \to D$ and $(h \circ g) \circ f: A \to D$, and

$$h \circ (g \circ f) = (h \circ g) \circ f = h \circ g \circ f$$

without proof (*brez dokaza*); it is the same as $(f * g) * h = f * (g * h)$ for relations.

**Claim:** $f: B \to C$, $g: A \to B$.

1. $f, g$ injective $\Rightarrow f \circ g$ injective
2. $f, g$ surjective $\Rightarrow f \circ g$ surjective
3. $f \circ g$ injective $\Rightarrow g$ injective
4. $f \circ g$ surjective $\Rightarrow f$ surjective

Example: $f: \mathbb{N} \to \mathbb{N}$, $g: \mathbb{N} \to \mathbb{N}$,

$$f: n \mapsto \begin{cases} n - 1, & n \ge 1 \\ 3, & n = 0 \end{cases} \qquad g: n \mapsto n + 1 \;\text{(injective)}$$

![[Discrete structures 8 composition.svg]]

$f \circ g = \mathrm{id}_{\mathbb{N}}$ is bijective, although $g$ is not surjective and $f$ is not injective.

**Claim:** let $f: B \to A$, $g: A \to B$. If $f \circ g = \mathrm{id}_A$ and $g \circ f = \mathrm{id}_B$, then $f$ and $g$ are bijections and $g = f^{-1}$.

- $\mathrm{id}_A = f \circ g: A \to A$ → surjective and injective, so $f$ is surjective and $g$ is injective (by 4. and 3.).
- $\mathrm{id}_B = g \circ f: B \to B$ → surjective and injective, so $g$ is surjective and $f$ is injective.

$f$ is a bijection and $g$ is a bijection (*bijektivni preslikavi*). Then $f: B \to A$, $f^{-1}: A \to B$ and

$$f^{-1} = f^{-1} \circ \mathrm{id}_A = f^{-1} \circ (f \circ g) = (f^{-1} \circ f) \circ g = \mathrm{id}_B \circ g = g \qquad \blacksquare$$

#### Relations in the set of functions (*relaciji v množici preslikav*)

For functions $\mathbb{R} \to \mathbb{R}$:

- $f \preceq g$ iff (*ntk.*) for all $x \in \mathbb{R}$: $f(x) \le g(x)$.
- $f \trianglelefteq g$ iff there exists $M \in \mathbb{R}$ such that for all $x \ge M$: $f(x) \le g(x)$ — from some point on, one is greater than or equal to the other (*od nekje naprej ena večja ali enaka kot druga*).

$\mathrm{id}_{\mathbb{R}} \preceq \exp$ … $x \le e^x$ for every $x \in \mathbb{R}$.

![[Discrete structures 8 eventually below.svg]]

Are $\preceq$ and $\trianglelefteq$ partial orders (*delni urejenosti*)? Are they even linear orders (*celo linearno urejeni*)? (left open — see Questions)

### Cardinality of finite sets (*moč končnih množic*)

For a finite set $A$, $|A|$ denotes the number of elements or the **cardinality** (*moč*) of $A$. (Side note in the notebook next to $|\;|$: "distance from the start of the set" — *razdalja od začetka množice*.)

$A$ and $B$ are **equinumerous** (*enako močni*), $A \sim B$, if $|A| = |B|$.

Examples:

1. $|\emptyset| = 0$, $|\{\mathbb{N}\}| = 1$
2. $|\{1, 2\}| = 2$
3. $|\{\{0, 1\}\}| = 1$

**Claim:** $A, B, C$ are finite sets.

1. $|A \times B| = |A| \cdot |B|$ — the basic theorem of combinatorics (*osnovni izrek kombinatorike*)
2. $|\{f;\, f: A \to B\}| = |B^A| = |B|^{|A|}$
3. $|\mathcal{P}A| = 2^{|A|}$

Cardinality of the difference (*moč razlike*):

4. If $B \subseteq A$, then $|A \setminus B| = |A| - |B|$.

   ![[Discrete structures 8 difference.svg]]

   If $B \not\subseteq A$: $A \cap B \subseteq A$, and
   $$|A \setminus B| = |A \setminus (A \cap B)| = |A| - |A \cap B|$$
   because
   $$
   \begin{aligned}
   A \setminus (A \cap B) &= A \cap (A \cap B)^c = A \cap (A^c \cup B^c) \\
   &= (A \cap A^c) \cup (A \cap B^c) = A \cap B^c = A \setminus B
   \end{aligned}
   $$

5. If $A \cap B = \emptyset$, then $|A \cup B| = |A| + |B|$.

   ![[Discrete structures 8 disjoint union.svg]]

   In general (*v splošnem*):
   $$|A \cup B| = |A| + |B| - |A \cap B|$$

   ![[Discrete structures 8 union of two sets.svg]]

   $$A \cup (B \setminus A) = A \cup (B \cap A^c) = (A \cup B) \cap (A \cup A^c) = A \cup B$$
   $$|A \cup B| = |A \cup (B \setminus A)| = |A| + |B \setminus A| = |A| + |B| - |A \cap B|$$
   ($|B \setminus A|$ was derived before — *izpeljali prej*.)

   The inclusion–exclusion rule (*pravilo vključitev–izključitev*), remembered with the Audi logo:
   $$|A \cup B| + |A \cap B| = |A| + |B|$$

6. $$|A \cup B \cup C| = |A| + |B| + |C| - |A \cap B| - |A \cap C| - |B \cap C| + |A \cap B \cap C|$$

   ![[Discrete structures 8 union of three sets.svg]]

#### Principle of inclusion and exclusion (*načelo vključitve in izključitve*)

**Theorem** (*izrek*): $A$ is a finite set and $A_1, A_2, \dots, A_n \subseteq A$. Then

$$|A_1 \cup A_2 \cup \dots \cup A_n| = |A_1| + |A_2| + \dots + \text{(missing — \textit{manjka})}$$

Textbook p. 124–125 (Trditev 6.2):

$$|A_1 \cup \dots \cup A_n| = \sum_{k=1}^{n} (-1)^{k+1} \sum_{1 \le i_1 < \dots < i_k \le n} |A_{i_1} \cap \dots \cap A_{i_k}|$$

**Task** (*naloga*): how many numbers in the integer interval $[1..96]$ are divisible by 6 and divisible neither by 24 nor by 32? Use smart notation (*uporaba pametnih oznak*):

$A_k$ … the set of numbers between 1 and 96 that are divisible by $k$. We are interested in (*to nas zanima*):

$$
\begin{aligned}
|A_6 \setminus (A_{24} \cup A_{32})| &= |A_6| - |A_6 \cap (A_{24} \cup A_{32})| \\
|A_6 \cap (A_{24} \cup A_{32})| &= |(A_6 \cap A_{24}) \cup (A_6 \cap A_{32})| \\
&= |A_6 \cap A_{24}| + |A_6 \cap A_{32}| - |A_6 \cap A_{24} \cap A_{32}|
\end{aligned}
$$

$$
\begin{aligned}
&|A_6| - |A_6 \cap A_{24}| - |A_6 \cap A_{32}| + |A_6 \cap A_{24} \cap A_{32}| \\
&= |A_6| - |A_{24}| - |A_{96}| + |A_{96}| \qquad (96 = \operatorname{lcm}(6, 32)) \\
&= \left\lfloor \frac{96}{6} \right\rfloor - \left\lfloor \frac{96}{24} \right\rfloor = 16 - 4 = 12
\end{aligned}
$$

#### Dirichlet principle (*Dirichletov princip*)

**Theorem:** let $A$ be a finite set and $f: A \to A$. Then the following statements are equivalent (*enakovredne*); this separates finite sets from infinite ones (*loči končne od neskončnih množic*):

1. $f$ is injective
2. $f$ is surjective
3. $f$ is bijective

If $B$ is an infinite set and $f: B \to B$, the mentioned properties are in general not equivalent (*omenjene lastnosti v splošnem niso enakovredne*).

Example: $f: A \to B$, if $A, B$ are finite and $|A| = |B|$: $f$ surjective, $f$ injective, $f$ bijective are equivalent properties. Cars and garages:

![[Discrete structures 8 cars and garages.svg]]

- surjective: every garage has at least one car (*v vsaki garaži vsaj en avto*),
- injective: every garage has at most one car (*največ en avto*),
- bijective: every garage has exactly one car (*natančno en avto*).

A queue $[1\;2\;3\;4]$: every second one leaves (*vsako sekundo eno vn*) → after 4 seconds it is over (*po 4 sek konec*). A queue $[0\;1\;2\;3\;\dots]$: the same (*—||—*) → in the future, after infinite time, it depends on the initial conditions (*po neskončnem času odvisno od začetnih pogojev*).

Goal (*cilj*): show that there are uncomputable real numbers (*neizračunljiva realna števila*) — there is no procedure for them (*ne obstaja postopek*).

### Comparing infinite sets

```python
print('1')
print('2')
print('3')
```

— a program that prints $\mathbb{N}$ (*program, ki izpiše $\mathbb{N}$*).

```python
print('0')
print(',')
while True: print('7')
```

Real numbers that we cannot write down with a program are uncomputable (*realna št., ki jih ne moremo zapisati s programom, so neizračunljiva*).

> [!note] From the professor's slides (p. 2): infinite sets, the computing goal (*neskončne množice, računalniški cilj*)
> A real number $x$ is **computable** (*izračunljivo*) if there exists a computer program that prints $x$.
> - $123$, $\pi$, $0.77777\ldots$ are computable real numbers.
> - Every natural number is computable.
> - We allow programs that do not terminate (i.e. loop forever — *se zaciklajo*).
> - What is a computer program? What does it mean to print $x$?
>
> A real number $x$ is **uncomputable** (*neizračunljivo*) if there is no computer program that prints $x$.
>
> **Theorem:** there exist uncomputable real numbers. In fact, the vast majority of real numbers are uncomputable.

Two sets $A$ and $B$ are **equinumerous** (*enako močni*), $A \sim B$, if there exists a bijective function from $A$ to $B$. We also write $|A| = |B|$. *(slides, p. 3)*

$B$ is **at least as large** (*kvečjemu močnejša*, has at least as many elements as $A$), $|A| \le |B|$, if there exists an injective function from $A$ to $B$. These are no longer numbers (*to niso več števila*).

$|A| < |B|$ means $|A| \le |B|$ and $|A| \ne |B|$:

- there exists an injective function $A \to B$,
- there is no injective function $B \to A$ (Dirichlet principle).

On the slides (p. 3): $|A| < |B|$ means that there exists an injective function from $A$ to $B$ and that there is **no bijective** function from $A$ to $B$.

**Theorem (Cantor–Schröder–Bernstein):** $|A| = |B|$ iff $|A| \le |B|$ and $|B| \le |A|$. This is not trivial (*to ni trivialno*). So a bijection is not strictly needed (*bijekcija ni nujno potrebna*, slides p. 4): two injections, one in each direction, are enough.

**Theorem (trichotomy — *o trihotomiji*)** *(slides, p. 4)*: any two sets are comparable by cardinality (*vsaki dve množici sta primerljivi po moči*). For arbitrary sets $A$ and $B$, exactly one of $|A| < |B|$, $|A| = |B|$ or $|A| > |B|$ holds.

### Countable and uncountable sets (*števne in neštevne množice*)

- $A$ is **countably infinite** (*števno neskončna*) if $|A| = |\mathbb{N}|$.
- $B$ is **countable** (*števna*) if it is countably infinite or finite.
- $C$ is **uncountable** (*neštevna*) if it is not countable.

Examples of countably infinite sets: $|\mathbb{N}|, |\mathbb{Z}|, |\mathbb{Q}|$. The slides (p. 5) also list:

- the set of syntactically correct Java programs (*množica sintaktično pravilnih javanskih programov*),
- the set of computable real numbers (*množica izračunljivih realnih števil*).

$$\mathbb{N} \overset{\text{inj}}{\hookrightarrow} \mathbb{Z} \overset{\text{inj}}{\hookrightarrow} \mathbb{Q}, \qquad n \mapsto n, \qquad n \mapsto \frac{n}{1}$$

$$(-1)^s \frac{p}{q} \;\longmapsto\; 2^s\, 3^p\, 5^q \quad \text{(injective)}$$

$$\text{ASCII Java programs} \overset{\text{inj}}{\longrightarrow} \mathbb{N} \longrightarrow \text{computable real number (\textit{izračunljivo } \mathbb{R} \text{ število})}$$

$1, 2, 3 \overset{\text{inj}}{\hookrightarrow}$ `print 1`, `print 2`, `print 3`.

$x$ a computable real number: we choose the shortest program that prints $x$; among those, I choose the first one in alphabetical order (*med njimi izberem po abc prvega*).

**Proposition** (*trditev*): if $A$ and $B$ are countable, then $A \cup B$ is countable too.

#### How do we get to uncountable sets (*kako do neštevnih množic*)?

**Theorem:** for every set $A$: $|A| < |\mathcal{P}A|$.

- $A$ finite: $n < 2^n$ for all $n \in \mathbb{N}$.
- $A$ infinite: $|A| < |\mathcal{P}A|$ … there exists an injection $A \hookrightarrow \mathcal{P}A$ and there is no injection $\mathcal{P}A \to A$.

$$a \in A \;\overset{\text{inj}}{\longmapsto}\; \{a\} \in \mathcal{P}A$$

Suppose (*denimo*) there exists an injective $f: \mathcal{P}A \to A$. Then there exists a surjective $g: A \to \mathcal{P}A$:

- if $a \in A \cap Z_f$, then $g(a) = f^{-1}(a)$ (the original — *original*),
- if $a \in A \setminus Z_f$, then $g(a) = \emptyset$.

Let us say there exists a surjective $g: A \to \mathcal{P}A$, $a \mapsto g(a) \in \mathcal{P}A$, $g(a) \subseteq A$.

- $a \in A$ is **good** (*dober*) if $a \in g(a)$,
- $a \in A$ is **bad** (*slab*) if $a \notin g(a)$.

$S = \{s \in A;\, s \text{ is bad}\}$. I claim $S \notin Z_g$ (it is not among the images — *slike*). Why (*zakaj*)?

If $S \in Z_g$, then $\exists x \in A:\, g(x) = S$. $x$ is bad or good:

- if $x$ is bad, then $x \notin g(x)$ and $x \in S$ → this is nonsense (*to je neumnost*) ⨳
- if $x$ is good, then $x \in g(x)$ and $x \notin S$ ⨳

Examples of uncountable sets (*zgledi neštevnih množic*):

- $\mathcal{P}\mathbb{N}$
- $\mathbb{R}$

$$[0, 1] \to \mathbb{R},\; x \mapsto x \qquad\qquad \mathbb{R} \to \left(-\tfrac{\pi}{2}, \tfrac{\pi}{2}\right),\; x \mapsto \arctan x$$

A number $x \in (0, 1)$ in binary:

$$x_{(2)} = 0.110101100110001\dots$$

($0.09999\ldots = 0.10000\ldots$) — the positions of the ones give a subset of $\mathbb{N}$:

$$\{0, 1, 3, 5, 6, 9, 10, 14, \dots\}$$

> [!note] From the professor's slides (p. 6)
> Examples of uncountable sets:
> - $\mathcal{P}\mathbb{N}$,
> - $\mathbb{R}$, $(0, 1)$, $[0, 1)$, $[0, 1]$, since
>   $$|[0, 1]| = |\mathbb{R}| = \left|\left(-\tfrac{\pi}{2}, \tfrac{\pi}{2}\right)\right| = |(0, 1)| = |\mathcal{P}\mathbb{N}|,$$
> - the set of uncomputable real numbers (*množica neizračunljivih realnih števil*).
>
> Ever larger infinities in the sequence (*vedno večje neskončnosti v zaporedju*):
> $$|\mathbb{N}|,\ |\mathcal{P}\mathbb{N}|,\ |\mathcal{P}\mathcal{P}\mathbb{N}|,\ |\mathcal{P}\mathcal{P}\mathcal{P}\mathbb{N}|,\ |\mathcal{P}\mathcal{P}\mathcal{P}\mathcal{P}\mathbb{N}|,\ \dots$$

## Questions

- [ ] Is $\trianglelefteq$ ("from some point on $f(x) \le g(x)$") a partial order — is it antisymmetric if $f$ and $g$ differ only for small $x$? Are $\preceq$ and $\trianglelefteq$ linear orders?
- [ ] For $(-1)^s \frac{p}{q} \mapsto 2^s 3^p 5^q$ to be injective, must $\frac{p}{q}$ be in lowest terms with $q \ge 1$?
- [ ] How do $x \mapsto \arctan x$ and the binary expansion of $x \in (0, 1)$ show that $|\mathbb{R}| = |\mathcal{P}\mathbb{N}|$, and what to do with numbers that have two expansions ($0.0111\ldots_{(2)} = 0.1000\ldots_{(2)}$)?
- [ ] Why does "computable real numbers are countable" together with "$\mathbb{R}$ is uncountable" mean that uncomputable real numbers exist?

## Connections

- Course: [[Discrete structures]]
- Exercises: [[Sources/discrete_structures/photoNotes/vaje/vaje 8.pdf|vaje 8]]
- Previous lecture: [[2026-11-16 - Graph of a Relation, Operations, Closures and Equivalence Relations - 7]] — properties of relations, inverse relation, product of relations, equivalence classes $[p \Rightarrow q]$
- [[Partial Order]], [[Linear Order]], [[Hasse Diagram]], [[Function]], [[Injective Function]], [[Surjective Function]], [[Bijective Function]], [[Composition of Functions]], [[Inclusion–Exclusion Principle]], [[Pigeonhole Principle]], [[Countable Set]], [[Cantor's Theorem]]
- [[Composition of Relations]], [[Inverse Relation]]: $g \circ f = f * g$ and $f^{-1}$ come from lecture 7
- [[Set]], [[Power Set]], [[Cartesian Product]]: $|\mathcal{P}A| = 2^{|A|}$, $|A \times B| = |A| \cdot |B|$ ([[2026-11-02 - Prenex Normal Form, Sets and Russell's Paradox - 5]], [[2026-11-09 - Set Equations, Cartesian Product and Relations - 6]])
- [[Tautology]], [[Logical Equivalence]]: the relation $\vdash$ and the hypothetical syllogism ([[2026-10-19 - Valid Arguments and Inference Rules - 3]])
- [[Russell's Paradox]]: the set $S$ of "bad" elements in Cantor's proof uses the same trick
- [[Prime Number]]: the levels of the divisibility Hasse diagram count prime factors

## Sources

- Handwritten notes: [[Sources/discrete_structures/photoNotes/lectures/lecture8/lecture 8.pdf|lecture 8]]
- Slides: [[Sources/discrete_structures/photoNotes/lectures/lecture8/dsuni-predavanje_malo_o_neskoncnih_mnozicah.pdf|Malo o neskončnih množicah]] (G. Fijavž, 23. 11. 2026): computable real numbers (p. 2), cardinality, Cantor–Schröder–Bernstein and trichotomy (pp. 3–4), countable sets (p. 5), uncountable sets and $|A| < |\mathcal{P}A|$ (p. 6)
- G. Fijavž, *Diskretne strukture* (FRI, 2015): 4.6.1 Partial and linear order (p. 96), 4.6.3 Hasse diagram (pp. 99–100), 5.1 Functions and their properties (pp. 103–106), 5.2 Inverse function and composition (pp. 106–108), 5.3 Properties of functions and composition (pp. 112–114), 6.1 Finite sets and the Dirichlet principle (pp. 119–121), 6.2 Cardinality of finite sets and operations, principle of inclusion and exclusion (pp. 122–125) — [[Sources/discrete_structures/ds.pdf#page=96|ds.pdf]]
