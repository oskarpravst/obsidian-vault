---
type: "[[Concepts]]"
status: developed
aliases:
  - Delo
  - Mechanical work
---

# Work

## Definition

The work (*delo*) of a force $\vec{F}$ along a path from $\vec{r}_z$ to $\vec{r}_k$ is

$$A = \int_{\vec{r}_z}^{\vec{r}_k} \vec{F} \cdot d\vec{s} \qquad [\text{N}\,\text{m} = \text{J}]$$

where $d\vec{s} = \vec{v}\,dt$ is a small displacement. For a constant force along a straight path, $A = F\,s\cos\theta$.

## Explanation

- Only the part of the force **along the displacement** does work — that is why it is a [[Dot Product|dot product]]: $\vec{F} \cdot d\vec{s} = F\,ds\cos\theta$.
- **Sign:**
  - $A > 0$ when the force has a component along the motion;
  - $A < 0$ for [[Friction|friction]] and air resistance, which always point along $-\vec{v}$ ($\cos\theta = -1$) — dissipative forces brake;
  - $A = 0$ when $\vec{F} \perp d\vec{s}$, e.g. the centripetal force in uniform [[Circular Motion|circular motion]].
- **Work–energy theorem:** multiplying Newton's 2nd law by $d\vec{s}$ and integrating gives $A = \Delta W_k$ — work changes the [[Kinetic Energy|kinetic energy]].
- **[[Conservative Force|Conservative forces]]** (gravity, the spring force) do work that depends only on the start and end position, not on the path. Their work is replaced by [[Potential Energy|potential energy]], $\Delta W_p = -A$:

$$A_{zun} = \Delta W_k + \Delta W_p + \Delta W_{pr}$$

where $A_{zun}$ is the work of all external forces except gravity and the spring force.
- **Rotation:** a [[Torque|torque]] also does work, $A = \int \vec{M} \cdot d\vec{\varphi}$, so for a rigid body $A = \int \vec{F}_z \cdot d\vec{s} + \int \vec{M}_z \cdot d\vec{\varphi}$.
- The unit of torque is also N·m, but torque is **not** work, so it is not written in joules.

## Examples

**Gravity** (Physics 3): $A_g = -mg\,(h_k - h_z)$ — independent of the path; start and end at the same height gives $A_g = 0$.

**Spring** (Physics 3): $A_{vz} = -k\int_{x_z}^{x_k} x\,dx = -\left(\tfrac{1}{2}kx_k^2 - \tfrac{1}{2}kx_z^2\right)$, which defines the elastic energy $W_{pr} = \tfrac{1}{2}kx^2$.

**Elastic collision** (Physics 4): no external work and no losses, $A_z = 0 \implies \Delta W_k = 0$, which gives the second equation for the two unknown velocities.

## Connections

- [[2026-10-20 - Forces, Work, Energy and Momentum - 3]] — definition, sign, work of gravity and of the spring force, the theorem (Physics)
- [[2026-10-27 - Systems of Bodies, Collisions and Rotation - 4]] — elastic collision, work of a torque (Physics)
- [[Dot Product]], [[Integral]], [[Kinetic Energy]], [[Potential Energy]], [[Conservative Force]], [[Friction]], [[Newton's Laws]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), section 7.1: [[Sources/physics/FRI_Fizika.pdf#page=53|p. 53]]; work of a torque, eq. (9.8): [[Sources/physics/FRI_Fizika.pdf#page=70|p. 70]]
