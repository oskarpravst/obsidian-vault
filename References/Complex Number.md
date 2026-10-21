---
type: "[[Concepts]]"
status: developed
aliases:
  - Complex numbers
  - Kompleksno število
  - Kompleksna števila
---

# Complex Number

## Definition

We introduce a new number $i$ with $i^2 = -1$. A complex number (*kompleksno število*) is

$$z = x + iy, \qquad x, y \in \mathbb{R}, \qquad \mathbb{C} = \{x + iy;\ x, y \in \mathbb{R}\}$$

- $x = \operatorname{Re}(z)$ is the real part (*realna komponenta*),
- $y = \operatorname{Im}(z)$ is the imaginary part (*imaginarna komponenta*).

## Explanation

**Complex plane** (*kompleksna ravnina*): $z = x + iy$ is the point $(x, y)$, with the real axis horizontal and the imaginary axis vertical.

**Conjugate and absolute value:**

- Conjugate (*konjugirano število*): $\bar{z} = x - iy$, the reflection across the real axis.
- Absolute value (modulus): $|z|^2 = z\bar{z} = x^2 + y^2$, the distance from $0$.
- $x = \frac{z + \bar{z}}{2}$, $y = \frac{z - \bar{z}}{2i}$, $\ \overline{z_1 z_2} = \bar{z}_1 \bar{z}_2$, $\ |z_1 z_2| = |z_1|\,|z_2|$, $\ |z_1 + z_2| \leq |z_1| + |z_2|$ (triangle inequality).

**Two forms:**

| | Cartesian (*kartezični zapis*) | Polar (*polarni zapis*) |
|---|---|---|
| form | $z = x + iy$ | $z = r(\cos\varphi + i\sin\varphi) = r e^{i\varphi}$ |
| good for | $+$, $-$ | $\cdot$, $/$, powers, roots |

Conversion: $x = r\cos\varphi$, $y = r\sin\varphi$; $r = |z| = \sqrt{x^2 + y^2}$, $\tan\varphi = \frac{y}{x}$. The argument $\varphi$ is only determined up to $2k\pi$, and the **quadrant** must be taken into account. The polar form rests on [[Euler's Formula|Euler's formula]].

**Operations as transformations of the plane:** $z \mapsto z + z_0$ is a shift, $z \mapsto \bar{z}$ a reflection, $z \mapsto rz$ a stretch, and $z \mapsto z e^{i\alpha}$ a rotation by $\alpha$.

**Why $\mathbb{C}$:** by the [[Fundamental Theorem of Algebra|fundamental theorem of algebra]], every polynomial of degree $n \geq 1$ has exactly $n$ zeros in $\mathbb{C}$ (counted with multiplicity). Real polynomials have their non-real zeros in conjugate pairs. Complex numbers are also used in signal processing: the [[Discrete Fourier Transform|DFT]] writes a signal as a sum of complex exponentials.

## Examples

**Division:** multiply by the conjugate of the denominator:

$$\frac{1 + 2i}{1 + i} \cdot \frac{1 - i}{1 - i} = \frac{3 + i}{2}$$

**Equation $2\bar{z} = z^2$:** comparing real and imaginary parts gives $z \in \{0,\ 2,\ -1 \pm i\sqrt{3}\}$.

**Polar form, watch the quadrant:** $1 + i = \sqrt{2}e^{i\frac{\pi}{4}}$, but $-1 - i = \sqrt{2}e^{i\frac{5\pi}{4}}$, although $\tan\varphi = 1$ in both cases.

**Roots:** $z^5 = 32$ has 5 solutions $z_k = 2e^{i\frac{2k\pi}{5}}$, which form a regular pentagon, and their sum is $0$.

## Connections

- [[2026-10-11 - Numbers - 1]]: definition, arithmetic, conjugate, absolute value (Calculus)
- [[2026-10-14 - Polar Form of Complex Numbers - 2]]: polar form, geometry of operations, roots, fundamental theorem of algebra (Calculus)
- [[2026-10-21 - Spectral Decomposition and Sequences - 3]]: why complex numbers are used, spectral decomposition (Calculus)
- [[Euler's Formula]], [[De Moivre's Formula]], [[Fundamental Theorem of Algebra]], [[Discrete Fourier Transform]]

## Sources

- J. Globevnik, M. Brojan, *Analiza I* (2012), section 1.7: [[Sources/calculus/skripta.pdf#page=31|skripta p. 21]], 1.7.1 geometric representation [[Sources/calculus/skripta.pdf#page=38|p. 28]]
- Course script: [[Sources/calculus/mat1 (2).pdf#page=32|mat1, 1.3 polar form]]
