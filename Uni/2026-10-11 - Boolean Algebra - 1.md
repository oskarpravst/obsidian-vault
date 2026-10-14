---
type: "[[Lectures]]"
course: "[[Introduction to Digital Circuits]]"
date: 2026-10-11
week: "1"
---

# 2026-10-11 - Boolean Algebra

## Main Idea

[[Boolean Algebra]] (*Boolova algebra*) is defined by a set of elements, binary operators and a set of postulates from which all other rules can be proven. Its postulates come in pairs (original and [[Duality|dual]]). On top of it we build [[Switching Function|switching functions]] (*preklopne funkcije*) and switching circuits (*preklopna vezja*), which can be described equivalently by a formula, a [[Truth Table|truth table]] or a circuit schematic.

## Notes

### ODV 1 — Boolean algebra

Boolean algebra consists of:

- a set (*množica*)
- (operators)
- (postulates)

**Binary operator** (*binarni operator*) — acts between two numbers (elements): $a + b$, $a - b$, $a \cdot b$, $a / b$.

**Postulates** (*postulati*, axioms — *aksiomi*) — basic assumptions; everything else is proven from them.

#### General postulates (e.g. for numbers)

1. **Closure** (*zaprtost*) — take 2 elements from the set, combine them with a binary operator → the result is in the same set.
2. **Associativity** (*asociativnost*) — the order of evaluation does not matter:
   $$(a + b) + c = a + (b + c)$$
3. **Commutativity** (*komutativnost*) — the operands can be swapped:
   $$a + b = b + a$$
4. **Neutral element** (*nevtralni element*) — does not change the result. For all $\mathbb{N}$ numbers:
   - sum: $0$ $(a + 0 = a)$
   - product: $1$ $(a \cdot 1 = a)$
5. **Inverse element** (*inverzni element*) — for the sum: $a \to -a$
6. **Distributive law** (*zakon distributivnosti*):
   $$a(b + c) = ab + ac$$

#### Postulates of Boolean algebra (*aksiomi Boolove algebre*)

Conjunction $x \land y$ can also be written as $xy$.

1. **Closure** (*zaprtost*): $x, y \in X$
   - P1: $x \lor y$
   - P1\*: $x \land y$

   — the result must be in the set $X$.

2. **Neutral element** (*nevtralni element*):
   - P2: $x \lor 0 = x$
   - P2\*: $x \land 1 = x$ (written $x1 = x$)

3. **Commutativity** (*komutativnost*):
   - P3: $x \lor y = y \lor x$
   - P3\*: $xy = yx$

4. **Distributivity** (*distributivnost*):
   - P4: $x \lor (yz) = (x \lor y)(x \lor z)$
   - P4\*: $x(y \lor z) = xy \lor xz$

   P4 and P4\* are [[Duality|dual]] to each other (they complement each other).

5. **Inverse element** (*inverzni element*):
   - P5: $\forall x \in X,\ \exists \bar{x};\ x \lor \bar{x} = 1$
   - P5\*: $\forall x \in X,\ \exists \bar{x};\ x\bar{x} = 0$

   ($\forall$ — for every, *za vsak*; $\exists$ — there exists, *obstaja / eksistira*)

6. **Number of elements** — has no dual form: there exist at least two elements $x, y \in X$ such that $x \neq y$.

#### Operations

1. Negation (*negacija*): $\bar{a}$
2. Conjunction (*konjunkcija*): $ab$
3. Disjunction (*disjunkcija*): $a \lor b$

$\bar{b}$ negates one variable; $\overline{bc}$ negates the whole expression (conjunction is evaluated first).

### Rules (*pravila*)

1. **Idempotence** (*idempotenca*):
   - $x \lor x = x$
   - $xx = x$
2. **Absorption** (*absorpcija*):
   - $x \lor xy = x$
   - $x(x \lor y) = x$
3. **Associativity** (*asociativnost*):
   - $(x \lor y) \lor z = x \lor (y \lor z)$
   - $(xy)z = x(yz)$
4. **[[De Morgan's Laws|De Morgan's theorem]]** (*De Morganov izrek*):
   - $\overline{xy} = \bar{x} \lor \bar{y}$ (conjunction → disjunction)
   - $\overline{x \lor y} = \bar{x}\,\bar{y}$ (disjunction → conjunction)

### Proofs (*dokazi*)

**For proofs we use only the postulates, not the rules.**

#### 1. Idempotence: $a \lor a = a$

$$
\begin{aligned}
a \lor a &= (a \lor a)1 && \text{P2*} \\
&= (a \lor a)(a \lor \bar{a}) && \text{P5: } x \lor \bar{x} = 1 \\
&= a \lor a\bar{a} && \text{P4: } x \lor yz = (x \lor y)(x \lor z) \\
&= a \lor 0 && \text{P5*: } x\bar{x} = 0 \\
&= a \ \checkmark && \text{P2: } x \lor 0 = x
\end{aligned}
$$

#### 2. Absorption: $a \lor ab = a$

$$
\begin{aligned}
a \lor ab &= a1 \lor ab && \text{P2*} \\
&= a(1 \lor b) && \text{P4*} \\
&= a((1 \lor b)1) && \text{P2*} \\
&= a((1 \lor b)(b \lor \bar{b})) && \text{P5} \\
&= a((b \lor 1)(b \lor \bar{b})) && \text{P3} \\
&= a(b \lor 1\bar{b}) && \text{P4} \\
&= a(b \lor \bar{b}1) && \text{P3*} \\
&= a(b \lor \bar{b}) && \text{P2*} \\
&= a1 && \text{P5} \\
&= a \ \checkmark && \text{P2*}
\end{aligned}
$$

#### 3. Double negation: $\bar{\bar{a}} = a$

$$
\begin{aligned}
\bar{\bar{a}} &= \bar{\bar{a}} \lor 0 && \text{P2} \\
&= \bar{\bar{a}} \lor a\bar{a} && \text{P5*} \\
&= (\bar{\bar{a}} \lor a)(\bar{\bar{a}} \lor \bar{a}) && \text{P4} \\
&= (\bar{\bar{a}} \lor a)(\bar{a} \lor \bar{\bar{a}}) && \text{P3} \\
&= (\bar{\bar{a}} \lor a)1 && \text{P5 (applied to } \bar{a}\text{: } \bar{a} \lor \bar{\bar{a}} = 1) \\
&= (\bar{\bar{a}} \lor a)(a \lor \bar{a}) && \text{P5} \\
&= (a \lor \bar{\bar{a}})(a \lor \bar{a}) && \text{P3} \\
&= a \lor \bar{\bar{a}}\bar{a} && \text{P4} \\
&= a \lor \bar{a}\bar{\bar{a}} && \text{P3*} \\
&= a \lor 0 && \text{P5* (applied to } \bar{a}\text{: } \bar{a}\bar{\bar{a}} = 0) \\
&= a \ \checkmark && \text{P2}
\end{aligned}
$$

### Duality (*dualnost*)

A postulate consists of an original and a dual part.

$$f^d(a, b) = \overline{f(\bar{a}, \bar{b})}$$

We obtain it by swapping the logical values ($0 \leftrightarrow 1$) **and** swapping conjunctions and disjunctions.

| Original | Dual |
|---|---|
| $x \lor 0 = x$ | $x1 = x$ |
| $x \lor \bar{x} = 1$ | $x\bar{x} = 0$ |

Negation has no dual (it stays the same). … (applies to all rules)

$$\overline{\overline{f(\bar{\bar{a}}, \bar{\bar{b}})}} = f(a, b)$$

— the dual of the dual function is the original function again.

### Switching functions and switching circuits (*preklopne funkcije in preklopna vezja*)

A function of two variables as a block (p.f. = switching function):

```
a ──┐
    │ p.f. ├── f(a, b)
b ──┘
```

In general: inputs $x_1, x_2, \dots, x_n$ are $0$ or $1$; the output $f(x_1, x_2, \dots, x_n)$ is also $0$ or $1$ (this is where **closure** shows).

**Example:**

$$f(x_1, x_2, x_3) = x_1 x_2 \lor \bar{x}_3$$

#### Logic symbols (*logični simboli*)

1. **Conjunction** — AND gate: inputs $x_1, x_2$, output $x_1 x_2$
2. **Disjunction** — OR gate: inputs $x_1, x_2$, output $x_1 \lor x_2$
3. **Negation** — NOT gate (triangle with a circle): input $x$, output $\bar{x}$

The function from before as a circuit: $x_1, x_2$ → AND; $x_3$ → NOT; both outputs → OR → $f$.

#### Truth table (*pravilnostna tabela*)

Example for disjunction:

| $a$ | $b$ | $f(a, b)$ |
|:-:|:-:|:-:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

The inputs (*vhod*) are vectors; the output column (*izhod*) contains the function values for each row.

For $n$ variables there are $2^n$ combinations:

| $x_1\ x_2 \dots x_n$ | $f(x_1, x_2, \dots, x_n)$ |
|:-:|:-:|
| $0\ 0 \dots 0$ | $f(0, 0, \dots, 0)$ |
| $0\ 0 \dots 1$ | $f(0, 0, \dots, 1)$ |
| $\vdots$ | $\vdots$ |
| $1\ 1 \dots 1$ | $f(1, 1, \dots, 1)$ |

Input vectors: $\tilde{w}_i = (w_{1i}, w_{2i}, \dots, w_{ni})$. For $n = 3$ (written as $m = 3$ in the notes):

- $w_0 = (0, 0, 0)$
- $w_1 = (0, 0, 1)$
- $w_2 = (0, 1, 0)$
- $\vdots$
- $w_7 = (1, 1, 1)$

**Truth table for $n$ variables:**

| $x_1, x_2, \dots, x_n$ | $f$ |
|:-:|:-:|
| $\tilde{w}_0$ | $f(\tilde{w}_0)$ |
| $\tilde{w}_1$ | $f(\tilde{w}_1)$ |
| $\vdots$ | $\vdots$ |
| $\tilde{w}_{2^n-1}$ | $f(\tilde{w}_{2^n-1})$ |

#### Example: $f(x_1, x_2, x_3) = x_1 \bar{x}_2 x_3 \lor \bar{x}_1 x_2$

$$f(0, 0, 0) = 0\bar{0}0 \lor \bar{0}0 = 0$$
$$f(0, 0, 1) = 0\bar{0}1 \lor \bar{0}0 = 0$$
$$f(0, 1, 0) = 0\bar{1}0 \lor \bar{0}1 = 1$$

| $x_1$ | $x_2$ | $x_3$ | $f(x_1, x_2, x_3)$ |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 0 |

An equation can be transformed into a table → they are **equivalent representations** (*ekvivalentna zapisa*).

**Schematic** (*shema*): $x_1$, $\bar{x}_2$ (NOT on $x_2$), $x_3$ → AND; $\bar{x}_1$ (NOT on $x_1$), $x_2$ → AND; both → OR → $f(x_1, x_2, x_3)$.

#### Several functions in one table

A truth table can be written in parts. If the set of input variables is the same, several functions can be written into the same table:

| $x_1$ | $x_2$ | $x_3$ | $f_1$ | $f_2$ | $f_3$ |
|:-:|:-:|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 1 | 1 |
| 0 | 1 | 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 | 0 | 1 |
| 1 | 0 | 0 | 0 | 1 | 1 |
| 1 | 0 | 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 1 | 1 | 0 |
| 1 | 1 | 1 | 0 | 1 | 0 |

- $f_1(x_1, x_2, x_3) = x_1 x_2 \bar{x}_3$
- $f_2(x_1, x_2, x_3) = x_1 \lor \bar{x}_2 x_3$
- $f_3(x_1, x_2, x_3) = \bar{x}_1 \bar{x}_2 x_3 \lor \bar{x}_1 x_2 x_3 \lor x_1 \bar{x}_2$

## Questions

- [ ] test
- [ ] test2

## Connections

- Course: [[Introduction to Digital Circuits]]
- Related: [[2026-10-05 - Propositional Logic - 1]] (same laws in propositional logic)

## Sources

- Handwritten notes: [[Sources/introduction_to_digital_circuits/photoNotes/lectures/lecture 1.pdf|lecture 1]]
