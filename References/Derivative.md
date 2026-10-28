---
type: "[[Concepts]]"
status: developed
aliases:
  - Odvod
---

# Derivative

## Definition

The derivative of a quantity $y(x)$ with respect to $x$ tells how fast $y$ changes when $x$ changes:

$$\frac{dy}{dx} = \lim_{\Delta x \to 0} \frac{y(x + \Delta x) - y(x)}{\Delta x}$$

Geometrically it is the **slope** (*strmina*) of the tangent to the graph. A derivative with respect to time is written with a dot (Newton's notation): $\dot{x} = \frac{dx}{dt}$, $\ddot{x} = \frac{d^2x}{dt^2}$ (Leibniz's notation).

## Explanation

Rules used so far:

| Rule | Formula |
|---|---|
| power | $\frac{d}{dt}(k\,t^n) = k\,n\,t^{n-1}$ |
| product | $(f \cdot g)' = f' g + f g'$ |
| chain | $\frac{d}{dt} f(g(t)) = f'(g(t))\,\dot{g}(t)$, e.g. $\frac{d}{dt}\cos(\omega t) = -\omega\sin(\omega t)$ |

- **Vectors** are differentiated component by component: $\dot{\vec{r}} = (\dot{x}, \dot{y}, \dot{z})$. The product rule also holds for the [[Dot Product|dot]] and [[Cross Product|cross]] products.
- The derivative and the [[Integral|integral]] are inverse operations: differentiating $x(t)$ gives $v(t)$, integrating $v(t)$ gives back $x(t)$ up to the initial value.
- In physics a derivative is pictured as the quotient of two very small changes, and its unit is the unit of that quotient (e.g. density $\rho = \frac{dm}{dx}$ … kg/m). The script notes that physics takes this limit step while skipping the more involved mathematical justification.

## Examples

**Kinematics** (Physics 1):

$$v(t) = \frac{dx}{dt} = \dot{x}, \qquad a(t) = \frac{dv}{dt} = \dot{v} = \ddot{x}$$

For $x(t) = A\cos(\omega t)$: $v = -A\omega\sin(\omega t)$ and $a = -A\omega^2\cos(\omega t) = -\omega^2 x$.

**Circular motion** (Physics 2): with $\vec{v} = r\dot{\varphi}\,(-\sin\varphi, \cos\varphi, 0)$, the product rule gives the tangential part $r\ddot{\varphi}$ and the radial part $-r\dot{\varphi}^2$ of $\vec{a}$; $\omega = \dot{\varphi}$, $\alpha = \ddot{\varphi}$.

**Kinetic energy** (Physics 3): by the chain/product rule

$$\frac{d}{dt}(v^2) = \frac{d}{dt}(\vec{v} \cdot \vec{v}) = 2\,\vec{v} \cdot \vec{a}$$

which turns $m\int \vec{a} \cdot \vec{v}\,dt$ into $\frac{1}{2}mv_k^2 - \frac{1}{2}mv_z^2$.

## Connections

- [[2026-10-11 - Physical Quantities and Kinematics - 1]] — velocity and acceleration as derivatives, power rule (Physics)
- [[2026-10-13 - Circular Motion and Newton's Laws - 2]] — product rule, $\omega = \dot{\varphi}$, $\alpha = \ddot{\varphi}$ (Physics)
- [[2026-10-20 - Forces, Work, Energy and Momentum - 3]] — $\frac{d}{dt}(v^2) = 2\,\vec{v} \cdot \vec{a}$ (Physics)
- [[Integral]], [[Circular Motion]], [[Kinetic Energy]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), section 3.2: [[Sources/physics/FRI_Fizika.pdf#page=12|pp. 12–19]]
- [Derivative — Wikipedia](https://en.wikipedia.org/wiki/Derivative)
