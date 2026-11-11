---
type: "[[Concepts]]"
status: developed
aliases:
  - Newtonovi zakoni
  - Newton's laws of motion
  - Newton's 2nd law
---

# Newton's Laws

## Definition

Newton's laws (*Newtonovi zakoni*, 1687) for a point body:

1. **First law:** if no force acts on a body, or the sum of the forces is zero, the body is at rest or moves in a straight line at constant velocity:
   $$\sum_i \vec{F}_i = 0 \implies \vec{a} = 0 \iff \vec{v} = \text{const.}$$
2. **Second law:** the sum of the forces equals mass times acceleration:
   $$\sum_i \vec{F}_i = m\vec{a}$$
3. **Third law, action and reaction** (*akcija – reakcija*): if body 1 acts on body 2 with a force, body 2 acts on body 1 with an equal and opposite force:
   $$\vec{F}_{2\to1} = -\vec{F}_{1\to2}$$

## Explanation

- A **force** is an external influence (*zunanji vpliv*) that changes the motion of a body or deforms it. Unit: $\text{N} = \text{kg}\,\text{m/s}^2$.
- **Mass is inertia** (*inercija*): resistance to changes of motion. The acceleration is the *consequence* of the force, not the other way round.
- The laws hold in an **inertial frame** (*inercialni sistem*).
- $\vec{F} = m\ddot{\vec{r}}$ is a differential equation. Solving it gives the motion $\vec{r}(t)$.
- **Systems of bodies:** the internal forces cancel in pairs (3rd law), so only external forces accelerate the [[Centre of Mass|centre of mass]]:
  $$\vec{F}_z = m_s\,\vec{a}_*$$
- **Limits:** in Newton's picture the influence is instantaneous, but in reality there is a response time. Mercury's orbit does not quite agree with Newton's equations, and light, which has no mass, is bent by galaxies ([[Gravitational Lensing|gravitational lensing]]). Both lead to the general theory of gravitation ([[General Relativity|general relativity]]).

**The 2nd law leads to the conservation theorems** (Physics 3):

- Multiply by $d\vec{s}$ and integrate along the path to get [[Work|work]] and [[Kinetic Energy|kinetic energy]]: $A = \Delta W_k$.
- Integrate over time $dt$ to get [[Impulse|impulse]] and [[Momentum|momentum]]: $\int \vec{F}_z\,dt = \Delta\vec{G}$, with $\vec{G} = m\vec{v}$.

## Examples

- **Free fall:** only gravity acts, $m\vec{g} = m\vec{a}$, so $\vec{a} = \vec{g}$ for every body.
- **Circular motion:** for [[Circular Motion|circular motion]] the sum of external forces must be the [[Centripetal Force|centripetal force]] $F_c = m\omega^2 r$.
- **Spring** (3rd law): the external force stretches the spring, and the spring pulls back on its surroundings with the opposite force.
- **Incline with [[Friction|friction]]** (vaje 3, task 3.2): perpendicular to the incline $\sum F = 0$ (1st law), along it $mg\sin\varphi - F_{tr} = ma$ (2nd law).
- **Statics vs. dynamics** (vaje 3): in statics the forces are in balance ($\sum \vec{F} = 0$); in dynamics $\sum \vec{F} \neq 0$ and the body accelerates.

## Connections

- [[2026-10-13 - Circular Motion and Newton's Laws - 2]]: the three laws, systems of bodies, centre of mass, force of gravity (Physics)
- [[2026-10-20 - Forces, Work, Energy and Momentum - 3]]: spring (3rd law), centripetal force, work and momentum from the 2nd law, beyond Newton (Physics)
- [[2026-11-10 - Physical Pendulum, Waves and Electrostatics - 6]] — Newton's 2nd law for rotation of the physical pendulum (Physics)
- Exercises: [[Sources/physics/photoNotes/vaje/vaje 3.pdf|vaje 3]]: Newton's laws, statics and dynamics, tasks 3.1 and 3.2
- [[Newton's Law of Universal Gravitation]], [[Friction]], [[Circular Motion]], [[Centre of Mass]], [[Momentum]], [[Work]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), section 6.1: [[Sources/physics/FRI_Fizika.pdf#page=45|p. 45]]
