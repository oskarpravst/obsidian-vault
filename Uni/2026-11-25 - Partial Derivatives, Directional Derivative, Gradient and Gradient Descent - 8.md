---
type: "[[Lectures]]"
course: "[[Calculus]]"
date: 2026-11-25
week: "8"
---

# 2026-11-25 - Partial Derivatives, Directional Derivative, Gradient and Gradient Descent

## Main Idea

The lecture opens with the overview from last time: for functions of 1 variable (*fun 1 spr*) we have the definition and the derivative (*def, odv*), and now the derivative is carried over to **functions of $n$ variables** (*fun n spr*). About the colloquium: it covers everything up to what we do this week in the exercises (*na kolokviju vse do kar delamo ta teden na vajah*).

1. **[[Partial Derivative|Partial derivatives]]** (*parcialni odvodi*): differentiate with respect to one variable and treat the others as constants. Four meanings of $f_x(a, b)$: the derivative of $t \mapsto f(a + t, b)$, the slope of a section of the graph, the slope in the $x$ direction and the best linear approximation.
2. The **[[Directional Derivative|directional derivative]]** (*smerni odvod*) $f_v$: we walk from $(a, b)$ in the direction of a vector $v$ and watch how the function changes. Example: does $x^2 + 2xy - y^2$ increase at $(2, -1)$ in the direction $(1, -1)$?
3. **[[Differentiability]]** (*diferenciabilnost*): $f$ is approximated by the tangent plane up to a sublinear remainder. Continuous partial derivatives are enough.
4. The **tangent vector to a curve** (*tangentni vektor na krivuljo*): a parametrized curve, velocity vector and speed.
5. The **[[Chain Rule|chain rule]]** (*verižno pravilo*) for $f(x(t), y(t))$, written with the **[[Gradient|gradient]]** $\nabla f$: $f_v = \nabla f \cdot v$. The gradient points in the direction of the steepest increase and is perpendicular to the [[Level Set|level curves]] (*nivojnice*).
6. **[[Gradient Descent|Gradient descent]]** (*gradientni spust*) $x_{k+1} = x_k - \gamma \nabla f$, demonstrated with one step of [[Linear Regression|linear regression]] (*linearna regresija*). This is how [[Neural Network|neural networks]] learn.

## Notes

### OMA 8 — Derivatives of functions of several variables (*odvodi funkcij več spremenljivk*)

$$\text{fun 1 spr: def, odv} \;\longrightarrow\; \text{fun } n \text{ spr: def, odv}$$

On the colloquium: everything up to what we do this week in the exercises (*na kolokviju vse do kar delamo ta teden na vajah*).

### 1. Partial derivatives (*parcialni odvodi*)

$$f: D \to \mathbb{R}, \quad D \subset \mathbb{R}^2, \quad (x, y) \longmapsto f(x, y)$$

$$g: D_g \to \mathbb{R}, \quad D_g \subset \mathbb{R}^n, \quad (x_1, x_2, \dots, x_n) \longmapsto g(x_1, \dots, x_n)$$

The **partial derivative** (*parcialni odvod*) of $f$ with respect to $x$ at $(a, b)$:

$$\frac{\partial f}{\partial x}(a, b) = f_x(a, b) = \lim_{h \to 0} \frac{f(a + h, b) - f(a, b)}{h}$$

The notebook writes $f(a + h\,b) - f(ab)$. The sign $\partial$ is not a delta (the notebook first labels it "delta"); in LaTeX: `\delta` is $\delta$, `\partial` is $\partial$.

With respect to $y$:

$$\frac{\partial f}{\partial y}(a, b) = f_y(a, b) = \lim_{h \to 0} \frac{f(a, b + h) - f(a, b)}{h}$$

(The notebook writes $f(b + ah) - f(b \cdot a)$; corrected after *Analiza II*, 1.5.)

For a function of $n$ variables, with $A = (a_1, \dots, a_n)$, only the $i$-th variable moves:

$$\frac{\partial g}{\partial x_i}(a_1, \dots, a_n) = \lim_{h \to 0} \frac{g(a_1, \dots, a_i + h, \dots, a_n) - g(a_1, \dots, a_n)}{h}$$

(The notebook leaves the numerator unfinished — "fill in (I can't see the board)" (*dopolni (ne vidim na tablo)*); completed after *Analiza II*, 1.5.)

**Example** (*primer*): compute the partial derivatives of $f(x, y) = x y^2 + x e^y$ at $(1, 0)$ (*izračunaj parcialna odvoda*).

$$f_x = y^2 + e^y, \qquad f_y = 2xy + x e^y$$

(A faint "$+y$" after the function, with "$+0$" in $f_x$ and "$+1$" in $f_y$, is written lighter in the notebook.)

When differentiating with respect to one variable, the other one behaves like a number:

$$2xy^3 \;\xleftarrow{\ \partial/\partial x\ }\; x^2 y^3 \;\xrightarrow{\ \partial/\partial y\ }\; x^2 \cdot 3y^2$$

just like $x^2 \cdot 5^3 \to 2x \cdot 5^3$ and $7^2 \cdot y^3 \to 7^2 \cdot 3y^2$.

$$f_x(1, 0) = y^2 + e^y \Big|_{\substack{x = 1 \\ y = 0}} = 0^2 + e^0 = 1, \qquad f_y(1, 0) = 1$$

**Neural networks** (*nevronske mreže*): in a function like $f(x, y) = a x^3 y^2 + e^x y^3$, neural networks learn by changing the coefficients ($a$) (*se učijo, da koeficiente spreminjamo*). (The exponent of $x$ is overwritten in the notebook.)

#### Meaning of $f_x(a, b)$ (*pomen*)

1. the derivative of $t \longmapsto f(a + t, b)$ at $t = 0$ (*odvod … pri $t = 0$*),
2. the slope coefficient of the section of the graph of $f$ with the plane $\{y = b\}$ (*naklonski koeficient prereza grafa f z ravnino $\{y = b\}$*),
3. the slope of the graph in the $x$ direction (*naklon grafa v smeri x*),
4. the slope coefficient of the best approximation with a line (*naklonski koeficient najboljše aproksimacije s premico*):
   $$f(a + t, b) \doteq f(a, b) + t \cdot f_x(a, b)$$

### 2. Directional derivative (*smerni odvod*)

For $v \in \mathbb{R}^2$ (in general $w \in \mathbb{R}^n$):

$$f_v(a, b) = \frac{\partial}{\partial t} f\big((a, b) + t \cdot v\big)\Big|_{t = 0}$$

where $t$ says how far we go (*kako daleč grem*). $v$ is a vector (*v je vektor*):

![[Calculus 8 directional derivative.svg]]

We walk in one direction and watch how the function changes (*sprehajamo se v eni smeri in gledamo, kako se funkcija spreminja*). For $n$ variables:

$$g_w(A) = \frac{\partial}{\partial t}\, g(A + t \cdot w)\Big|_{t = 0}$$

#### Meaning of $f_v(a, b)$ (*pomen*)

1. the same as before (*enaka kot prej*): the derivative of $t \mapsto f((a, b) + t v)$ at $t = 0$;
2. if $\|v\| = 1$, then $f_v(a, b)$ is the slope of the graph in the direction $v$ (*naklon grafa v smeri v*). In general (*v splošnem*):
   $$f_v(a, b) = f_{\frac{v}{\|v\|}}(a, b) \cdot \|v\|$$
3. the partial derivatives are directional derivatives in the directions of the axes:
   $$f_x = f_{(1, 0)}, \qquad f_y = f_{(0, 1)}$$

**Example** (*primer*): does the function $f(x, y) = x^2 + 2xy - y^2$ increase at the point $(2, -1)$ in the direction $(1, -1)$ (*ali v točki … v smeri … narašča*)?

$$f\big((2, -1) + t(1, -1)\big) = f(2 + t, -1 - t) = (2 + t)^2 + 2(2 + t)(-1 - t) - (-1 - t)^2$$

![[Calculus 8 direction example.svg]]

Differentiate with respect to $t$ term by term:

$$\frac{\partial}{\partial t}: \quad 2(2 + t) + 2\big(-1 - t - (2 + t)\big) - 2(t + 1)$$

$$\overset{t = 0}{\longrightarrow} \quad 4 + 2(-1 - 2) - 2 \cdot 1 = 4 - 6 - 2 = -4 = f_{(1, -1)}(2, -1)$$

with the direction $(1, -1)$ in the subscript and the point $(2, -1)$ in the brackets. The function decreases (the derivative is negative) (*funkcija pada (odvod je negativen)*). Since $\|(1, -1)\| = \sqrt{2}$:

$$\text{slope (}\textit{naklon}\text{)} = \frac{-4}{\|(1, -1)\|} = -\frac{4}{\sqrt{2}}$$

### 3. Differentiability (*diferenciabilnost*)

$f$ is **differentiable** (*diferenciabilna*) at $(a, b) \in D$ if

$$f(a + h_1, b + h_2) = \underbrace{f(a, b) + h_1 \cdot f_x(a, b) + h_2 \cdot f_y(a, b)}_{\text{tangent plane}} + \underbrace{o(h_1, h_2)}_{\text{remainder}}$$

where

$$\lim_{(h_1, h_2) \to 0} \frac{o(h_1, h_2)}{\|(h_1, h_2)\|} = 0$$

- The first part is the tangent plane (*tangentna ravnina*), parametrized with $h_1$ and $h_2$.
- $o(h_1, h_2)$ is the remainder (*ostanek*), a sublinear remainder (*sublinearen ostanek*).

This means: at $(a, b)$ the tangent plane exists and is determined by $f_x(a, b)$ and $f_y(a, b)$ (*v $(a, b)$ obstaja tangentna ravnina in je določena z …*).

> [!theorem] Theorem (*izrek*)
> If the partial derivatives $f_x$ and $f_y$ are continuous at $(a, b)$, then $f$ is differentiable.

### 4. Tangent vector to a curve (*tangentni vektor na krivuljo*)

$\gamma: [0, 1] \to \mathbb{R}^2$ continuous and differentiable (*zvezna, odvedljiva*) is a **parametrized curve** (*parametrizirana krivulja*):

$$t \longmapsto \big(x(t), y(t)\big)$$

![[Calculus 8 parametrized curve.svg]]

The same curve can have different parametrizations (speed) (*ista krivulja ima lahko različne parametrizacije (hitrost)*). The **velocity vector** (*vektor hitrosti*, velocity), with $x$ and $y$ both continuous and differentiable (*obe zvezni in odvedljivi*):

$$\gamma'(t) = \big(x'(t), y'(t)\big)$$

Its direction depends on the curve, but its size also depends on the parametrization (*smer odvisna od krivulje, velikost pa tudi od parametrizacije*).

$$\text{speed (}\textit{hitrost}\text{)} = \|\gamma'(t)\|$$

### 5. Chain rule (*verižno pravilo*)

Let $f$ be differentiable and $x(t)$, $y(t)$ differentiable (*odvedljivi*), and $h(t) = f\big(x(t), y(t)\big)$. Then

$$h'(t) = f_x\big(x(t), y(t)\big) \cdot x'(t) + f_y\big(x(t), y(t)\big) \cdot y'(t)$$

In short:

$$h' = f_x \cdot x' + f_y \cdot y' \qquad \text{or} \qquad dh = f_x\, dx + f_y\, dy \;\;\text{(physicists — } \textit{fiziki}\text{)}$$

As a dot product:

$$h' = \underbrace{(f_x, f_y)}_{\text{gradient } \nabla f \,=\, \operatorname{grad} f} \cdot \underbrace{(x', y')}_{\text{tangent vector}}$$

> [!note] Side note
> $\Delta f = f_{xx} + f_{yy}$ is the Laplacian (*Laplace*). $\nabla f$ and $\Delta f$ are not the same (*ni isto*).

For $n$ variables, $g = g(x_1, x_2, \dots, x_n)$:

$$\nabla g = (g_{x_1}, g_{x_2}, \dots, g_{x_n}), \qquad \frac{d}{dt}\, g\big(x_1(t), \dots, x_n(t)\big) = \nabla g \cdot (x_1', \dots, x_n')$$

$\nabla g(A) \in \mathbb{R}^n$: the gradient is a vector (*gradient je vektor*).

**The example from before** (*od primera prej*), $f(2 + t, -1 - t)$:

$$\nabla f = (2x + 2y,\ 2x - 2y), \qquad \nabla f(2, -1) = (2, 6)$$

$$\frac{\partial}{\partial t} f(2 + t, -1 - t) = \nabla f \cdot (1, -1) = (2, 6) \cdot (1, -1) = -4$$

the same directional derivative as before (*isti smerni odvod kot prej*). So the **directional derivative** is

$$f_v = \nabla f \cdot v$$

#### Direction of the steepest increase

$$|f_v| = |\nabla f \cdot v| = \|\nabla f\| \cdot \|v\| \cdot \cos\varphi = \|\nabla f\| \cos\varphi \qquad (\|v\| = 1)$$

![[Calculus 8 gradient angle.svg]]

It is largest for the angle $\varphi = 0$ (*za kot $\varphi = 0$ bo največji*): the maximum is at $\varphi = 0$ and $\varphi = \pi$:

$$\varphi = 0: \; v = \frac{\nabla f}{\|\nabla f\|} \;\text{(the vector is in the direction of the gradient — } \textit{vektor je v smeri gradienta}\text{)}, \qquad \varphi = \pi: \; v = -\frac{\nabla f}{\|\nabla f\|}$$

- $\nabla f$ points in the direction of the steepest increase of $f$ (*kaže v smeri največjega naraščanja f*).
- Its size is the slope in that direction (*njegova velikost je naklon v tej smeri*).

#### Level curves (*nivojnica*)

Parametrize a level curve as $(x(t), y(t))$, so $f\big(x(t), y(t)\big) = \text{const}$. Differentiate with respect to $t$:

$$\nabla f \cdot \underbrace{(x', y')}_{\text{tangent to the level curve}} = 0$$

$\nabla f$ is at every point perpendicular to the level curves (*$\nabla f$ je v vsaki točki $\perp$ na nivojnice*).

From the problem before (*iz naloge od prej*), at $(2, -1)$:

![[Calculus 8 gradient at a point.svg]]

### 6. Gradient descent (*gradientni spust*, GD)

We are looking for the minimum of a function $f$ (*iščemo minimum funkcije f*). $x_1$ is the first approximation (*prvi približek*):

$$\text{GD:} \quad x_{k+1} = x_k - \gamma \cdot \nabla f, \qquad \gamma > 0$$

#### Example: linear regression (*linearna regresija*)

Draw a function through the points on the left (*skozi točke na levi napelji funkcijo*):

![[Calculus 8 linear regression.svg]]

Find the linear function that best approximates the data (*poišči linearno funkcijo, ki naj aproksimira podatke*). We demonstrate the solution with one step of GD (*rešitev demonstriramo z enim korakom GD*).

First approximation (*prva aproksimacija*): $y = 1 \cdot x + 0 = kx + n$.

Question (*vprašanje*): how should we change $k$ and $n$ so that the line $y = kx + n$ fits better (*bolje prilegala*)? This is how neural networks work (*tako delujejo nevronske mreže*).

The **loss function** $f$ (the notebook writes $f(k, m)$):

$$f(k, n) = \big((k + n) - 2\big)^2 + \big((2k + n) - 5\big)^2 + \big((3k + n) - 1\big)^2$$

$$f_k = 2(k + n - 2) + 2 \cdot 2(2k + n - 5) + 3 \cdot 2(3k + n - 1)$$

$$f_n = 2(k + n - 2) + 2(2k + n - 5) + 2(3k + n - 1)$$

$$f_k(1, 0) = 2(1 - 2) + 4(2 - 5) + 6(3 - 1) = -2 - 12 + 12 = -2$$

$$f_n(1, 0) = 2(1 - 2) + 2(2 - 5) + 2(3 - 1) = -2 - 6 + 4 = -4$$

$$\nabla f(1, 0) = (-2, -4)$$

One GD step from $(k, n) = (1, 0)$:

$$(1, 0) - \gamma(-2, -4) = (1 + 2\gamma,\ 4\gamma)$$

Answer (*odgovor*): $y = (1 + 2\gamma)\,x + 4\gamma$.

## Questions

- [ ] Was the example function $x y^2 + x e^y$ or $x y^2 + x e^y + y$ (with $f_y(1, 0) = 2$)?
- [ ] In the example $(2, -1) + t(1, -1)$, the point at $t = 1$ is labelled $(1, -1)$. Is that the direction, not the point $(3, -2)$?

## Connections

- Course: [[Calculus]]
- Previous lecture: [[2026-11-18 - Functions of Several Variables, Derivatives and L'Hôpital's Rule - 7]] — functions of several variables, level curves, the derivative as a limit of the difference quotient, the chain rule in one variable and neural networks
- [[2026-11-11 - Limits of Functions, Continuity and Zeros of Continuous Functions - 6]] — gradient descent in 1D, $a_{n+1} = a_n - \operatorname{sign} f'(a_n) \cdot \mu$
- [[2026-11-17 - Electric Field, Gauss's Law and Capacitors - 7]] — Physics: the field from the potential with the gradient, field lines perpendicular to equipotential surfaces (like $\nabla f \perp$ level curves)
- [[Derivative]], [[Partial Derivative]], [[Directional Derivative]], [[Gradient]], [[Differentiability]], [[Chain Rule]], [[Level Set]], [[Gradient Descent]], [[Linear Regression]], [[Neural Network]], [[Function of Several Variables]], [[Parameter]]

## Sources

- Handwritten notes: [[Sources/calculus/photoNotes/lectures/lecture 8.pdf|lecture 8]]
- *Analiza II* (skriptaII): 1.4 vector functions, velocity as the derivative of $r(t)$ [[Sources/calculus/skriptaII.pdf#page=17|pp. 11–12]]; 1.5 partial derivatives [[Sources/calculus/skriptaII.pdf#page=20|pp. 14–16]], differentiability (Definicija 10, Izrek 8) [[Sources/calculus/skriptaII.pdf#page=24|pp. 18–19]], slope in the $x$ and $y$ directions [[Sources/calculus/skriptaII.pdf#page=27|p. 21]], continuous partial derivatives ⇒ differentiable (Izrek 9) [[Sources/calculus/skriptaII.pdf#page=29|p. 23]]; 1.6 differentiability of a composition (Izrek 12) [[Sources/calculus/skriptaII.pdf#page=39|p. 33]] and its example [[Sources/calculus/skriptaII.pdf#page=42|p. 36]]; 5.1 directional derivative and gradient [[Sources/calculus/skriptaII.pdf#page=179|p. 173]]
