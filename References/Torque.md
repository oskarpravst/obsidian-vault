---
type: "[[Concepts]]"
status: developed
aliases:
  - Navor
  - Moment of force
---

# Torque

## Definition

The **torque** (*navor*) of a force $\vec{F}$ about an axis is

$$\vec{M} = \vec{r} \times \vec{F} \qquad [\text{N}\,\text{m}]$$

where $\vec{r}$ is the position vector of the point of application of the force (*prijemališče sile*), measured from the axis. Its size is $M = rF\sin\theta$.

## Explanation

- Torque is to rotation what force is to linear motion. We get it by multiplying Newton's 2nd law vectorially by $\vec{r}$ ([[Cross Product|cross product]]).
- Only the **perpendicular component** $F_\perp = F\sin\theta$ turns the body. A force along $\vec{r}$ ($\theta = 0$) only pulls it, so $M = 0$.
- **Newton's 2nd law for rotation** of a rigid body: $\vec{M}_z = J\vec{\alpha}$, with the [[Moment of Inertia|moment of inertia]] $J$.
- Integrated over time it gives the angular impulse (*sunek navorov*) and the theorem of conservation of [[Angular Momentum|angular momentum]]: $\int \vec{M}\,dt = \Delta\vec{\Gamma}$.
- The unit is N·m, but torque is **not** [[Work|work]], so it is never written in joules. A torque does work when it turns a body through an angle: $A = \int \vec{M} \cdot d\vec{\varphi}$.
- **Sign:** with the positive angle counterclockwise, a torque that turns clockwise is negative.

## Examples

**Force couple** (*dvojica sil*, Physics 4): two opposite forces $\pm\vec{F}$ at $\pm\vec{r}$ do not move the [[Centre of Mass|centre of mass]], but their torques add up: $\vec{M}_s = 2(\vec{r} \times \vec{F})$.

**Point mass on a circle** (Physics 4): $\vec{M} = \vec{r} \times m(\vec{\alpha} \times \vec{r}) = mr^2\vec{\alpha}$.

**Physical pendulum** (Physics 6): the torque of gravity is $M_g = -r_*\,mg\sin\varphi$. It always turns the pendulum back towards equilibrium, which gives [[Harmonic Oscillation|harmonic oscillation]] for small angles.

**Precession** (Physics 5): the torque of gravity on a spinning top is perpendicular to $\vec{\Gamma}$, so it changes only the direction of the angular momentum, not its size.

## Connections

- [[2026-10-27 - Systems of Bodies, Collisions and Rotation - 4]] — definition, force couple, $\vec{M} = J\vec{\alpha}$ (Physics)
- [[2026-11-03 - Angular Momentum, Kepler's Laws, Precession and Oscillations - 5]] — angular impulse, precession of a top (Physics)
- [[2026-11-10 - Physical Pendulum, Waves and Electrostatics - 6]] — torque of gravity on a physical pendulum (Physics)
- [[Cross Product]], [[Moment of Inertia]], [[Angular Momentum]], [[Newton's Laws]], [[Work]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), 9.3 *Navor*: [[Sources/physics/FRI_Fizika.pdf#page=69|p. 69]]; 9.5 *Navor dvojice nasprotno enakih sil*: [[Sources/physics/FRI_Fizika.pdf#page=76|p. 76]]
