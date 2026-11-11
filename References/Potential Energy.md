---
type: "[[Concepts]]"
status: developed
aliases:
  - Potencialna energija
---

# Potential Energy

## Definition

**Potential energy** (*potencialna energija*) replaces the [[Work|work]] of a [[Conservative Force|conservative force]]:

$$\Delta W_p = -A_{sile}$$

It depends only on the position of the body, so the work of the force between two positions is the difference of potential energies.

## Explanation

- It exists only for conservative forces, because only their work is independent of the path.
- Only **differences** matter. We pick where it is zero: on the ground for gravity near the Earth, at $\infty$ for gravitation and the electric force.
- Once a force is moved into $W_p$, it is left out of the external work:

$$A_{zun} = \Delta W_k + \Delta W_p + \Delta W_{pr}$$

- Sign for two bodies: $W_p > 0$ means the force is repulsive, $W_p < 0$ means it is attractive.

## Examples

| force | potential energy | lecture |
|---|---|---|
| gravity near the Earth | $W_p = mgh$ | Physics 3 |
| spring | $W_{pr} = \frac{1}{2}kx^2$ (elastic energy, *prožnostna*) | Physics 3 |
| gravitation | $W_g = -G\frac{m_1 m_2}{r}$ | Physics 6 |
| electric force between point charges | $W_{ep} = \frac{e_1 e_2}{4\pi\varepsilon_0 r}$ | Physics 6 |

**Electric potential energy** (Physics 6): pin $e_1$ and move $e_2$ from $r_1$ to $r_2$:

$$\Delta W_{ep} = -\int_{r_1}^{r_2} \frac{e_1 e_2}{4\pi\varepsilon_0 r^2}\,dr = \frac{e_1 e_2}{4\pi\varepsilon_0 r_2} - \frac{e_1 e_2}{4\pi\varepsilon_0 r_1}$$

Divided by the test charge $e_2$ it gives the potential $V$, and the difference of potentials is the [[Voltage|voltage]].

**Oscillator** (Physics 6): kinetic and elastic energy of a spring pendulum add up to the constant $\frac{1}{2}kA^2$.

## Connections

- [[2026-10-20 - Forces, Work, Energy and Momentum - 3]] — $\Delta W_p = -A$, $mgh$, elastic energy, the energy theorem (Physics)
- [[2026-11-10 - Physical Pendulum, Waves and Electrostatics - 6]] — energy of the spring pendulum, electric potential energy, potential and voltage (Physics)
- [[Work]], [[Conservative Force]], [[Kinetic Energy]], [[Newton's Law of Universal Gravitation]], [[Coulomb's Law]], [[Voltage]], [[Integral]]

## Sources

- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), 7.2 *Kinetična energija in težnostna potencialna energija*: [[Sources/physics/FRI_Fizika.pdf#page=54|p. 54]]; 7.4 *Gravitacijska sila in energija*: [[Sources/physics/FRI_Fizika.pdf#page=58|p. 58]]; 11.3 *Električna potencialna energija*: [[Sources/physics/FRI_Fizika.pdf#page=106|p. 106]]
