---
type: "[[Concepts]]"
status: developed
aliases:
  - Vector product
  - Vektorski produkt
---

# Cross Product

## Definition

The cross product (*vektorski produkt*) of two vectors is a **vector**:

$$\vec{c} = \vec{a} \times \vec{b}, \qquad |\vec{c}| = |\vec{a}|\,|\vec{b}|\sin\theta$$

where $\theta$ is the angle between $\vec{a}$ and $\vec{b}$. $\vec{c}$ is perpendicular to both $\vec{a}$ and $\vec{b}$, and its direction follows the **right-hand rule** (*pravilo desnega vijaka*): turn $\vec{a}$ towards $\vec{b}$ like a screw; $\vec{c}$ points where the screw moves.

In components:

$$\vec{a} \times \vec{b} = (a_y b_z - a_z b_y,\; a_z b_x - a_x b_z,\; a_x b_y - a_y b_x)$$

## Explanation

- **Order matters** (anticommutative): $\vec{a} \times \vec{b} = -(\vec{b} \times \vec{a})$.
- **Parallel vectors:** $\theta = 0$ gives $\vec{a} \times \vec{b} = 0$ — two parallel vectors do not define a plane.
- **Perpendicular vectors:** $\theta = \frac{\pi}{2}$ gives the largest size, $|\vec{a}|\,|\vec{b}|$.
- The size $|\vec{a}|\,|\vec{b}|\sin\theta$ is the area of the parallelogram spanned by $\vec{a}$ and $\vec{b}$, and $b\sin\theta$ is the part of $\vec{b}$ perpendicular to $\vec{a}$.
- Compare with the [[Dot Product|dot product]]: that one gives a **number** and uses $\cos\theta$ (the parallel part); the cross product gives a **vector** and uses $\sin\theta$ (the perpendicular part).
- Product rule for derivatives: $\frac{d}{dt}(\vec{a} \times \vec{b}) = \dot{\vec{a}} \times \vec{b} + \vec{a} \times \dot{\vec{b}}$ (keep the order).

## Examples

**Circular motion** (Physics 2): treat $\vec{\omega}$ as a vector perpendicular to the plane of rotation. Then

$$\vec{v} = \vec{\omega} \times \vec{r}, \qquad v = \omega r \sin\tfrac{\pi}{2} = \omega r$$

$$\vec{a} = \dot{\vec{v}} = \underbrace{\vec{\alpha} \times \vec{r}}_{\vec{a}_t} + \underbrace{\vec{\omega} \times \vec{v}}_{\vec{a}_r}$$

**[[Torque]]** (Physics 4): $\vec{M} = \vec{r} \times \vec{F}$, $M = rF\sin\theta$. Only the part of the force perpendicular to $\vec{r}$, $F_\perp = F\sin\theta$, turns the body; a force along $\vec{r}$ ($\theta = 0$) gives $M = 0$.

**Force couple** (Physics 4): $\vec{r}_1 = -\vec{r}$, $\vec{F}_1 = -\vec{F}$, $\vec{r}_2 = \vec{r}$, $\vec{F}_2 = \vec{F}$:

$$\vec{M}_1 = (-\vec{r}) \times (-\vec{F}) = \vec{r} \times \vec{F}, \qquad \vec{M}_s = 2\,(\vec{r} \times \vec{F})$$

**Point mass on a circle** (Physics 4): $\vec{r} \times m(\vec{\alpha} \times \vec{r}) = mr^2\vec{\alpha}$ (for $\vec{r} \perp \vec{\alpha}$), which leads to the [[Moment of Inertia|moment of inertia]].

## Connections

- [[2026-10-13 - Circular Motion and Newton's Laws - 2]] — definition, $\vec{v} = \vec{\omega} \times \vec{r}$, $\vec{a}_t$ and $\vec{a}_r$ (Physics)
- [[2026-10-27 - Systems of Bodies, Collisions and Rotation - 4]] — torque, force couple, $\vec{M} = mr^2\vec{\alpha}$ (Physics)
- [[Dot Product]] — the other product of vectors; it gives a number
- [[Circular Motion]], [[Torque]], [[Moment of Inertia]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), section 3.1: [[Sources/physics/FRI_Fizika.pdf#page=11|p. 11]]
- [Cross product — Wikipedia](https://en.wikipedia.org/wiki/Cross_product)
