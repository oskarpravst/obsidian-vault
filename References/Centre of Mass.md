---
type: "[[Concepts]]"
status: developed
aliases:
  - Masno središče
  - Težišče
  - Center of mass
---

# Centre of Mass

## Definition

The **centre of mass** (*masno središče*) of a system of $N$ bodies is the mass-weighted average of their positions:

$$\vec{r}_* = \frac{\sum_{i=1}^{N} m_i\vec{r}_i}{m_s}, \qquad m_s = \sum_{i=1}^{N} m_i$$

Differentiating gives its velocity $\vec{v}_* = \frac{\sum m_i\vec{v}_i}{m_s}$ and acceleration $\vec{a}_* = \frac{\sum m_i\vec{a}_i}{m_s}$.

## Explanation

- **Newton's 2nd law for a system:** $\vec{F}_z = m_s\vec{a}_*$. The centre of mass moves as if the whole mass were there and all external forces acted on it. Internal forces cancel.
- The total [[Momentum|momentum]] of the system is $\vec{G} = m_s\vec{v}_*$. If the external [[Impulse|impulse]] is zero, the centre of mass keeps a constant velocity.
- The motion of a system splits into 2 parts: the **motion of the centre of mass** and the **rotation around it** (described by [[Torque|torque]]).
- In a uniform gravitational field it coincides with the **centre of gravity** (*težišče*).

## Examples

**Force couple** (Physics 4): the two forces cancel, $\vec{F}_z = 0$, so the centre of mass stays at rest, yet the system rotates.

**Physical pendulum** (Physics 6): $\vec{r}_*$ points from the axis to the centre of mass, and the torque of gravity is $\vec{r}_* \times \vec{F}_g$.

**Kinetic energy of a rigid body** (Physics 4): $W_k = \frac{1}{2}mv_*^2 + \frac{1}{2}J\omega^2$, the motion of the centre of mass plus rotation around it.

## Connections

- [[2026-10-13 - Circular Motion and Newton's Laws - 2]] — definition for 3 and $N$ bodies, $\vec{F}_z = m_s\vec{a}_*$ (Physics)
- [[2026-10-27 - Systems of Bodies, Collisions and Rotation - 4]] — momentum of a system, motion of a system of bodies, force couple (Physics)
- [[Momentum]], [[Newton's Laws]], [[Torque]], [[Moment of Inertia]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), 9.1 *Masno središče in težišče*: [[Sources/physics/FRI_Fizika.pdf#page=67|p. 67]]; 9.2 *Gibanje težišča sistema teles*: [[Sources/physics/FRI_Fizika.pdf#page=69|p. 69]]
