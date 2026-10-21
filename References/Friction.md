---
type: "[[Concepts]]"
status: developed
aliases:
  - Trenje
  - Lepenje
  - Static friction
  - Kinetic friction
---

# Friction

## Definition

Friction is the resistance of a surface to the motion of a body on it. It comes from the roughness of the surfaces (*nazobčenost površine*). There are two kinds:

| | Static friction (*lepenje*) | Kinetic friction (*trenje*) |
|---|---|---|
| when | body at rest, $\vec{v} = 0$ | body moves, $\vec{v} \neq 0$ |
| size | $F_l \leq k_l F_n$ | $F_{tr} = k_{tr} F_n$ |
| direction | against the force trying to move the body | against the motion, $\vec{F}_{tr} \parallel -\vec{v}$ |

- $k_l$ is the coefficient of static friction (*koeficient lepenja*), $k_{tr}$ the coefficient of kinetic friction (*koeficient trenja*), and usually $k_{tr} < k_l$.
- $F_n$ is the **normal** (perpendicular) component of the force of the surface (*normalna komponenta sile podlage*).

## Explanation

- **Static friction adjusts itself.** It is as large as needed to keep the body at rest, $F_l = -F$, but only up to $F_l^{\max} = k_l F_n$. If the pushing force is larger, the body starts to move and kinetic friction takes over.
- The **total force of the surface** is $\vec{F}_p = \vec{F}_n + \vec{F}_{tr}$: one component is perpendicular to the surface and one parallel to it.
- Friction is a **dissipative force** (*disipativna sila*). It always points against the motion, so its [[Work|work]] is negative ($\cos\theta = -1$, $A < 0$). It brakes the body and turns kinetic energy into internal energy. Unlike the force of gravity, it is not a [[Conservative Force|conservative force]].

## Examples

**Exercise 3.1** (vaje 3): a box with $m_p = 10\ \text{kg}$ is also pressed down by a rope, so $F_N = 100\ \text{N} + 25\ \text{N} = 125\ \text{N}$. With $k_l = 0{,}1$:

$$F_l^{\max} = k_l F_N = 12{,}5\ \text{N}$$

The horizontal pull is $14{,}43\ \text{N} > F_l^{\max}$, so the box moves.

**Exercise 3.2** (vaje 3): a body slides down an incline with $\varphi = 10^\circ$, $k_{tr} = 0{,}1$:

- perpendicular to the incline: $F_N = mg\cos\varphi$
- along the incline: $mg\sin\varphi - k_{tr}\,mg\cos\varphi = ma$

$$a = g(\sin\varphi - k_{tr}\cos\varphi) \approx 0{,}737\ \text{m/s}^2$$

On a horizontal surface, friction alone brakes the body: $a_b = -g\,k_{tr} \approx -0{,}98\ \text{m/s}^2$ (the mass cancels out).

## Connections

- [[2026-10-13 - Circular Motion and Newton's Laws - 2]]: static and kinetic friction, coefficients (Physics)
- [[2026-10-20 - Forces, Work, Energy and Momentum - 3]]: friction as a dissipative force, negative work (Physics)
- Exercises: [[Sources/physics/photoNotes/vaje/vaje 3.pdf|vaje 3]], tasks 3.1 and 3.2
- [[Newton's Laws]], [[Work]], [[Conservative Force]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), sections 6.2–6.4: [[Sources/physics/FRI_Fizika.pdf#page=46|pp. 46–48]]
