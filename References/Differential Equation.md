---
type: "[[Concepts]]"
status:
aliases:
  - Diferencialna enačba
---

# Differential Equation

## Definition

A **differential equation** (*diferencialna enačba*) is an equation for an unknown function that contains its [[Derivative|derivatives]]. Its **order** is the order of the highest derivative.

## Explanation

- Newton's 2nd law $m\ddot{x} = F(x, \dot{x}, t)$ is a 2nd order differential equation for the position $x(t)$. Physics uses it to get the motion from the forces.
- A 2nd order equation needs **2 initial conditions** (e.g. $x(0)$ and $v(0)$) to pick one solution.
- One way to solve it: guess the solution (e.g. from an experiment) and check by differentiating that it satisfies the equation.

## Examples

**Harmonic oscillator** (Physics 5): $m\ddot{x} = -kx$. Checking $x = A\sin(\omega t)$: $\ddot{x} = -\omega^2 x$, so $\omega = \sqrt{k/m}$. See [[Harmonic Oscillation]].

**Physical pendulum** (Physics 6): $\ddot{\varphi} + \frac{mgr_*}{J}\sin\varphi = 0$. With $\sin\varphi \approx \varphi$ it becomes the harmonic equation.

**General oscillation** (Physics 6): $\ddot{x} + 2\beta\dot{x} + \omega^2 x = f(t)$ (damping and driving).

## Connections

- [[2026-11-03 - Angular Momentum, Kepler's Laws, Precession and Oscillations - 5]] — mass on a spring, 2nd order equation (Physics)
- [[2026-11-10 - Physical Pendulum, Waves and Electrostatics - 6]] — physical pendulum, damped and driven oscillation (Physics)
- [[Harmonic Oscillation]], [[Derivative]], [[Newton's Laws]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), 10.1 *Sinusno nihanje*: [[Sources/physics/FRI_Fizika.pdf#page=87|p. 87–88]]
