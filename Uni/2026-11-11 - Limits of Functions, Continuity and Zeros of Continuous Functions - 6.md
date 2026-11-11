---
type: "[[Lectures]]"
course: "[[Calculus]]"
date: 2026-11-11
week: "6"
---

# 2026-11-11 - Limits of Functions, Continuity and Zeros of Continuous Functions

## Main Idea

From sequences to **functions** (*funkcije*):

1. Basics of functions (a pdf on the online classroom — *spletna učilnica*): division by $0$ is an error, a neural network is a big composition of functions, and the inverse of $x^2$ on $[0, \infty)$ is $\sqrt{x}$.
2. The **[[Limit of a Function|limit of a function]]** (*limita funkcije*) with $\varepsilon$ and $\delta$, left and right limits, limits at infinity and growing over every bound. A limit of a function can be computed with [[Sequence|sequences]], so the rules are the same as for the [[Limit of a Sequence|limit of a sequence]]. The important limit $\lim\limits_{x \to 0}\frac{\sin x}{x} = 1$.
3. **[[Continuity|Continuity]]** (*zveznost*): $f(a) = \lim\limits_{x \to a} f(x)$. Properties of continuous functions: elementary functions are continuous, sums, products and compositions are continuous, and a continuous function on $[a, b]$ is bounded, reaches its minimum and maximum and every value in between. Continuous extension.
4. **Zeros of continuous functions** (*ničle zveznih funkcij*): there is no formula for the roots of a polynomial of degree 5, so numerical methods approximate the zeros. [[Bisection Method|Bisection]], regula falsi and the secant method, and gradient descent in 1D.

## Notes

### OMA 6 — Basics of functions (*osnove funkcij*)

The basics of functions are in a pdf on the online classroom (*pdf na spletni učilnici*).

- If we divide by $0$, we get an error (*če delimo z 0 → error*).
- A neural network (*nevronska mreža*) is a big composition of functions (*veliko kompozitumov*).

![[Calculus 6 parabola.svg]]

$$f(x) = x^2, \qquad f: [0, \infty) \to [0, \infty), \qquad f^{-1}(x) = \sqrt{x} \quad \text{(the positive root — } \textit{pozitivni koren}\text{)}$$

### Limits of functions (*limite funkcij*)

Let $f$ be a function and $a, b \in \mathbb{R}$.

**Limit:** $\lim\limits_{x \to a} f(x) = b$ means: the closer $x$ is to $a$, the closer $f(x)$ is to $b$ (*bližje kot je x do a, bližje je b*). Precisely:

$$\lim_{x \to a} f(x) = b \iff \forall \varepsilon > 0\ \exists \delta > 0:\ x \in (a - \delta, a + \delta) \setminus \{a\} \implies f(x) \in (b - \varepsilon, b + \varepsilon)$$

- The smaller $\varepsilon$ is, the smaller $\delta$ must be, and the harder the condition is to satisfy (*manjši kot bo ε, manjši mora biti δ, težje je uresničiti pogoj*).
- $f(x) \in (b - \varepsilon, b + \varepsilon)$ is the same as $|f(x) - b| < \varepsilon$ (*isto*).

#### Left and right limit (*leva in desna limita*)

**Left limit** (*leva limita*), written $\lim\limits_{x \nearrow a} f(x)$ or $\lim\limits_{x \to a^-} f(x)$:

$$\lim_{x \nearrow a} f(x) = b \iff \forall \varepsilon > 0\ \exists \delta > 0:\ x \in (a - \delta, a) \implies f(x) \in (b - \varepsilon, b + \varepsilon)$$

**Right limit** (*desna limita*), written $\lim\limits_{x \searrow a} f(x)$ or $\lim\limits_{x \to a^+} f(x)$:

$$\lim_{x \searrow a} f(x) = b \iff \forall \varepsilon > 0\ \exists \delta > 0:\ x \in (a, a + \delta) \implies f(x) \in (b - \varepsilon, b + \varepsilon)$$

> [!theorem] Claim (*trditev*)
> $$\lim_{x \to a} f(x) = b \iff \lim_{x \nearrow a} f(x) = b = \lim_{x \searrow a} f(x)$$
> Both one-sided limits must exist as a **number** (*mora obstajati kot število*); infinity does not count (*neskončnost ne šteje*).

**Examples** (*primer*):

- $f(x) = \dfrac{x}{|x|}$, $f(0)$ is not defined:
  $$\lim_{x \nearrow 0} f(x) = -1, \qquad \lim_{x \searrow 0} f(x) = 1$$
  so $\lim\limits_{x \to 0} f(x)$ does not exist.
- $g(x) = \dfrac{1}{1 + e^{1/x}}$:
  $$\lim_{x \nearrow 0} g(x) = 1, \qquad \lim_{x \searrow 0} g(x) = 0$$
- $\lim\limits_{x \to 0} \dfrac{1}{x}$ does not exist (*ne obstaja*): from the left it goes to $-\infty$, from the right to $\infty$.

![[Calculus 6 one over x.svg]]

#### Limits at infinity (*limite v neskončnost*)

These limits converge (*konvergirajo*); only the part about $x$ changes (*samo ta del se spremeni*):

$$\lim_{x \to \infty} f(x) = b \iff \forall \varepsilon > 0\ \exists M \in \mathbb{R}:\ x > M \implies f(x) \in (b - \varepsilon, b + \varepsilon)$$

$$\lim_{x \to -\infty} f(x) = b \iff \forall \varepsilon > 0\ \exists m \in \mathbb{R}:\ x < m \implies f(x) \in (b - \varepsilon, b + \varepsilon)$$

#### Growing / falling over every bound (*naraščanje / padanje preko vsake meje*)

This is not convergence (*ni konvergenca*). Now the outer part is different (*zunanji del je drugačen*):

$$\lim_{x \to a} f(x) = \infty \iff \forall N \in \mathbb{R}\ \exists \delta > 0:\ x \in (a - \delta, a + \delta) \setminus \{a\} \implies f(x) > N$$

The same for the one-sided limits $\lim\limits_{x \nearrow a} f(x) = \infty$ and $\lim\limits_{x \searrow a} f(x) = \infty$, plus the variants for $-\infty$ (*+ variante za −∞*). At infinity:

$$\lim_{x \to \infty} f(x) = \infty \iff \forall N \in \mathbb{R}\ \exists M \in \mathbb{R}:\ x > M \implies f(x) > N$$

#### Limits of functions with sequences

> [!theorem] Claim (*trditev*)
> Let $a, b \in \mathbb{R} \cup \{\pm\infty\}$. Then
> $$\lim_{x \to a} f(x) = b \iff \lim_{n \to \infty} f(a_n) = b \quad \text{for every sequence } (a_n) \text{ with } \lim_{n \to \infty} a_n = a,\ a_n \neq a\ \forall n.$$

(The notebook writes $a, b \in \mathbb{R} \in \{\pm\infty\}$.)

So the rules for computing limits are the same as for sequences (*pravila za računanje limit so ista kot pri zaporedjih*).

**Example:** $\lim\limits_{x \to 2} \dfrac{\sin x}{x} = \dfrac{\sin 2}{2}$

$$\boxed{\lim_{x \to 0} \frac{\sin x}{x} = 1}$$

**Proof** (*dokaz*): no time (*ni časa*). The sketch compares the areas of a triangle, a circular sector and a larger triangle:

![[Calculus 6 sin x over x.svg]]

### Continuity (*zveznost*)

Intuitively, the graph is an unbroken curve (*graf je neprekinjena krivulja*).

**Definition:** a function $f$ is **continuous** (*zvezna*) at $a \in D_f$ if

$$f(a) = \lim_{x \to a} f(x)$$

**Examples** (*primeri*):

![[Calculus 6 continuity examples.svg]]

- $x^{-1}$ is not defined at $0$ (*ni def.*), but it is continuous on $D_f$ (*je zvezna na $D_f$*).
- A function with a jump is not continuous (*ni zvezna*).

**Example:** determine $a$ so that the function

$$f(x) = \begin{cases} 3, & x \le 2 \\ 2x + a, & x > 2 \end{cases}$$

is continuous.

![[Calculus 6 piecewise function.svg]]

$$\underbrace{\lim_{x \searrow 2} f(x)}_{4 + a} = f(2) = 3 = \underbrace{\lim_{x \nearrow 2} f(x)}_{3} \implies a = -1$$

#### Properties of continuity (*lastnosti zveznosti*)

1. All elementary functions are continuous (poles are not a problem — *poli niso problematični*).
2. If $f$ and $g$ are continuous at $a$:
   1. the graphs of $f$ and $g$ are unbroken curves at $a$,
   2. $f + g$, $f \cdot g$, $3f + 6g$, … are continuous at $a$,
   3. we can swap the order of the limit and the function (*lahko zamenjamo vrstni red limite in funkcije*):
      $$\lim_{x \nearrow 0} \frac{1}{1 + e^{1/x}} = \frac{1}{1 + \lim\limits_{x \nearrow 0} e^{1/x}} = \dots$$
3. If $f$ is continuous at $a$ and $g$ is continuous at $f(a)$, then $g \circ f$ is continuous at $a$.
4. If $f$ is continuous on $[a, b]$, then:
   1. $f$ is bounded and reaches its infimum and supremum: $\inf = \min$, $\sup = \max$ (there are no poles — *ni polov*),
   2. $\forall y \in [\min f, \max f]\ \exists x \in [a, b]:\ f(x) = y$.
5. If $\lim\limits_{x \to a} f(x) = b$ but $a \notin D_f$, we can **extend $f$ continuously** (*zvezno razširimo*) with $f(a) := b$.

**Example:** $f(x) = \dfrac{x}{x} \neq g(x) = 1$, because $0 \notin D_f$. After the extension

$$f(x) = \begin{cases} \dfrac{x}{x}, & x \neq 0 \\ 1, & x = 0 \end{cases}$$

the two functions are equal (*enaki funkciji*).

### Zeros of continuous functions (*ničle zveznih funkcij*)

$f: [a, b] \to \mathbb{R}$ is continuous. **Task** (*naloga*): find a zero of $f$ (*poiščimo ničlo f*).

**A short story** (*zgodbica*): there is a formula for the roots of a polynomial of degree 3, Cardano's formula (an algorithm; the notebook writes *Kordanove formule*), and for degree 4 as well. For a polynomial of degree 5 there is no such formula (Galois — *Galua*). Numerical methods approximate the zeros (*numerične metode ničle aproksimirajo*); we need limits and continuity to understand these methods.

"Idea of the method" (*ideja metode*): clever guessing (*zvito ugibanje*) — a good guess and approximately converging (*dobro ugibanje + približki konvergirajo*).

#### Bisection (*bisekcija*)

![[Calculus 6 bisection.svg]]

1. Let $f(a) \cdot f(b) < 0$ (one is $+$, the other $-$ — *ena +, ena −*).
2. Initial approximations of the zero (*začetna približka ničle*): $a_1 = a$, $b_1 = b$.
3. Compute the next approximations inductively (*induktivno računamo naslednje približke*):
   $$x_{n+1} = \frac{a_n + b_n}{2}$$
4. Three possibilities (*3 možnosti*):
   - $f(x_{n+1}) = 0$ — found it,
   - $f(x_{n+1}) \cdot f(a_n) < 0 \implies [a_{n+1}, b_{n+1}] = [a_n, x_{n+1}]$,
   - otherwise (*sicer*) $\implies [a_{n+1}, b_{n+1}] = [x_{n+1}, b_n]$.
5. The zero of $f$ is
   $$\lim_{n \to \infty} a_n = \lim_{n \to \infty} b_n = \lim_{n \to \infty} x_n$$
   We construct sequences that go towards the zero (*konstruiramo zaporedja, ki grejo proti ničli*).

#### Regula falsi (*regula falsi*)

The notebook heads it "secant method (regula falsi)" (*sekantna metoda (regula falsi)*), with the condition $f(a) \cdot f(b) < 0$. The only change is $x_{n+1}$; everything else is the same as in bisection (*$x_{n+1}$ bo edina sprememba, drugo je isto*). $x_{n+1}$ is where the line through $(a_n, f(a_n))$ and $(b_n, f(b_n))$ crosses the $x$-axis:

![[Calculus 6 regula falsi.svg]]

From the similar triangles:

$$\frac{f(a_n)}{x_{n+1} - a_n} = \frac{-f(b_n)}{b_n - x_{n+1}}$$

Computation (*izračun*):

$$x_{n+1} = \frac{a_n f(b_n) - b_n f(a_n)}{f(b_n) - f(a_n)}$$

Both bisection and regula falsi converge reliably (*obe zanesljivo konvergirata*).

#### Secant method (*sekantna metoda*)

Linear interpolation (*linearna interpolacija*): $x_{n+1}$ is computed the same way as in regula falsi, but without the condition $f(a_n) \cdot f(b_n) < 0$, so $x_{n+1}$ can lie outside $[a_n, b_n]$:

![[Calculus 6 secant method.svg]]

**Problem:** we do not know whether it converges. We hope it does, but it does not have to (*ne konvergira vedno*).

#### Gradient descent in 1D (*gradientni spust v 1D*)

(A "time capsule" — *time capsule*.) At $a_n$ we look at the slope $f'(a_n)$. With a positive slope we search to the left (*poz. naklon ⇒ iščemo levo*):

![[Calculus 6 gradient descent.svg]]

$$a_{n+1} = a_n - \operatorname{sign} f'(a_n) \cdot \mu, \qquad \mu > 0$$

This method is used for functions of several variables (*funkcije več spremenljivk*), where the previous methods do not necessarily work (*prejšnje metode ni nujno, da delujejo*).

## Questions

- [ ] How does the proof of $\lim\limits_{x \to 0}\frac{\sin x}{x} = 1$ with the triangle, the sector and the larger triangle go?
- [ ] What is $\lim\limits_{x \nearrow 0} \frac{1}{1 + e^{1/x}}$ when computed by swapping the limit and the function? (The notebook stops at "$= \dots$".)

## Connections

- Course: [[Calculus]]
- Previous lecture: [[2026-11-04 - Series and Convergence Tests - 5]] — series and convergence tests
- [[2026-10-28 - Limits of Sequences - 4]] — limit of a sequence, growing over every bound, rules for limits (the same rules hold for functions)
- [[2026-10-11 - Numbers - 1]] — supremum, infimum, maximum and minimum
- [[Binary Search]] — the same halving idea as bisection (Programming 1)
- [[Limit of a Sequence]], [[Sequence]], [[Supremum and Infimum]], [[Derivative]]

## Sources

- Handwritten notes: [[Sources/calculus/photoNotes/lectures/lecture 6.pdf|lecture 6]]
- J. Globevnik, M. Brojan, *Analiza I* (2012): 3.3 continuity, characterisation with sequences (Izrek 24) [[Sources/calculus/skripta.pdf#page=82|skripta p. 72]]; 3.5 properties of continuous functions, zero on $[a, b]$ (Izrek 29), boundedness and min/max (Izrek 30, Posledica 14) [[Sources/calculus/skripta.pdf#page=90|p. 80]]; 3.8 limit of a function [[Sources/calculus/skripta.pdf#page=97|p. 87]], left limit (Def. 56) [[Sources/calculus/skripta.pdf#page=100|p. 90]]
