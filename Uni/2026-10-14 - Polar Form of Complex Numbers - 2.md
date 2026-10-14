---
type: "[[Lectures]]"
course: "[[Calculus]]"
date: 2026-10-14
week: "2"
---

# 2026-10-14 - Polar Form of Complex Numbers

## Main Idea

A [[Complex Number|complex number]] can be written in **Cartesian form** $x + iy$ (good for $+$, $-$) or in **polar form** $r e^{i\varphi}$ (good for $\cdot$, $/$, $\sqrt{\ }$). In polar form, multiplication means *multiply the absolute values and add the angles* ([[Euler's Formula|Euler's formula]], [[De Moivre's Formula|De Moivre's formula]]). This gives a geometric picture of operations in $\mathbb{C}$ (shift, reflection, stretch, rotation), a recipe for $n$-th roots (they form a regular $n$-gon), and the [[Fundamental Theorem of Algebra|fundamental theorem of algebra]].

## Notes

### OMA 2 — Cartesian and polar form

![[Calculus 2 polar form.svg]]

| | Cartesian form (*kartezični zapis*) | Polar form (*polarni zapis*) |
|---|---|---|
| form | $z = x + iy$ | $z = r(\cos\varphi + i\sin\varphi) = r \cdot e^{i\varphi}$ |
| coordinates | Cartesian coordinates $x, y$ | polar coordinates $r, \varphi$ |
| great for (*super za*) | $+$, $-$ | $\cdot$, $/$, $\sqrt{\ }$ |

**Conversion:**

- polar → Cartesian:
  $$x = r\cos\varphi \in \mathbb{R}, \qquad y = r\sin\varphi \in \mathbb{R}$$
- Cartesian → polar:
  $$r = |z| = \sqrt{x^2 + y^2} \in [0, \infty), \qquad \tan\varphi = \frac{y}{x}, \quad \varphi = \arctan\frac{y}{x} \in \mathbb{R}$$

$\varphi$ is called the **argument** of $z$.

> [!warning] $\varphi$ is not uniquely determined (*ni enolično določeno*)
> - It is determined only up to $\pm 2k\pi$, $k \in \mathbb{Z}$.
> - When computing $\varphi$, take the **quadrant** into account (*pri določanju upoštevamo kvadrant*).

#### Example 1: write in polar coordinates (*zapiši v pol. koord.*)

| | $z_1 = 1 + i$ | $z_2 = -1 - i$ |
|---|---|---|
| $r$ | $\sqrt{1^2 + 1^2} = \sqrt{2}$ | $\sqrt{1 + 1} = \sqrt{2}$ |
| $\tan\varphi$ | $\frac{1}{1} = 1$ | $\frac{-1}{-1} = 1$ |
| candidates | $\varphi \in \{\frac{\pi}{4} + k\pi;\ k \in \mathbb{Z}\}$ | same |
| quadrant | 1st | 3rd |
| $\varphi$ | $45^\circ = \frac{\pi}{4}$ | $\pi + \frac{\pi}{4} = \frac{5\pi}{4}$ |

#### Example 2: draw (*nariši*)

$$\{z \in \mathbb{C};\ |z| < 1,\ \operatorname{Re} z > 0\} \qquad \text{and} \qquad \{z \in \mathbb{C};\ \varphi \in [\tfrac{\pi}{2}, \pi],\ r \geq 1\}$$

![[Calculus 2 regions.svg]]

- Blue: $\{|z| < 1,\ \operatorname{Re} z > 0\}$ (dashed boundary)
- Orange: $\{\varphi \in [\frac{\pi}{2}, \pi],\ r \geq 1\}$

### Multiplication in polar form (*množenje v polarnem zapisu*)

Let $z_i = r_i(\cos\varphi_i + i\sin\varphi_i)$:

$$
\begin{aligned}
z_1 \cdot z_2 &= r_1(\cos\varphi_1 + i\sin\varphi_1) \cdot r_2(\cos\varphi_2 + i\sin\varphi_2) \\
&= r_1 r_2\big(\cos\varphi_1\cos\varphi_2 - \sin\varphi_1\sin\varphi_2 + i(\cos\varphi_1\sin\varphi_2 + \sin\varphi_1\cos\varphi_2)\big) \\
&= \underbrace{r_1 r_2}_{\text{product of abs. values}}\underbrace{\big(\cos(\varphi_1 + \varphi_2) + i\sin(\varphi_1 + \varphi_2)\big)}_{\text{sum of angles}}
\end{aligned}
$$

#### [[Euler's Formula]] (*Eulerjeva formula*)

$$e^{i\varphi} = \cos\varphi + i\sin\varphi$$

A shortcut (*bližnjica*) for the calculation above:

$$r_1 e^{i\varphi_1} \cdot r_2 e^{i\varphi_2} = r_1 r_2 \cdot e^{i(\varphi_1 + \varphi_2)}$$

Examples: $i = e^{i\frac{\pi}{2}}$, $\quad 1 + i = \sqrt{2} \cdot e^{i\frac{\pi}{4}}$

![[Calculus 2 unit circle.svg]]

$-1 = e^{i\pi} = e^{-i\pi}$ and $-i = e^{i\frac{3\pi}{2}} = e^{-i\frac{\pi}{2}}$.

#### Exercise (*naloga*): draw $\{r e^{ir};\ r \geq 0\}$

So (*torej*) it is a **spiral**. Marked points: $e^{i1}$, $2e^{i2}$, $3e^{i3}$ and $\pi e^{i\pi} = -\pi$.

![[Calculus 2 spiral.svg]]

### Playing in polar form (*igranje v polarnem zapisu*)

| Rule                                                 | Formula                                                                                                                                                                                                        | Condition    |
| ---------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| equality                                             | $r_1 e^{i\varphi_1} = r_2 e^{i\varphi_2} \implies r_1 = r_2 \neq 0$ and $\varphi_1 - \varphi_2 \in \{2k\pi;\ k \in \mathbb{Z}\}$ — or $r_1 = r_2 = 0$ (then the angles don't matter — *vseeno kakšni so koti*) |              |
| conjugate                                            | $\overline{r e^{i\varphi}} = r e^{-i\varphi}$ (reflection of $z$ to $\bar{z}$)                                                                                                                                 |              |
| power — [[De Moivre's Formula\|De Moivre's formula]] | $(r e^{i\varphi})^n = r^n e^{in\varphi}$                                                                                                                                                                       |              |
| inverse                                              | $(r e^{i\varphi})^{-1} = r^{-1} e^{-i\varphi}$                                                                                                                                                                 | $r \neq 0$   |
| quotient                                             | $\dfrac{r_1 e^{i\varphi_1}}{r_2 e^{i\varphi_2}} = \dfrac{r_1}{r_2} e^{i(\varphi_1 - \varphi_2)}$                                                                                                               | $r_2 \neq 0$ |

#### Example 1: $z = 1 - i\sqrt{3}$ — draw $z, z^2, z^3, z^{-1}, \dots$ (*narišite*)

$r = 2$, $\varphi = -\frac{\pi}{3}$ (4th quadrant: $x = 1$, $y = -\sqrt{3}$), so $z = 2e^{-i\frac{\pi}{3}}$.

| | value |
|---|---|
| $z$ | $2e^{-i\frac{\pi}{3}}$ |
| $z^2$ | $4e^{-i\frac{2\pi}{3}}$ |
| $z^3$ | $8e^{-i\frac{3\pi}{3}} = 8e^{-i\pi} = -8$ |
| $z^{-1}$ | $\frac{1}{2} \cdot e^{i\frac{\pi}{3}}$ |

![[Calculus 2 powers.svg]]

### Geometry of operations in $\mathbb{C}$ (*geometrija operacij v* $\mathbb{C}$)

A map (*preslikava*) $\mathbb{C} \to \mathbb{C}$ = a transformation of $\mathbb{C}$:

| Map | Transformation |
|---|---|
| $z \mapsto z + z_0$ | shift by $z_0$ (*premik*) |
| $z \mapsto \bar{z}$ | reflection across the real axis $\operatorname{Re}(z)$ (*zrcaljenje*) |
| $z \mapsto r \cdot z$; $r \in (0, \infty)$ | stretch by $r$ (*razteg*) |
| $z \mapsto z \cdot e^{i\alpha}$; $\alpha \in \mathbb{R}$ | rotation around $0$ by the angle $\alpha$ |
| $z \mapsto z \cdot r \cdot e^{i\varphi}$; $r \in (0, \infty)$, $\varphi \in \mathbb{R}$ | rotation by $\varphi$ and stretch by $r$ |
| ? (homework — *DN*) | reflection across the imaginary axis $\operatorname{Im}(z)$ |

#### Example: move the upper half of the unit disc

![[Calculus 2 transformation.svg]]

First rotate by $-\frac{\pi}{2}$, then shift by $2 + 2i$:

$$z \mapsto z \cdot e^{-i\frac{\pi}{2}} + 2 + 2i \quad ✓$$

> [!failure] Not like this
> $z \mapsto (z + 2 + 2i)\,e^{-i\frac{\pi}{2}}$ ✗

### Roots in $\mathbb{C}$ (*korenjenje v* $\mathbb{C}$)

#### Example: $z^5 = 32$

Write both sides in polar form:

$$z = r e^{i\varphi} \implies z^5 = r^5 e^{5i\varphi}$$

$$32 = 32 \cdot e^{i \cdot 0} = 2^5 \cdot e^{i \cdot 0} = 2^5 e^{i2\pi} = 2^5 e^{i4\pi} = \dots = 2^5 e^{-i2\pi}$$

$$r^5 e^{5i\varphi} = 2^5 \cdot e^{i \cdot 0}$$

- $\implies r = 2$
- $\implies 5\varphi \in \{0, 2\pi, 4\pi, \dots, -2\pi, \dots\}$ — infinitely many possible angles (*neskončno možnih kotov*):

| | $\varphi_1$ | $\varphi_2$ | $\varphi_3$ | … | $\varphi_{-1}$ |
|---|:-:|:-:|:-:|:-:|:-:|
| $5\varphi$ | $0$ | $2\pi$ | $4\pi$ | … | $-2\pi$ |
| $\varphi$ | $0$ | $\frac{2\pi}{5}$ | $\frac{4\pi}{5}$ | … | $-\frac{2\pi}{5}$ |

The angles repeat after 5 steps: $z_6 = z_1$, $z_{-1} = z_5$, … — the step is $\frac{2\pi}{5}$ (*skok je* $\frac{2\pi}{5}$).

![[Calculus 2 fifth roots.svg]]

- **5 solutions** — geometrically they form a **regular pentagon** (*pravilni 5-kotnik*).
- **The sum of the solutions is 0** (*vsota rešitev je 0*).

#### General rule

The solutions of $z^n = r e^{i\varphi}$, $r \neq 0$, are

$$z_k = \underbrace{\sqrt[n]{r}}_{\in \mathbb{R}}\; e^{i\frac{\varphi + 2k\pi}{n}}, \qquad k \in \{0, 1, \dots, n-1\}$$

**Proof** (*dokaz*): the same as in the example $z^5 = 32$.

The $n$ different solutions form a **regular $n$-gon** in $\mathbb{C}$ (*pravilni n-kotnik*). If we put the solutions one after another as vectors, we come back to the start, because the angles and the lengths are the same (*pridem nazaj, ker so koti in dolžine isti*) — so their sum is $0$:

![[Calculus 2 sum of roots.svg]]

#### Example: solve $(z^3 - 2)(z^2 - i) = 0$ (*reši*)

| | $z^3 = 2 = 2e^{i \cdot 0}$ | $z^2 = i = e^{i\frac{\pi}{2}}$ |
|---|---|---|
| solutions | $z_3 = \sqrt[3]{2}$ | $z_1 = 1 \cdot e^{i\frac{\pi}{4}}$ |
| | $z_4 = \sqrt[3]{2} \cdot e^{i\frac{2\pi}{3}}$ | $z_2 = 1 \cdot e^{i(\frac{\pi}{4} + \pi)} = -e^{i\frac{\pi}{4}}$ |
| | $z_5 = \sqrt[3]{2} \cdot e^{i\frac{4\pi}{3}}$ | |

### [[Fundamental Theorem of Algebra]] (*osnovni izrek algebre*)

Every equation $p(z) = 0$, where

$$p(z) = a_n z^n + a_{n-1} z^{n-1} + \dots + a_0, \qquad a_k \in \mathbb{C}\ \ \forall k \in \{0, \dots, n\}, \qquad a_n \neq 0,\ n \geq 1,$$

has (counted with multiplicity — *šteto z večkratnostjo*) **exactly $n$ zeros** in $\mathbb{C}$.

So:

$$p(z) = a_n (z - z_1) \cdot \ldots \cdot (z - z_n), \qquad z_k \in \mathbb{C}$$

**Additionally** (*dodatno*): if all coefficients are real ($a_k \in \mathbb{R}$, $\forall k$), then the complex zeros come in **conjugate pairs** (*konjugirani pari*):

$$z \notin \mathbb{R} \text{ is a zero} \implies \bar{z} \text{ is also a zero.}$$

So a real polynomial factors as

$$
p(z) = a_n \underbrace{(z - x_1) \cdots (z - x_p)}_{\text{real zeros}} \cdot \underbrace{Q_1 \cdot Q_2 \cdot \ldots \cdot Q_{\frac{n-p}{2}}}_{\text{quadratic factors irreducible over } \mathbb{R}}
$$

Each $Q_j$ is a quadratic factor that cannot be split over $\mathbb{R}$ (*kvadratni v $\mathbb{R}$ nerazcepni člen*) — zeros $\frac{-b \pm \sqrt{D}}{2a}$.

## Questions

- [ ] Homework (*DN*): which map $z \mapsto \ ?$ is the reflection across the imaginary axis $\operatorname{Im}(z)$?

## Connections

- Course: [[Calculus]]
- Previous lecture: [[2026-10-11 - Numbers - 1]] — Cartesian form, conjugate, absolute value
- [[Circular Motion]] — the same $r$, $\varphi$ description of a point on a circle (Physics)

## Sources

- Handwritten notes: [[Calculus 2 notes.pdf]]
- J. Globevnik, M. Brojan, *Analiza I* (2012), section 1.7.1 (`calculus/skripta.pdf`)
- [Fundamental theorem of algebra — Wikipedia](https://en.wikipedia.org/wiki/Fundamental_theorem_of_algebra)
