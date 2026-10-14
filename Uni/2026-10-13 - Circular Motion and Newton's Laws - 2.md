---
type: "[[Lectures]]"
course: "[[Physics]]"
date: 2026-10-13
week: "2"
---

# 2026-10-13 - Circular Motion and Newton's Laws

## Main Idea

[[Circular Motion|Circular motion]] (*kroženje*) described with the angle $\varphi(t)$: velocity and acceleration follow by differentiating the position, and the acceleration splits into a **tangential** and a **radial** part. Even uniform circular motion is accelerated, because the direction of the velocity keeps changing. The [[Dot Product|scalar]] and [[Cross Product|vector product]] give a compact way to write all of this ($\vec{v} = \vec{\omega} \times \vec{r}$). Then [[Newton's Laws|Newton's laws]], their use for a system of bodies (only external forces move the [[Centre of Mass|centre of mass]]), the force of gravity and [[Friction|friction]].

## Notes

### F 2.1 — Circular motion (*kroženje*)

**Definition of circular motion** (*definicija kroženja*):

$$|\vec{r}(t)| = r = \text{const.}$$

In 2D: $x^2 + y^2 = r^2$, i.e. $x(t)^2 + y(t)^2 = r^2$.

The position is described by the angle $\varphi(t)$ from the $x$ axis ([[Physics 2 notes.pdf#page=1|sketch]]):

$$
\vec{r}(t):\quad
\begin{cases}
x(t) = r\cos\varphi(t) \\
y(t) = r\sin\varphi(t) \\
z(t) = 0 & \text{(because we are in 2D)}
\end{cases}
$$

#### ① Velocity — derivative of position with respect to time (*odvod lege po času*)

$$\vec{v}(t) = \dot{\vec{r}}(t) = (\dot{x}, \dot{y}, \dot{z})$$

$$
\vec{v}(t) = \big(r(-\sin\varphi(t))\,\dot{\varphi},\; r\cos\varphi(t)\,\dot{\varphi},\; 0\big) = r\dot{\varphi}(t)\,\big(-\sin\varphi(t),\; \cos\varphi(t),\; 0\big)
$$

#### ② Acceleration

$$\vec{a}(t) = \dot{\vec{v}}(t) = (\dot{v}_x, \dot{v}_y, \dot{v}_z)$$

$\vec{v}$ is a product of $r\dot{\varphi}(t)$ and the vector $(-\sin\varphi, \cos\varphi, 0)$, so use the product rule $(f \cdot g)' = f' \cdot g + f \cdot g'$:

$$
\begin{aligned}
\vec{a}(t) &= r\ddot{\varphi}(t)\,\big(-\sin\varphi(t),\; \cos\varphi(t),\; 0\big) \\
&\quad + r\dot{\varphi}(t)\,\big(-\cos\varphi(t)\,\dot{\varphi}(t),\; -\sin\varphi(t)\,\dot{\varphi}(t),\; 0\big) \\[4pt]
&= \underbrace{r\ddot{\varphi}(t)\,\big(-\sin\varphi(t),\; \cos\varphi(t),\; 0\big)}_{\text{same as before}} \;+\; \big(-r\,\dot{\varphi}(t)^2\big)\big(\cos\varphi(t),\; \sin\varphi(t),\; 0\big)
\end{aligned}
$$

Here $\ddot{\varphi}(t) = \alpha(t)$ and $\dot{\varphi}(t)^2 = \omega(t)^2$ (see below).

#### Angular velocity and angular acceleration

| Quantity | Definition | Unit |
|---|---|---|
| Angular velocity (*kotna hitrost*) | $\omega = \dot{\varphi}(t)$ | rad/s |
| Angular acceleration (*kotni pospešek*) | $\alpha = \dot{\omega} = \ddot{\varphi}$ | rad/s² |

#### Two special cases

| | ① Uniform circular motion (*enakomerno kroženje*) | ② Uniformly accelerated circular motion (*enakomerno pospešeno kroženje*) |
|---|---|---|
| angular acceleration | $\alpha = 0$ | $\alpha = \text{const.}$ |
| angular velocity | $\omega = \text{const.}$ | $\omega = \omega_0 + \alpha t$ |
| angle | $\varphi(t) = \varphi_0 + \omega t$ | $\varphi(t) = \varphi_0 + \omega_0 t + \dfrac{\alpha t^2}{2}$ |

#### Speed of circular motion

From ① with $\dot{\varphi} = \omega$ ([[Physics 2 notes.pdf#page=3|sketch]]: $\vec{v}$ is tangent to the circle):

$$\vec{v}(t) = r\omega\,\big(-\sin\varphi(t),\; \cos\varphi(t),\; 0\big)$$

> [!info] Scalar product (*skalarni produkt*)
> $$s = \vec{a} \cdot \vec{b} = |\vec{a}|\,|\vec{b}|\cos\vartheta = a_x b_x + a_y b_y + a_z b_z = \sum_{i=1}^{3} a_i b_i \qquad (a_1 = a_x, \dots)$$
> where $\vartheta$ is the angle between $\vec{a}$ and $\vec{b}$. The result is a **number** (scalar).
>
> - A vector with itself ($\vartheta = 0$, $\cos 0 = 1$): $|\vec{a}|^2 = \vec{a} \cdot \vec{a} = |\vec{a}|\,|\vec{a}|\cos 0$
> - Perpendicular vectors ($\vartheta = \frac{\pi}{2}$): $s = |\vec{a}|\,|\vec{b}|\underbrace{\cos\tfrac{\pi}{2}}_{0} = 0$

The size of the velocity, using $\vec{v} \cdot \vec{v}$:

$$v^2(t) = \vec{v} \cdot \vec{v} = (r\omega)^2\big(\underbrace{(-\sin\varphi)^2 + (\cos\varphi)^2}_{1} + 0\big)$$

$$|\vec{v}(t)| = v(t) = r\,\omega(t)$$

#### $\vec{v}$ is perpendicular to $\vec{r}$

With $\vec{r} = r\,(\cos\varphi(t),\; \sin\varphi(t),\; 0)$:

$$\vec{r} \cdot \vec{v} = r^2\omega\,\big(\cos\varphi\,(-\sin\varphi) + \sin\varphi\cos\varphi + 0\big) = 0$$

→ the vectors are perpendicular (*torej sta pravokotna*).

#### Tangential and radial acceleration

$$\vec{a}(t) = \vec{a}_t(t) + \vec{a}_r(t)$$

| | Tangential acceleration (*tangentni pospešek*) | Radial acceleration (*radialni pospešek*) |
|---|---|---|
| direction | $\vec{a}_t \parallel \vec{v}$ | $\vec{a}_r \parallel -\vec{r}$ (towards the centre) |
| vector | | $\vec{a}_r(t) = -\omega^2\vec{r}$ |
| size | $a_t(t) = \lvert\vec{a}_t\rvert = r\,\alpha(t)$ | $a_r(t) = \lvert\vec{a}_r(t)\rvert = \omega^2 r$ |

These are exactly the two terms of $\vec{a}(t)$ from ②: the first ($r\ddot{\varphi}$) is along $\vec{v}$, the second ($-r\dot{\varphi}^2$) points against $\vec{r}$.

**Example** (*zgled*): what are the accelerations in uniform circular motion, i.e. $\vec{a}$ for $\omega = \text{const.}$?

- $\dot{\omega} = \alpha = 0 \implies \vec{a}_t = 0$
- $a_r = \omega^2 r = \text{const.}$, but $\vec{a}_r = -\omega^2\vec{r}$ changes direction (*spreminja smer*)
- $v = |\vec{v}(t)| = \omega r = \text{const.}$, but $\vec{v}$ changes direction

> [!tip] Fun lesson (*hecna lekcija*)
> Uniform circular motion is **still accelerated motion** — $\vec{a}_r$ points towards the centre ([[Physics 2 notes.pdf#page=5|sketch]]).
> As soon as you move in a circle, the direction of the velocity changes → it is accelerated motion. (That is why on Earth we are in an accelerated frame — *zato smo na Zemlji v pospešenem sistemu*.)

### F 2.2 — Vector form of circular motion

> [!info] Vector product (*vektorski produkt*) — simplified
> $$\vec{c} = \vec{a} \times \vec{b} = -(\vec{b} \times \vec{a}), \qquad |\vec{c}| = |\vec{a}|\,|\vec{b}|\sin\theta$$
> - The result is a **vector**, perpendicular to both $\vec{a}$ and $\vec{b}$. Its direction is defined by the positive rule (*smer definirana s pozitivnim pravilom*) — see the [[Physics 2 notes.pdf#page=6|sketch]].
> - $\theta = 0 \implies |\vec{c}| = 0$: parallel vectors have no vector product (they don't define a plane — *ni ravnine*).
> - $\theta = \frac{\pi}{2} \implies |\vec{c}|_{\max} = |\vec{a}|\,|\vec{b}|$

**Clever trick** (*zvit trik*): treat $\vec{\omega}$ as a vector perpendicular to the plane of rotation — **up** for the positive direction of rotation, **down** for the negative.

$$\vec{v} = \vec{\omega} \times \vec{r}$$

$\vec{\omega}$ and $\vec{r}$ are perpendicular ($\theta = \frac{\pi}{2}$), so

$$v = |\vec{v}| = \omega r \underbrace{\sin\theta}_{1} = \omega r, \qquad \vec{v} \perp \vec{\omega}, \qquad \vec{v} \perp \vec{r}$$

Differentiating (product rule):

$$
\vec{a} = \dot{\vec{v}} = \dot{\vec{\omega}} \times \vec{r} + \vec{\omega} \times \dot{\vec{r}} = \underbrace{\vec{\alpha} \times \vec{r}}_{\vec{a}_t} + \underbrace{\vec{\omega} \times \vec{v}}_{\vec{a}_r}
$$

### F 2.3 — [[Newton's Laws]] (*Newtonovi zakoni*, 1687)

A force is an external influence (*zunanji vpliv*) that causes a change of motion or a deformation.

1. **First law:** if the sum of forces on a body is zero, the body is at rest or moves in a straight line at constant velocity (*miruje ali se giblje premo enakomerno*).
2. **Second law:** $\vec{F} = m\vec{a}$ — valid in an **inertial frame** (*inercialni sistem* — the condition for the laws to hold).
   - Mass = **inertia** (*inercija*): resistance to changes (*nasprotovanje spremembam*).
   - $\vec{F} = m\dot{\vec{v}}$
   - $\vec{F} = m\ddot{\vec{r}}$ → you are looking for the position as a function of time, $\vec{r}(t)$.
   - $\vec{F} = 0 \implies \vec{a} = 0 \implies \vec{v} = \text{const.}$ (uniform linear motion)
3. **Third law — action and reaction** (*akcija – reakcija*):
   $$\vec{F}_{2\to1} = -\vec{F}_{1\to2}$$

**Tricks** (*triki*): in Newton's picture the influence is **instantaneous** (*vpliv je takojšen*) — but what about between the Earth and the Sun? In reality there is a response time of the system (*obstaja odzivni čas sistema*).

### F 2.4 — Types of bodies (*tipi teles*)

1. **Point body** (*točkasto telo*)
2. **System of several bodies** (*sistem več teles*)

The basic building block of matter is the **atom** — approximately a point body with $m_1 \neq 0$. A body made of $N$ atoms is a **system of $N$ bodies**.

#### Newton's laws for $N = 2$ atoms (both with mass $m_1$)

Each atom feels an **external force** (*zunanja sila*) $\vec{F}_{z1}$, $\vec{F}_{z2}$ and an **internal force** (*notranja sila* — inside the system) from the other atom, $\vec{F}_{2\to1}$, $\vec{F}_{1\to2}$ ([[Physics 2 notes.pdf#page=8|sketch]]).

- **2nd law** for each body:
  $$
  \begin{aligned}
  \text{body 1:}\quad \vec{F}_1 &= \vec{F}_{z1} + \vec{F}_{2\to1} = m_1\vec{a}_1 \\
  \text{body 2:}\quad \vec{F}_2 &= \vec{F}_{z2} + \vec{F}_{1\to2} = m_1\vec{a}_2
  \end{aligned}
  $$
- **3rd law:** $\vec{F}_{2\to1} = -\vec{F}_{1\to2}$

Adding the two equations:

$$\vec{F}_{z1} + \cancel{\vec{F}_{2\to1}} + \vec{F}_{z2} + \cancel{\vec{F}_{1\to2}} = m_1\vec{a}_1 + m_1\vec{a}_2$$

(the internal forces cancel out — *notranji sili se odštejeta*)

$$
\underbrace{\vec{F}_{z1} + \vec{F}_{z2}}_{\vec{F}_z} = \underbrace{2m_1}_{\text{mass of the system}} \cdot \underbrace{\frac{\vec{a}_1 + \vec{a}_2}{2}}_{\text{acceleration of the system}}
$$

$$\vec{F}_z = m_{\text{system}} \cdot \vec{a}_{\text{system}}$$

**Example** (*npr.*): $\vec{a}_1 = \vec{a}_2$ — two atoms at a fixed distance $R$ (*R = fiksna*), moving without rotation $\implies \vec{a}_2 = \vec{a}_1$. The system $S$ has $m_{\text{system}} = 2m_1$, and its acceleration is determined by $\vec{F}_z = \vec{F}_{z1} + \vec{F}_{z2}$.

#### $N = 3$

Each body feels its external force and the internal forces of the other two ([[Physics 2 notes.pdf#page=9|sketch]]).

**Punchline:** the sum of internal forces is always 0 (because of Newton's 3rd law) (*vsota notranjih sil je vedno 0, zaradi 3. N. z.*).

$$\underbrace{\vec{F}_{z1} + \vec{F}_{z2} + \vec{F}_{z3}}_{\vec{F}_z} = m_1\vec{a}_1 + m_2\vec{a}_2 + m_3\vec{a}_3$$

With $m_s = m_1 + m_2 + m_3$:

$$\vec{a}_* = \frac{m_1\vec{a}_1 + m_2\vec{a}_2 + m_3\vec{a}_3}{m_s}$$

For a rigid body (*togo telo*) that moves without rotating (translation): $\vec{a}_1 = \vec{a}_2 = \vec{a}_3$, e.g. $\vec{a}_3 = \vec{a}_1$. If the body rotates, the accelerations differ (each point has its own $a_r = \omega^2 r$).

#### [[Centre of Mass|Centre of mass]] (*masno središče*)

The position of the centre of mass is the mass-weighted average of the position vectors ([[Physics 2 notes.pdf#page=10|sketch]]); differentiating gives its velocity and acceleration:

$$
\vec{r}_* = \frac{m_1\vec{r}_1 + m_2\vec{r}_2 + m_3\vec{r}_3}{m_s}
\;\implies\;
\vec{v}_* = \dot{\vec{r}}_* = \frac{m_1\vec{v}_1 + m_2\vec{v}_2 + m_3\vec{v}_3}{m_s}
\;\implies\;
\vec{a}_* = \ddot{\vec{r}}_* = \frac{m_1\vec{a}_1 + m_2\vec{a}_2 + m_3\vec{a}_3}{m_s}
$$

$$\vec{F}_z = m_s\,\vec{a}_*$$

($\vec{a}_*$ = acceleration of the centre of mass — *masnega središča, težišče*; English: *centre of mass*.)

#### System of $N$ bodies (*sistem $N$ teles*)

| | |
|---|---|
| total mass | $m_s = \sum_{i=1}^{N} m_i$ |
| position of the centre of mass | $\vec{r}_* = \dfrac{\sum_{i=1}^{N} m_i\vec{r}_i}{m_s}$ |
| velocity of the centre of mass | $\vec{v}_* = \dfrac{\sum_{i=1}^{N} m_i\vec{v}_i}{m_s}$ |
| acceleration of the centre of mass | $\vec{a}_* = \dfrac{\sum_{i=1}^{N} m_i\vec{a}_i}{m_s}$ |
| total external force | $\vec{F}_z = \sum_{i=1}^{N} \vec{F}_{zi}$ |

$$\boxed{\vec{F}_z = m_s\,\vec{a}_*}$$

### F 2.5 — Force of gravity (*sila teže* — the gravitational force on Earth)

$$\vec{F}_g = m\vec{g}, \qquad g \approx 9{,}8\ \text{m/s}^2, \qquad [\text{N} = \text{kg}\,\text{m/s}^2] \text{ — newton}$$

**System of bodies:**

$$\vec{F}_z = \sum_{i=1}^{N} \vec{F}_{gi} = \sum_{i=1}^{N} m_i\vec{g} = m_s\vec{g}$$

**Free fall** (*prosti pad*) — only gravity acts:

$$\vec{F}_z = m_s\vec{a}_* \implies \cancel{m_s}\,\vec{g} = \cancel{m_s}\,\vec{a}_* \implies \vec{a}_* = \vec{g}$$

The total force of gravity is placed in the centre of mass (*damo v masno središče*) ([[Physics 2 notes.pdf#page=11|sketch]]).

**Two kinds of mass:**

- $\vec{F}_g = m_g\vec{g}$ — $m_g$ is the **gravitational mass** (*gravitacijska masa*)
- $\vec{F} = m\vec{a}$ — $m$ is the **inertial mass** (*inercialna masa*)
- $m_g = m_a$?

### F 2.6 — [[Friction]] (*trenje*)

Friction comes from the roughness of the surfaces (*nazobčenost površine*).

**Static friction → kinetic friction** (*lepenje → trenje*):

| | Static friction (*lepenje*) | Kinetic friction (*trenje*) |
|---|---|---|
| when | the body is at rest, $\vec{v} = 0$ | once the body moves, $\vec{v} \neq 0$ |
| force | $\vec{F}_l$ — force of static friction (*sila lepenja*), direction $-\vec{F}_z$ | $\vec{F}_{tr}$ |
| size | $F_l^{\max} = k_l \cdot F_p$ | $F_{tr} = k_{tr} \cdot F_p$ |

- $k_l$ … coefficient of static friction (*koeficient lepenja*)
- $k_{tr}$ … coefficient of kinetic friction
- $F_p$ … force of the surface (*sila podlage*)
- $k_{tr} < k_l$

**Steel on steel** (*jeklo na jeklo*): what would happen if the surfaces were made perfectly smooth? (welding process — *proces varjenja*)

## Questions

- [ ] Is the gravitational mass equal to the inertial mass ($m_g = m_a$)?
- [ ] Newton's influence is instantaneous — what about between the Earth and the Sun?
- [ ] What would happen if two steel surfaces were made perfectly smooth? (welding process)

## Connections

- Course: [[Physics]]
- Exercises: [[Sources/physics/photoNotes/vaje/vaje 2.pdf|vaje 2]]
- Previous lecture: [[2026-10-11 - Physical Quantities and Kinematics - 1]] — uniform circular motion, $\vec{a} = -\omega^2\vec{r}$
- [[Derivative]] — product rule

## Sources

- Handwritten notes: [[Sources/physics/photoNotes/lectures/notes 2.pdf|notes 2]]
- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), sections 3.1, 5.8–5.10, 6.1–6.2, 9.1–9.2
