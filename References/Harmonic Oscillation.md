---
type: "[[Concepts]]"
status: developed
aliases:
  - Harmonično nihanje
  - Sinusno nihanje
  - Simple harmonic motion
---

# Harmonic Oscillation

## Definition

**Harmonic** (*sinusno*) **oscillation** is motion described by

$$x(t) = A\sin(\omega t + \delta)$$

It is the solution of the [[Differential Equation|differential equation]]

$$\ddot{x} + \omega^2 x = 0$$

- $A$ … amplitude (*amplituda*)
- $\delta$ … phase (*faza*, *fazni zamik*)
- $\omega = \frac{2\pi}{t_0} = 2\pi\nu$ … angular frequency, $t_0$ … period (*nihajni čas*)

## Explanation

- **Whenever** a quantity obeys $\ddot{y} = -\omega^2 y$, the solution is harmonic oscillation, no matter what the quantity is (position, angle, later charge in an LC circuit).
- $\omega$ is a **property of the system** (e.g. $\omega = \sqrt{k/m}$ for a spring). $A$ and $\delta$ come from the **2 initial conditions** $x(0)$ and $v(0)$.
- Velocity and acceleration: $v = A\omega\cos(\omega t + \delta)$, $a = -A\omega^2\sin(\omega t + \delta) = -\omega^2 x$.
- It is the projection of uniform [[Circular Motion|circular motion]] onto a line (the shadow of a point on a circle).
- **Energy:** kinetic and elastic energy swap back and forth, but their sum stays constant: $W = \frac{1}{2}kA^2$.
- **General equation:** $\ddot{x} + 2\beta\dot{x} + \omega^2 x = f(t)$. Damping ($2\beta\dot{x}$, e.g. air resistance) takes energy away, $x(t) = e^{-\beta t}\sin(\dots)$. External driving $f(t)$ adds energy and causes [[Resonance|resonance]] when it matches the natural frequency.

## Examples

**Mass on a spring** (Physics 5): $m\ddot{x} = -kx \implies \omega = \sqrt{k/m}$.

**Physical pendulum** (Physics 6): $J\ddot{\varphi} = -r_*mg\sin\varphi$. For small angles $\sin\varphi \approx \varphi$:

$$\ddot{\varphi} + \frac{mgr_*}{J}\varphi = 0 \implies t_0 = 2\pi\sqrt{\frac{J}{mgr_*}}$$

**Mathematical pendulum** (Physics 6): $J = ml^2$, $r_* = l$, so $t_0 = 2\pi\sqrt{l/g}$. For large angles it still oscillates, but no longer harmonically.

## Connections

- [[2026-11-03 - Angular Momentum, Kepler's Laws, Precession and Oscillations - 5]] — projection of circular motion, mass on a spring, $\omega = \sqrt{k/m}$ (Physics)
- [[2026-11-10 - Physical Pendulum, Waves and Electrostatics - 6]] — physical and mathematical pendulum, damping, resonance, energy (Physics)
- [[Differential Equation]], [[Circular Motion]], [[Moment of Inertia]], [[Torque]], [[Potential Energy]], [[Resonance]], [[Wave]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), 10.1 *Sinusno nihanje*: [[Sources/physics/FRI_Fizika.pdf#page=87|p. 87]]; 10.2 *Nekaj značilnih nihal*: [[Sources/physics/FRI_Fizika.pdf#page=89|p. 89]]; 10.3 *Mehanska energija nedušenih nihal*: [[Sources/physics/FRI_Fizika.pdf#page=96|p. 96]]
