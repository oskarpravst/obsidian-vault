---
type: "[[Lectures]]"
course: "[[Calculus]]"
date: 2026-11-18
week: "7"
---

# 2026-11-18 - Functions of Several Variables, Derivatives and L'Hôpital's Rule

## Main Idea

The lecture opens with an overview of the topic **functions** (*funkcije*): for functions of 1 variable (*1 spr.*) we have already done the definition and the limit (ticked off), the derivative $f'$ and the integral $\int f\,dx$ are still to come. Functions of $n$ variables (*n spr.*) are **new** (*novo*).

1. **[[Function of Several Variables|Functions of several variables]]** (*funkcije več spremenljivk*): a rule $f: D_f \to \mathbb{R}$ with $D_f \subseteq \mathbb{R}^n$. Domains, the graph $\Gamma_f \subseteq \mathbb{R}^{n+1}$ and [[Level Set|level curves]] (*nivojnice*), e.g. the paraboloid $x^2 + y^2$ and "Triglav".
2. The **[[Limit of a Function|limit of a function]]** of several variables: the same $\varepsilon$–$\delta$ definition as before, but with the distance $d(x, a)$ in $\mathbb{R}^n$. Limits at $(0, 0)$ are computed with [[Polar Coordinates|polar coordinates]]: the result must not depend on the angle $\varphi$.
3. The **[[Derivative|derivative]]** (*odvod*) as the limit of the difference quotient (*diferenčni kvocient*): the slope of the tangent. Differentiability, $|x|$, higher derivatives, the meaning of $f'$ and $f''$, left and right derivatives, rules for differentiation ([[Chain Rule|chain rule]], used in neural networks) and the basic derivatives, with the proofs for $x^n$ and $\ln x$.
4. **[[L'Hôpital's Rule]]** (*L'Hôspitalovo pravilo*) for limits of the form $\frac{0}{0}$ and $\frac{\infty}{\infty}$, applied to comparing the speed of algorithms ($n^2$ vs. $n \ln n$, [[Big O Notation]]) and to $e^n$ vs. $n^{307}$.

## Notes

### OMA 7 — Functions of several variables (*funkcije več spremenljivk*)

**Definition** (*def*): let $n \in \{1, 2, \dots\}$. A **function of $n$ variables** (*funkcija n spremenljivk*) is a rule (*predpis*)

$$f: D_f \to \mathbb{R}, \qquad (x_1, x_2, \dots, x_n) \longmapsto f(x_1, x_2, \dots, x_n)$$

where $D_f \subseteq \mathbb{R}^n$ is the domain (*definicijsko območje*). (The notebook writes $m \in \{1, 2, \dots\}$ and $D_f \in \mathbb{R}^n$.)

$$\mathbb{R}^n = \{(x_1, x_2, \dots, x_n);\ x \in \mathbb{R}\}$$

- $\mathbb{R}^2$ is the plane (*ravnina*),
- $\mathbb{R}^3$ is "3D space" (*"3D prostor"*).

**Examples** (*primeri*):

- $f_1(x, y) = \sin x + y \cos y$, with $D_{f_1} = \mathbb{R}^2$.
- $f_2(x, y, z) = x \cdot y^2 - 3y e^x$, with $D_{f_2} \supseteq \{(x, y, z) \in \mathbb{R}^3;\ y \ge 0\}$.
- $f_3(x, y) = \sqrt{1 - x^2 - y^2}$. The root needs $1 - x^2 - y^2 \ge 0$, i.e. $1 \ge x^2 + y^2$:
  $$D_{f_3} = \{(x, y);\ 1 \ge x^2 + y^2\}$$
  which is a disk (*krog*):

![[Calculus 7 unit disk.svg]]

- $f_4(x, y) = \ln(x \cdot y)$. $D_{f_4}$ is the open I and III quadrant (*I in III odprt kvadrant*), $(x \cdot y > 0)$.
  - **Trick** (*trik*): $\ln(x \cdot y) = \ln x + \ln y$, but the right-hand side has as its domain only the I quadrant (*$D_f$ le I kvadrant*). You have to be careful (*pazit je treba*).

### Graph of a function (*graf funkcije*)

$$\Gamma_f = \{(x_1, x_2, \dots, x_n, f(x_1, x_2, \dots, x_n));\ (x_1, \dots, x_n) \in D_f\} \subseteq \mathbb{R}^{n+1}$$

### Level curve of a function (*nivojnica funkcije*)

The **level curve** of $f$ at $c \in \mathbb{R}$:

$$\{(x_1, \dots, x_n) \in D_f:\ f(x_1, \dots, x_n) = c\} = \{f = c\}$$

where $f$ is the function and $c$ a constant value (*konstantna vrednost*).

**Examples** (*primeri*): $f(x, y) = x^2 + y^2$. Its graph is a bowl above the plane $\mathbb{R}^2$; the level curves $\{f = 1\}$, $\{f = 2\}$, $\{f = 3\}$ are circles around the origin:

![[Calculus 7 paraboloid level curves.svg]]

**Triglav** (*triglav*): three peaks, and on the plane below them the level curves around each peak, which merge further down (like the contour lines on a hiking map):

![[Calculus 7 Triglav level curves.svg]]

For several variables it is very hard to visualise (*za več spremenljivk zelo težko vizualiziramo*).

### Limit of a function (*limita funkcije*)

Let $f: D_f \to \mathbb{R}$, $D_f \subseteq \mathbb{R}^n$, $L \in \mathbb{R}$. $L$ is the **limit of $f$ at $a \in \mathbb{R}^n$** $\left[L = \lim\limits_{x \to a} f(x)\right]$ if

$$\forall \varepsilon > 0\ \exists \delta > 0:\ d(x, a) < \delta \implies d(f(x), L) < \varepsilon$$

- $d(x, a)$ is a distance (*razdalja*) between points of $\mathbb{R}^n$.
- $d(f(x), L) = |f(x) - L|$, the usual distance in $\mathbb{R}$.
- In several dimensions the distance is the **norm** (*v več dimenzijah je razdalja norma*).

**Example:**

$$\lim_{(x, y) \to (0, 0)} \frac{x}{y} \quad \text{does not exist (} \textit{ne obstaja} \text{)}$$

Approaching $(0, 0)$ from different directions gives different values (the notebook marks $1$ on the diagonal and $0$ on the $x$-axis):

![[Calculus 7 approaching origin.svg]]

#### Procedure for limits at $(0, 0)$ (*postopek za limite v (0, 0)*)

1. Use [[Polar Coordinates|polar coordinates]] (*uporabimo polarne koordinate*): $x = r\cos\varphi$, $y = r\sin\varphi$.
2. Send $r \to 0$ (*pošljemo $r \to 0$*).
3. The result must be independent of the argument $\varphi$ (*rezultat mora biti neodvisen od argumenta $\varphi$*).

For $\frac{x}{y}$:

$$\lim_{r \to 0} \frac{r \cos\varphi}{r \sin\varphi} = \lim_{r \to 0} \frac{\cos\varphi}{\sin\varphi} = \cot\varphi$$

There is no limit, because it depends on $\varphi$ (*ni limite, ker je odvisen od $\varphi$*).

**Example:**

$$\lim_{(x, y) \to (0, 0)} \frac{2x^2 y}{x^2 + y^2} = \lim_{r \to 0} \frac{2r^3 \cos^2\varphi \sin\varphi}{r^2} = \lim_{r \to 0} 2r \cos^2\varphi \sin\varphi = 0$$

independent of $\varphi$ (*neodvisna od $\varphi$*), so the limit is $0$.

**Homework** (*D.N.*):

$$\lim_{(x, y) \to 0} \frac{x \cdot y + 3y^2 x + x^2 y^2}{x^2 + y^2}$$

### Derivative (*odvod*)

![[Calculus 7 secant and tangent.svg]]

The slope of the secant (*naklon sekante*) through $x_0$ and $x_0 + h$ is the **difference quotient** (*diferenčni kvocient*):

$$\frac{f(x_0 + h) - f(x_0)}{h}$$

**Definition** (*def*): the **derivative** (*odvod*) of $f$ at $x_0 \in \mathbb{R}$ is

$$f'(x_0) = \lim_{h \to 0} \frac{f(x_0 + h) - f(x_0)}{h}$$

the slope of the tangent at $x_0$ (*naklon tangente v $x_0$*). The derivative is the function

$$f': D_{f'} \to \mathbb{R}, \qquad x \longmapsto f'(x)$$

- $f$ is **differentiable** (*odvedljiva*) at $x$ if $f'(x)$ exists (if that limit exists — *če obstaja tista limita*).
- $f$ is differentiable if it is differentiable $\forall x \in D_f$.

**Example** (*primer*): $f(x) = |x|$, $D_f = \mathbb{R}$.

![[Calculus 7 absolute value.svg]]

$f$ is differentiable on $\mathbb{R} \setminus \{0\} = D_{f'}$:

$$f'(x) = \begin{cases} 1, & x > 0 \\ -1, & x < 0 \end{cases}$$

#### Higher derivatives (*višji odvodi*)

The **second derivative** (*drugi odvod*) $f''$ and the **$n$-th derivative** (*$n$-ti odvod*) $f^{(n)}$:

$$f''(x_0) = (f')'(x_0), \qquad f^{(n)}(x_0) = \left(f^{(n-1)}\right)'(x_0) \quad \text{(inductive definition — } \textit{induktivna definicija}\text{)}$$

$f$ is **$n$ times differentiable** (*$n$-krat odvedljiva*) (at $x_0$) if the $n$ derivatives exist (at $x_0$).

#### Meaning (*pomen*)

$f'(x_0)$ represents (*predstavlja*):

- the slope of the tangent (*naklon tangente*),
- the rate of change of $f$ (*hitrost spreminjanja f*).

$f''(x_0)$ represents:

- the "curvature" (*"ukrivljenost"*),
- the acceleration of the change of $f$ (*pospešek spreminjanja f*).

> [!theorem] Claim (*trditev*)
> If $f$ is differentiable at $x_0$, it is also continuous there (*je tam tudi zvezna*).

The second derivative is important (*drugi odvod pomemben*).

#### Left and right derivative (*levi in desni odvod*)

**Left derivative** (*levi odvod*) of $f$ at $x_0$:

$$\lim_{h \nearrow 0} \frac{f(x_0 + h) - f(x_0)}{h}$$

**Right derivative** (*desni odvod*) of $f$ at $x_0$:

$$\lim_{h \searrow 0} \frac{f(x_0 + h) - f(x_0)}{h}$$

(The notebook first wrote $h \nearrow x_0$ and $h \searrow x_0$ and corrected it to $0$.)

#### Rules for differentiation (*pravila za odvajanje*)

Let $f, g$ be functions and $\alpha \in \mathbb{R}$.

| Rule | Formula |
|---|---|
| linearity (*linearnost*) | $(\alpha \cdot f + g)' = \alpha f' + g'$ |
| product rule (*produktno pravilo*) | $(f \cdot g)' = f'g + fg'$ |
| chain rule (*verižno pravilo*) | $(f \circ g)'(x) = f'(g(x)) \cdot g'(x)$ |
| quotient rule (*kvocientno pravilo*) | $\left(\dfrac{f}{g}\right)' = \dfrac{f'g - fg'}{g^2}$ |

The chain rule is used in neural networks (*uporablja v nevronskih mrežah*). In short: $(f \circ g)' = (f' \circ g) \cdot g'$. The derivative of $f$ is evaluated at $g(x)$, not at $x$, so it is not simply $f' \cdot g'$.

#### Basic derivatives (*osnovni odvodi*)

| $f(x)$ | $f'(x)$ |
|---|---|
| $\text{const}$ | $0$ |
| $x^n$ | $n x^{n-1}$, $n \neq 0$ |
| $\log_a x$ | $\dfrac{1}{x \cdot \ln a}$ |
| $\sin x$ | $\cos x$ |
| $\cos x$ | $-\sin x$ |
| $a^x$ | $a^x \cdot \ln a$ |
| $\arctan x$ | $\dfrac{1}{1 + x^2}$ |
| $\arcsin x$ | $\dfrac{1}{\sqrt{1 - x^2}}$ |

Next to $\log_a x$ the notebook has the side note "$a > 1$, power of an exception".

**Proof for $x^n$**, $n \ge 1$, with the binomial expansion (*binomska formula*):

$$\lim_{h \to 0} \frac{(x + h)^n - x^n}{h} = \lim_{h \to 0} \frac{x^n + n x^{n-1} h + \dots + h^n - x^n}{h}$$

$$= \lim_{h \to 0} \left(n x^{n-1} + h \cdots + h^2 \cdots + \dots + h^{n-1}\right) = n \cdot x^{n-1}$$

because every term with $h$ goes to $0$.

**Proof for $\ln x$:**

$$\ln'(x) = \lim_{h \to 0} \frac{\ln(x + h) - \ln x}{h} = \lim_{h \to 0} \frac{1}{h} \cdot \ln\left(\frac{x + h}{x}\right) = \lim_{h \to 0} \ln\left(\left(1 + \frac{h}{x}\right)^{\frac{1}{h}}\right)$$

$$= \lim_{h \to 0} \ln\left(\left(1 + \frac{1}{\frac{x}{h}}\right)^{\frac{x}{h} \cdot \frac{1}{x}}\right) = \lim_{h \to 0} \frac{1}{x} \cdot \ln\underbrace{\left(1 + \frac{1}{\frac{x}{h}}\right)^{\frac{x}{h}}}_{\to\, e} = \frac{1}{x}$$

because $\frac{x}{h} \to \infty$ as $h \searrow 0$, the bracket goes to $e$, and $\ln e = 1$.

### L'Hôpital's rule (*L'Hôspitalovo pravilo*)

For limits of the form $\lim\limits_{x \to a} \frac{f(x)}{g(x)}$ where both $f$ and $g$ go to $0$:

![[Calculus 7 L'Hopital.svg]]

We approximate them with tangents, so the quotient is the same as the quotient of the derivatives (*to aproksimiramo s tangento, kvocient je isti kvocientom odvodov*).

> [!theorem] L'Hôpital's rule
> Let $f, g$ be differentiable on $(a, b) \subseteq \mathbb{R}$, $g \neq 0$ and $g' \neq 0$. For $c \in (a, b)$ let one of the conditions (*eden izmed pogojev*) hold:
> - $\lim\limits_{x \to c} f(x) = \lim\limits_{x \to c} g(x) = 0$, or
> - $\lim\limits_{x \to c} f(x) = \lim\limits_{x \to c} g(x) = \pm\infty$.
>
> Then (*tedaj*), if the limit on the right exists:
> $$\lim_{x \to c} \frac{f(x)}{g(x)} = \lim_{x \to c} \frac{f'(x)}{g'(x)}$$
> This also holds for $b = c = \pm\infty$ (*velja tudi*).

(The notebook writes $(a, b) \in \mathbb{R}$.)

#### Example: speed of algorithms (*hitrost algoritmov*)

If we process $n$ numbers in order, each one separately (linear search), the time grows like $n$. **Sorting $n$ numbers by size** (*urejanje $n$ števil po velikosti*):

- brute force (*surova sila*) $\sim n^2$ (more precisely $\frac{(n-1)(n-2)}{2}$, as written in the notebook),
- quick sort $\sim n \ln(n)$.

Which is faster? Compare with L'Hôpital ([[Big O Notation]]):

$$\lim_{n \to \infty} \frac{n^2}{n \cdot \ln(n)} \overset{\text{L'H}}{\underset{\frac{\infty}{\infty}}{=}} \lim_{n \to \infty} \frac{2n}{\ln(n) + n \cdot \frac{1}{n}} = \lim_{n \to \infty} \frac{2n}{\ln(n) + 1} \overset{\text{L'H}}{\underset{\frac{\infty}{\infty}}{=}} \lim_{n \to \infty} \frac{2}{\frac{1}{n}} = \lim_{n \to \infty} 2n = \infty$$

So $n^2$ grows faster than $n \ln n$: quick sort is faster.

Expressions such as $\ln \ln n$ or $n^3 k^2 \ln(n \cdot k)$ are also compared with L'Hôpital (*poračuna se z L'H*).

#### Mental note (*mentalni zapisek*)

$$\ln n < n < n \ln n < n^2$$

for large $n$. The last inequality $n \ln n < n^2$ we proved (*dokazali*); the rest is for home (*doma*).

$$n^m < e^n$$

$$\lim_{n \to \infty} \frac{e^n}{n^{307}} \overset{\text{L'H}}{\underset{\frac{\infty}{\infty}}{=}} \lim_{n \to \infty} \frac{e^n}{307 \cdot n^{306}} \overset{(\text{L'H})^{306}}{\underset{\frac{\infty}{\infty}}{=}} \lim_{n \to \infty} \frac{e^n}{307!} = \infty$$

## Questions

- [ ] Homework: what is $\lim\limits_{(x, y) \to (0, 0)} \frac{xy + 3y^2 x + x^2 y^2}{x^2 + y^2}$?
- [ ] Homework: prove $\ln n < n < n \ln n$ for large $n$ with L'Hôpital's rule.
- [ ] Is "the result is independent of $\varphi$" enough for the limit at $(0, 0)$ to exist, or does the bound also have to be independent of $\varphi$?
- [ ] What does the side note "$a > 1$, power of an exception" next to $(\log_a x)'$ mean?

## Connections

- Course: [[Calculus]]
- Exercises: [[Sources/calculus/photoNotes/vaje/vaje 7.pdf|vaje 7]]
- Previous lecture: [[2026-11-11 - Limits of Functions, Continuity and Zeros of Continuous Functions - 6]] — limit of a function of one variable with $\varepsilon$ and $\delta$, left and right limits, continuity; gradient descent already used $f'$
- [[2026-10-14 - Polar Form of Complex Numbers - 2]] — polar form $r$, $\varphi$, the same idea as the polar coordinates for limits at $(0, 0)$
- [[2026-10-28 - Limits of Sequences - 4]] — the number $e$ as $\lim (1 + \frac{1}{n})^n$, used in the proof of $(\ln x)' = \frac{1}{x}$
- [[Derivative]] — derivatives and the product and chain rules in Physics
- [[Continuity]], [[Function]], [[Neural Network]], [[Sorting Algorithm]]

## Sources

- Handwritten notes: [[Sources/calculus/photoNotes/lectures/lecture 7.pdf|lecture 7]]
- J. Globevnik, M. Brojan, *Analiza I* (2012): ch. 4 derivative, definition [[Sources/calculus/skripta.pdf#page=105|p. 95]], differentiable ⇒ continuous (Trditev 22) and left/right derivative (Trditev 23) [[Sources/calculus/skripta.pdf#page=106|pp. 96–97]], rules and chain rule (Izrek 36) [[Sources/calculus/skripta.pdf#page=110|pp. 100–101]], table of derivatives (Tabela 4.1) [[Sources/calculus/skripta.pdf#page=118|p. 108]]; 4.8 L'Hospital's rules (Izrek 43, 44) [[Sources/calculus/skripta.pdf#page=139|pp. 129–132]]
- *Analiza II* (skriptaII): ch. 1 functions of several variables, $f: D \subset \mathbb{R}^n \to \mathbb{R}$ and continuity [[Sources/calculus/skriptaII.pdf#page=11|p. 5]]
