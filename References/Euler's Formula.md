---
type: "[[Concepts]]"
status: developed
aliases:
  - Eulerjeva formula
---

# Euler's Formula

## Definition

$$e^{i\varphi} = \cos\varphi + i\sin\varphi, \qquad \varphi \in \mathbb{R}$$

## Explanation

- $e^{i\varphi}$ is the point on the **unit circle** at angle $\varphi$, so $|e^{i\varphi}| = 1$.
- Every [[Complex Number|complex number]] can be written in **polar form**: $z = r(\cos\varphi + i\sin\varphi) = r e^{i\varphi}$.
- **Multiplying means rotating:** the usual rules for exponents hold, so absolute values multiply and angles add:
  $$r_1 e^{i\varphi_1} \cdot r_2 e^{i\varphi_2} = r_1 r_2\, e^{i(\varphi_1 + \varphi_2)}$$
  Multiplying by $e^{i\alpha}$ rotates the plane around $0$ by $\alpha$.
- It is a shortcut for the trigonometric addition formulas. Multiplying out $(\cos\varphi_1 + i\sin\varphi_1)(\cos\varphi_2 + i\sin\varphi_2)$ gives $\cos(\varphi_1 + \varphi_2) + i\sin(\varphi_1 + \varphi_2)$.
- **Cosine and sine from exponentials** (since $e^{-it} = \overline{e^{it}}$):
  $$\cos t = \operatorname{Re}(e^{it}) = \frac{e^{it} + e^{-it}}{2}, \qquad \sin t = \operatorname{Im}(e^{it}) = \frac{e^{it} - e^{-it}}{2i}$$
- The angle is only determined up to $2k\pi$: $e^{i\varphi} = e^{i(\varphi + 2k\pi)}$, $k \in \mathbb{Z}$.

## Examples

**Special values** (Calculus 2):

$$1 = e^{i \cdot 0}, \quad i = e^{i\frac{\pi}{2}}, \quad -1 = e^{i\pi} = e^{-i\pi}, \quad -i = e^{i\frac{3\pi}{2}} = e^{-i\frac{\pi}{2}}, \quad 1 + i = \sqrt{2}\,e^{i\frac{\pi}{4}}$$

**Powers ([[De Moivre's Formula]]):** $(r e^{i\varphi})^n = r^n e^{in\varphi}$. E.g. $z = 1 - i\sqrt{3} = 2e^{-i\frac{\pi}{3}}$, so $z^3 = 8e^{-i\pi} = -8$.

**Roots:** the solutions of $z^n = r e^{i\varphi}$ are $z_k = \sqrt[n]{r}\, e^{i\frac{\varphi + 2k\pi}{n}}$, $k = 0, \dots, n-1$. They form a regular $n$-gon.

**Signals** (Calculus 3): the frequency vectors of the [[Discrete Fourier Transform|DFT]] are $C_k = \left(e^{i2\pi\frac{kn}{N}}\right)_{n=0}^{N-1}$. With the formulas for $\cos$ and $\sin$:

$$\cos t + \sin t = \left(\tfrac{1}{2} - \tfrac{i}{2}\right)e^{it} + \left(\tfrac{1}{2} + \tfrac{i}{2}\right)e^{-it} = \sqrt{2}\cos\left(t - \tfrac{\pi}{4}\right)$$

## Connections

- [[2026-10-14 - Polar Form of Complex Numbers - 2]]: polar form, multiplication, powers, roots (Calculus)
- [[2026-10-21 - Spectral Decomposition and Sequences - 3]]: $\cos$ and $\sin$ as exponentials, spectral decomposition (Calculus)
- [[Complex Number]], [[De Moivre's Formula]], [[Discrete Fourier Transform]]
- [[Circular Motion]]: $t \mapsto r e^{i\omega t}$ traces the same circle as $\vec{r}(t) = (r\cos\omega t,\ r\sin\omega t)$ (Physics)

## Sources

- Course script: [[Sources/calculus/mat1 (2).pdf#page=32|mat1, 1.3 polar form]]
- [Euler's formula — Wikipedia](https://en.wikipedia.org/wiki/Euler%27s_formula)
