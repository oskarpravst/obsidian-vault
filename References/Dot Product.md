---
type: "[[Concepts]]"
status: developed
aliases:
  - Scalar product
  - Skalarni produkt
---

# Dot Product

## Definition

The dot product (*skalarni produkt*) assigns a **number** (a scalar) to two vectors:

$$\vec{a} \cdot \vec{b} = |\vec{a}|\,|\vec{b}|\cos\vartheta = a_x b_x + a_y b_y + a_z b_z = \sum_{i=1}^{3} a_i b_i$$

where $\vartheta$ is the angle between $\vec{a}$ and $\vec{b}$. In $n$ dimensions: $(v_1, \dots, v_n) \cdot (w_1, \dots, w_n) = v_1 w_1 + \dots + v_n w_n$.

## Explanation

- **Order does not matter:** $\vec{a} \cdot \vec{b} = \vec{b} \cdot \vec{a}$.
- **Length of a vector:** with itself ($\vartheta = 0$): $\vec{a} \cdot \vec{a} = |\vec{a}|^2$, so $|\vec{a}| = \sqrt{\vec{a} \cdot \vec{a}}$.
- **Perpendicular vectors:** $\vartheta = \frac{\pi}{2}$ gives $\vec{a} \cdot \vec{b} = 0$, and conversely, if the dot product is $0$, the vectors are perpendicular.
- **Sign shows the angle:** $\vec{a} \cdot \vec{b} > 0$ means $\vartheta < 90^\circ$; $\vec{a} \cdot \vec{b} < 0$ means $90^\circ < \vartheta \leq 180^\circ$. The angle itself is $\vartheta = \arccos\dfrac{\vec{a} \cdot \vec{b}}{a\,b}$.
- **Projection:** $\vec{F} \cdot d\vec{s} = F\,ds\cos\theta$ keeps only the part of $\vec{F}$ along $d\vec{s}$. That is why [[Work|work]] is defined with a dot product.

**Complex vectors.** For vectors with complex entries the second vector is conjugated:

$$\langle v, w \rangle = \sum_{k} v_k\,\overline{w_k}, \qquad \langle v, v \rangle = \sum_k |v_k|^2 \geq 0$$

Without the conjugate, $v \cdot v$ could be $0$ or negative for a nonzero vector (e.g. $(1, i) \cdot (1, i) = 1 + i^2 = 0$). Calculus 3 computes exactly this way ($a \cdot \bar{a}$, $a \cdot \bar{b}$), though its handwritten definition is the real one.

## Examples

**Speed in circular motion** (Physics 2): $v^2 = \vec{v} \cdot \vec{v} = (r\omega)^2\big((-\sin\varphi)^2 + \cos^2\varphi\big) = (r\omega)^2$, and $\vec{r} \cdot \vec{v} = 0$, so $\vec{v} \perp \vec{r}$ in [[Circular Motion|circular motion]].

**Work** (Physics 3):

$$A = \int_{\vec{r}_z}^{\vec{r}_k} \vec{F} \cdot d\vec{s}$$

- Friction points along $-d\vec{s}$, so $\cos\theta = -1$ and $A < 0$.
- In uniform circular motion $\vec{F}_z \perp d\vec{s}$, so $A = 0$ and the speed stays constant.

**Complex vectors** (Calculus 3): $a = (1, i, -1, -i)$, $b = (1, -1, 1, -1)$:

$$a \cdot \bar{a} = 4 = b \cdot \bar{b}, \qquad a \cdot \bar{b} = 1 - i - 1 + i = 0$$

The frequency vectors $C_k$ of the [[Discrete Fourier Transform|discrete Fourier transform]] are pairwise perpendicular in this sense: $C_p \cdot \overline{C_q} = 0$ for $p \neq q$ and $N$ for $p = q$. That is how the coefficients are found.

## Connections

- [[2026-10-11 - Physical Quantities and Kinematics - 1]]: $r^2 = \vec{r} \cdot \vec{r}$ (Physics)
- [[2026-10-13 - Circular Motion and Newton's Laws - 2]]: definition, $|\vec{v}| = r\omega$, $\vec{v} \perp \vec{r}$ (Physics)
- [[2026-10-20 - Forces, Work, Energy and Momentum - 3]]: work $\vec{F} \cdot d\vec{s}$ and its sign (Physics)
- [[2026-10-21 - Spectral Decomposition and Sequences - 3]]: scalar product of complex vectors, DFT (Calculus)
- [[2026-11-03 - Angular Momentum, Kepler's Laws, Precession and Oscillations - 5]] — precession: the torque is perpendicular to $\vec{\Gamma}$, so the dot product is $0$ (Physics)
- [[2026-11-10 - Physical Pendulum, Waves and Electrostatics - 6]] — electric work $\vec{F}_e \cdot d\vec{r}$ (Physics)
- [[Cross Product]]: the other product of vectors; it gives a vector
- [[Work]], [[Circular Motion]], [[Discrete Fourier Transform]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), section 3.1: [[Sources/physics/FRI_Fizika.pdf#page=10|pp. 10–11]]
- [Dot product — Wikipedia](https://en.wikipedia.org/wiki/Dot_product) (complex vectors)
