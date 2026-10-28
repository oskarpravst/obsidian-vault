---
type: "[[Concepts]]"
status: developed
aliases:
  - Sunek sile
  - Sunek
---

# Impulse

## Definition

The impulse (*sunek sile*) of a force over a time interval is

$$\int_{t_z}^{t_k} \vec{F}\,dt \qquad [\text{N}\,\text{s} = \text{kg}\,\text{m/s}]$$

For a constant force it is simply $\vec{F}\,t$. The impulse has no special symbol.

## Explanation

- The impulse of the external forces equals the change of [[Momentum|momentum]]:

$$\int_{t_z}^{t_k} \vec{F}_z\,dt = m\vec{v}_k - m\vec{v}_z = \Delta\vec{G}$$

  This comes from integrating Newton's 2nd law $\vec{F}_z = m\vec{a}$ over **time** (integrating it over the **path** gives [[Work|work]] instead).
- Work and energy are scalars; impulse and momentum are **vectors**.
- The same change of momentum can come from a large force for a short time or a small force for a long time — what counts is the integral.
- If the impulse of the external forces is zero, momentum is conserved (e.g. a bomb that explodes, collisions on an air track where friction is neglected).

## Examples

**Theorem of momentum** (Physics 3):

$$\vec{F}_z = m\vec{a} \;\longrightarrow\; \int_{t_z}^{t_k} \vec{F}_z\,dt = \int_{t_z}^{t_k} m\vec{a}\,dt = m(\vec{v}_k - \vec{v}_z)$$

**System of bodies** (Physics 4): $\int_{t_z}^{t_k} \vec{F}_z\,dt = \vec{G}^s_k - \vec{G}^s_z$; with zero impulse, $0 = \Delta\vec{G}^s$.

## Connections

- [[2026-10-20 - Forces, Work, Energy and Momentum - 3]] — definition, impulse of the external forces (Physics)
- [[2026-10-27 - Systems of Bodies, Collisions and Rotation - 4]] — systems of bodies, conservation of momentum (Physics)
- [[Momentum]], [[Integral]], [[Newton's Laws]], [[Work]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), section 8.1: [[Sources/physics/FRI_Fizika.pdf#page=61|p. 61]]
