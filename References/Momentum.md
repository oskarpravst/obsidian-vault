---
type: "[[Concepts]]"
status: developed
aliases:
  - Gibalna količina
  - Linear momentum
---

# Momentum

## Definition

The momentum (*gibalna količina*) of a body is

$$\vec{G} = m\,\vec{v} \qquad [\text{kg}\,\text{m/s}]$$

For a system of bodies it is the sum of the momenta, which equals the total mass times the velocity of the [[Centre of Mass|centre of mass]]:

$$\vec{G}^s = \sum_{i=1}^{N} m_i\vec{v}_i = m\,\vec{v}^*, \qquad m = \sum_{i=1}^{N} m_i$$

## Explanation

- Integrating Newton's 2nd law over time gives the **theorem of momentum**: the [[Impulse|impulse]] of the external forces equals the change of momentum,

$$\int_{t_z}^{t_k} \vec{F}_z\,dt = \Delta\vec{G}$$

- **Conservation of momentum** (*ohranitev gibalne količine*): if the impulse of the external forces is zero, the total momentum does not change, whatever happens inside the system:

$$\sum_{i} m_i \vec{v}_i^{\,z} = \sum_{i} m_i \vec{v}_i^{\,k}$$

- Internal forces (between the bodies) cancel in pairs by Newton's 3rd law, so they cannot change $\vec{G}^s$.
- The lecture calls this a **law** (it always holds), unlike the theorem of kinetic and potential energy, which does not hold in every case.
- Momentum is a **vector**: it is conserved in each direction separately, and velocities in opposite directions have opposite signs.

## Examples

**Newton's cradle** (Physics 4): $m_1\vec{v}_1^{\,z} = m_N\vec{v}_N^{\,k}$ — it does not matter what happens in between.

**Inelastic collision** (Physics 4): the carts stick together,

$$m_1 v_1^z + m_2 v_2^z = (m_1 + m_2)\,v_k$$

**Elastic collision** (Physics 4): momentum alone gives one equation with two unknowns; conservation of kinetic energy gives the second.

**Rocket** (Physics 4): momentum before and after ejecting $\Delta m$ of gas gives $m(t)\,a = v_{rel}\,\Phi_m$.

## Connections

- [[2026-10-20 - Forces, Work, Energy and Momentum - 3]] — definition, theorem of momentum (Physics)
- [[2026-10-27 - Systems of Bodies, Collisions and Rotation - 4]] — system of bodies, Newton's cradle, collisions, rocket (Physics)
- [[Impulse]], [[Newton's Laws]], [[Centre of Mass]], [[Elastic Collision]], [[Inelastic Collision]], [[Rocket Equation]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), sections 8.1–8.2: [[Sources/physics/FRI_Fizika.pdf#page=61|pp. 61–66]]
