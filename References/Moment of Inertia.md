---
type: "[[Concepts]]"
status: developed
aliases:
  - Vztrajnostni moment
---

# Moment of Inertia

## Definition

The **moment of inertia** (*vztrajnostni moment*) of a body about an axis is

$$J = \sum_{i=1}^{N} m_i r_i^2 \quad\longrightarrow\quad J = \int_V r^2\,dm, \qquad dm = \rho\,dV \qquad [\text{kg}\,\text{m}^2]$$

where $r_i$ is the distance of the mass $m_i$ from the **axis of rotation** (not from the origin).

## Explanation

- It plays the role of mass in rotation. In **Newton's 2nd law for a rigid body** $\vec{M}_z = J\vec{\alpha}$ it replaces $m$ in $\vec{F} = m\vec{a}$.
- We get it by summing $\vec{M}_i = m_i r_i^2\vec{\alpha}$ over all atoms of a rigid body. $\vec{\alpha}$ is the same for all of them, so it can be taken out of the sum.
- It depends on the **axis**: the same body has a different $J$ for each axis. Mass far from the axis counts more ($r^2$).
- It appears in the [[Angular Momentum|angular momentum]] $\vec{\Gamma} = J\vec{\omega}$ and in the kinetic energy of rotation $\frac{1}{2}J\omega^2$:

$$W_k = \frac{1}{2}mv_*^2 + \frac{1}{2}J\omega^2$$

## Examples

**Bodies about their own axis through the centre of mass** (Physics 4):

| body | $J$ |
|---|---|
| solid sphere (*krogla*; notebook: *sfera*) | $\frac{2}{5}mR^2$ |
| cylinder (*valj*) | $\frac{1}{2}mR^2$ |
| cylindrical shell / ring (*plašč valja / obroč*) | $mR^2$ (all mass at distance $R$, as if it were a point) |

**Spinning person** (Physics 5): pulling the arms in makes $J$ smaller. $\Gamma = J\omega$ is conserved, so $\omega$ grows and the person spins faster.

**Mathematical pendulum** (Physics 6): a point mass on a string of length $l$ has $J = ml^2$, so the period of the physical pendulum $t_0 = 2\pi\sqrt{J/(mgr_*)}$ becomes $2\pi\sqrt{l/g}$.

## Connections

- [[2026-10-27 - Systems of Bodies, Collisions and Rotation - 4]] — definition, table of $J$, $\vec{M} = J\vec{\alpha}$, rotational kinetic energy (Physics)
- [[2026-11-03 - Angular Momentum, Kepler's Laws, Precession and Oscillations - 5]] — $\vec{\Gamma} = J\vec{\omega}$, spinning person (Physics)
- [[2026-11-10 - Physical Pendulum, Waves and Electrostatics - 6]] — period of the physical pendulum (Physics)
- [[Torque]], [[Angular Momentum]], [[Centre of Mass]], [[Integral]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), 9.4 *Vztrajnostni moment in rotacijska energija*: [[Sources/physics/FRI_Fizika.pdf#page=71|p. 71–76]]
