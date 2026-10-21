---
type: "[[Concepts]]"
status: developed
aliases:
  - Kroženje
  - Uniform circular motion
  - Enakomerno kroženje
---

# Circular Motion

## Definition

Circular motion (*kroženje*) is motion at a constant distance $r$ from a centre:

$$|\vec{r}(t)| = r = \text{const.}$$

In the plane the position is described by the angle $\varphi(t)$:

$$\vec{r}(t) = \big(r\cos\varphi(t),\ r\sin\varphi(t),\ 0\big)$$

## Explanation

| Quantity | Definition | Unit |
|---|---|---|
| angular velocity (*kotna hitrost*) | $\omega = \dot{\varphi}$ | rad/s |
| angular acceleration (*kotni pospešek*) | $\alpha = \dot{\omega} = \ddot{\varphi}$ | rad/s² |
| period (*obhodni čas*) | $T$, with $\omega = \frac{2\pi}{T} = 2\pi\nu$ (uniform motion) | s |

**Two special cases:**

- **uniform** (*enakomerno*): $\alpha = 0$, $\omega = \text{const.}$, $\varphi(t) = \varphi_0 + \omega t$
- **uniformly accelerated** (*enakomerno pospešeno*): $\alpha = \text{const.}$, $\omega = \omega_0 + \alpha t$, $\varphi(t) = \varphi_0 + \omega_0 t + \frac{\alpha t^2}{2}$

**Velocity** is tangent to the circle: $|\vec{v}| = v = \omega r$ and $\vec{v} \perp \vec{r}$ (checked with the [[Dot Product|dot product]]: $\vec{r} \cdot \vec{v} = 0$).

**Acceleration** splits into two parts:

| | tangential (*tangentni*) $\vec{a}_t$ | radial (*radialni*) $\vec{a}_r$ |
|---|---|---|
| direction | along $\vec{v}$ | towards the centre, $\vec{a}_r = -\omega^2\vec{r}$ |
| size | $a_t = r\alpha$ | $a_r = \omega^2 r = \dfrac{v^2}{r}$ |

**Vector form** with $\vec{\omega}$ perpendicular to the plane of rotation (up for the positive direction):

$$\vec{v} = \vec{\omega} \times \vec{r}, \qquad \vec{a} = \underbrace{\vec{\alpha} \times \vec{r}}_{\vec{a}_t} + \underbrace{\vec{\omega} \times \vec{v}}_{\vec{a}_r}$$

**Key lesson:** uniform circular motion is **accelerated** motion. The speed is constant, but the direction of $\vec{v}$ keeps changing, so $\vec{a}_r \neq 0$.

**Dynamics:** by [[Newton's Laws|Newton's 2nd law]], the sum of all external forces must point to the centre and have size

$$F_c = m\,a_r = m\omega^2 r$$

This is the [[Centripetal Force|centripetal force]], the condition for circular motion. In uniform circular motion it is perpendicular to the displacement, so it does no [[Work|work]] and the speed stays constant.

## Examples

**Satellite** (Physics 3): gravity provides the centripetal force:

$$G\frac{m M_Z}{r^2} = m\omega^2 r$$

The mass of the satellite cancels out. A geostationary satellite has the same $\omega$ as the Earth.

**Exercise 2.2a** (vaje 3): uniform circular motion with $\omega = 2\ \text{s}^{-1}$, $R = 1{,}5\ \text{m}$:

$$v = \omega R = 3\ \text{m/s}, \qquad a_r = \omega^2 R = 6\ \text{m/s}^2$$

**Complex plane** (Calculus 2): the same $r$, $\varphi$ description is the polar form $z = r e^{i\varphi}$ of a [[Complex Number|complex number]].

## Connections

- [[2026-10-11 - Physical Quantities and Kinematics - 1]]: uniform circular motion in 2D, $\vec{a} = -\omega^2\vec{r}$ (Physics)
- [[2026-10-13 - Circular Motion and Newton's Laws - 2]]: angle description, $\omega$, $\alpha$, tangential and radial acceleration, vector form (Physics)
- [[2026-10-20 - Forces, Work, Energy and Momentum - 3]]: forces in circular motion, centripetal force, satellites, work $= 0$ (Physics)
- [[2026-10-14 - Polar Form of Complex Numbers - 2]]: polar coordinates $r$, $\varphi$ (Calculus)
- Exercises: [[Sources/physics/photoNotes/vaje/vaje 3.pdf|vaje 3]], task 2.2
- [[Centripetal Force]], [[Cross Product]], [[Euler's Formula]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), sections 5.9 uniform circular motion [[Sources/physics/FRI_Fizika.pdf#page=41|p. 41]], 5.10 uniformly accelerated circular motion [[Sources/physics/FRI_Fizika.pdf#page=43|p. 43]], 6.6 centripetal force [[Sources/physics/FRI_Fizika.pdf#page=50|p. 50]]
