---
type: "[[Concepts]]"
status: developed
aliases:
  - Določeni integral
  - Definite integral
---

# Integral

## Definition

The definite integral adds up very many very small contributions $f(x)\,dx$ between $a$ and $b$:

$$\int_a^b f(x)\,dx = \lim_{\Delta x \to 0} \sum_i f(x_i)\,\Delta x$$

Geometrically it is the area under the graph of $f$. If $F$ is an antiderivative ($\dot{F} = f$), then

$$\int_a^b f(x)\,dx = F(x)\Big|_a^b = F(b) - F(a)$$

## Explanation

- The integral is the inverse of the [[Derivative|derivative]]: integrating a rate of change gives the total change.
- Power rule: $\int t^n\,dt = \dfrac{t^{n+1}}{n+1}$ ($n \neq -1$).
- In physics the integral appears whenever a quantity changes along the way and we "add up the whole path" (*seštejemo celotno pot*): split the path or time into pieces so small that the quantity is constant on each, multiply, and add.
- Write the integration variable differently from the upper limit ($t'$ vs. $t$) when the limit is a variable.
- For a body we integrate over its mass: $dm = \rho\,dV$.

## Examples

**Kinematics** (Physics 1):

$$v(t) = v(t_0) + \int_{t_0}^{t} a(t')\,dt', \qquad x(t) = x_0 + \int_{t_0}^{t} v(t')\,dt'$$

With constant $a_0$: $x(t) = x_0 + v_0 t + \frac{1}{2}a_0 t^2$.

**[[Work]]** (Physics 3): along the path,

$$A = \int_{\vec{r}_z}^{\vec{r}_k} \vec{F} \cdot d\vec{s}, \qquad A_{vz} = -k\int_{x_z}^{x_k} x\,dx = -\left(\tfrac{1}{2}kx_k^2 - \tfrac{1}{2}kx_z^2\right)$$

**[[Impulse]]** (Physics 3): over time, $\int_{t_z}^{t_k} \vec{F}\,dt = \Delta\vec{G}$.

**[[Moment of Inertia]]** (Physics 4): over the mass of a body, $J = \int_V r^2\,dm$.

**Rocket** (Physics 4): mass left after burning with a changing mass flow rate, $m(t) = m_{zač} - \int_{t_z}^{t_k} \Phi_m(t)\,dt$.

## Connections

- [[2026-10-11 - Physical Quantities and Kinematics - 1]] — velocity and position as integrals (Physics)
- [[2026-10-20 - Forces, Work, Energy and Momentum - 3]] — work and impulse (Physics)
- [[2026-10-27 - Systems of Bodies, Collisions and Rotation - 4]] — moment of inertia, rocket mass, work of a torque (Physics)
- [[Derivative]], [[Work]], [[Impulse]], [[Moment of Inertia]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), section 3.2: [[Sources/physics/FRI_Fizika.pdf#page=12|pp. 12–19]]
- [Integral — Wikipedia](https://en.wikipedia.org/wiki/Integral)
