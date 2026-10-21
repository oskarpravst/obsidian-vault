---
type: "[[Lectures]]"
course: "[[Physics]]"
date: 2026-10-11
week: "1"
---

# 2026-10-11 - Physical Quantities and Kinematics

## Main Idea

Physical quantities consist of a number and a unit, and the [[SI System|SI system]] defines the units objectively. [[Kinematics]] (*kinematika*) describes motion through position, velocity and acceleration, which are linked by [[Derivative|differentiation]] and [[Integral|integration]]. The lecture covers 1D motion (uniform and uniformly accelerated), oscillation, projectile motion and uniform [[Circular Motion|circular motion]].

## Notes

### F 1.1 — Physical quantities (*fizikalne količine*)

A physical quantity = **[number] [unit]** (*[ŠT] [ENOTE]*).

The "number" can be:

- a **scalar** (*skalar*): $s$
- a **vector** (*vektor*): $\vec{v}$
- a **tensor** (*tenzorji*, e.g. matrices): $\underline{A}$

#### Units — SI system

Science uses the **SI system** as an objective system of units.

- **Time** (*čas*): defined by the atomic clock (since 1967). One second is the duration of $9\,192\,631\,770$ periods of the radiation emitted by a caesium-133 atom in the transition between the two hyperfine levels of its ground state:
  $$1\,\text{s} = 9\,192\,631\,770 \text{ periods of the } {}^{133}\text{Cs radiation}$$
- **Distance** (*razdalja*): defined through the speed of light in vacuum, $c_0$ (or $c$), unit $[\text{m/s}]$:
  $$1\,\text{m} = \text{distance light travels in vacuum in } \tfrac{1}{299\,792\,458}\,\text{s}$$
  $$c_0 = 299\,792\,458\ \text{m/s} \approx 3 \cdot 10^8\ \text{m/s}$$
- **Mass** (*masa*) — *(yap sesh)*
  - $E = m c_0^2$
  - Electron mass: $m_e \approx 9 \cdot 10^{-31}\ \text{kg}$

### Example: 1D motion (*1D gibanje*) — kinematics in 1D

One axis is enough. A block moves along the $x$ axis with velocity $\vec{v}$:

$$\vec{v} = (v_x, v_y, v_z) = (v, 0, 0)$$

so the motion is fully described by the scalar function $v(t)$. On a $v(t)$ graph, $v > 0$ means motion in the positive direction and $v < 0$ in the negative direction.

From $v(t)$ we get:

- **acceleration** (*pospešek*) $a(t)$
- **position** (*lega*) $x(t)$

**Distance travelled** (*pot*) — how much the body has moved in total.
**Position** (*lega*) — displacement from the origin of the axis.

#### Acceleration — change of velocity over time (*spreminjanje hitrosti s časom*)

$$\Delta v = a \cdot \Delta t \iff a = \frac{\Delta v}{\Delta t}$$

$$a = \frac{v(t + \Delta t) - v(t)}{\Delta t}$$

On the $v(t)$ graph, $\Delta v / \Delta t$ is the slope of a triangle with legs $\Delta t$ and $\Delta v$. As $\Delta t \to 0$, this becomes the slope of the tangent at $t$:

$$a(t) = \lim_{\Delta t \to 0} \frac{v(t + \Delta t) - v(t)}{\Delta t}$$

This is the **derivative of velocity with respect to time** (*odvod hitrosti po času*):

$$a(t) = \frac{dv}{dt} \ \text{(Leibniz)} = \dot{v} \ \text{(Newton)}$$

Similarly:

$$v(t) = \frac{dx}{dt} = \dot{x}$$

#### Derivative of $t^n$ (review)

$$y = k \cdot t^n \implies \dot{y} = k \cdot n \cdot t^{n-1}$$

e.g. $y = k \cdot t \implies \dot{y} = k \cdot 1 \cdot t^0 = k$

#### Integration

The inverse operation (*obratna transformacija*) of differentiation is **integration**:

$$a(t) = \dot{v}(t) = \frac{dv}{dt}$$

($t'$ is the integration variable, so that it is not confused with the upper bound $t$.)

$$v(t) = \underbrace{v(t_0)}_{\text{initial velocity}} + \underbrace{\int_{t_0}^{t} a(t')\,dt'}_{\text{change } \Delta v = v(t) - v(t_0)}$$

e.g. $a(t) = B t^n$:

$$\int_{t_0}^{t} a(t')\,dt' = B \cdot \frac{1}{n+1} \cdot t'^{\,n+1} \Big|_{t_0}^{t} = B\frac{t^{n+1}}{n+1} - B\frac{t_0^{n+1}}{n+1} \qquad (n \neq -1)$$

**Position:**

$$x(t) = \underbrace{x(t_0)}_{x_0} + \int_{t_0}^{t} v(t')\,dt'$$

### Kinematics in 1D: linear motion (*premo gibanje*)

#### I. Uniform linear motion (*premo enakomerno gibanje*)

$$v(t) = v_0 \implies a(t) = \dot{v} = 0$$

$$x(t) = x_0 + \int_{t_0}^{t} v_0\,dt' = x_0 + v_0 t \quad (t_0 = 0)$$

The $x(t)$ graph is a straight line through $x_0$: rising for $v_0 > 0$, falling for $v_0 < 0$.

#### II. Uniformly accelerated motion (*enakomerno pospešeno gibanje*)

$$a(t) = a_0 \implies v(t) = v_0 + \int_{t_0}^{t} a_0\,dt' = v_0 + a_0 t$$

$$x(t) = x_0 + \int_{t_0}^{t} (v_0 + a_0 t')\,dt' = x_0 + v_0 t + \frac{a_0 t^2}{2} \quad (t_0 = 0)$$

The $x(t)$ graph is a parabola starting at $x_0$: curving upward for $a_0 > 0$, downward for $a_0 < 0$.

#### Just for fun: oscillation (*za foro: nihanje*)

$$x(t) = A \cos(\omega t) \quad [\text{m}]$$

$$v(t) = \dot{x}(t) = A \cdot (-\sin(\omega t)) \cdot \omega = -A\omega \sin(\omega t) \quad [\text{m/s}]$$

$$a(t) = \dot{v}(t) = \ddot{x}(t) = (-A\omega)\cos(\omega t) \cdot \omega = -A\omega^2 \cos(\omega t) = -\omega^2 x(t)$$

$x(t)$ oscillates between $A$ and $-A$; $v(t)$ oscillates between $A\omega$ and $-A\omega$.

### Motion in space (*gibanje v prostoru*)

Compute $x$, $y$ and $z$ separately.

#### Example: projectile motion (*poševni met*)

At $t = 0$ the body is launched with velocity $\vec{v}_0$ at angle $\varphi$ to the horizontal. Its velocity components are:

**$x$ direction:**

$$v_0^x = v_0 \cos\varphi, \qquad a_x = 0$$

$$x(t) = \underbrace{x_0}_{0} + v_0^x t = v_0^x t \quad \text{(uniform linear motion)}$$

**$y$ direction:**

$$v_0^y = v_0 \sin\varphi, \qquad a_y = -g$$

$$v_y(t) = v_0^y + a_y t = v_0^y - g t$$

$$y(t) = y_0 + \int_{0}^{t} (v_0^y - g t')\,dt' = y_0 + v_0^y t - \frac{g t^2}{2}$$

### Circular motion in 2D (*kroženje*)

$$\vec{r}(t) = (x(t), y(t), 0)$$

Two directions of rotation: (+) and (−).

- $T$ … period (*obhodni čas*)
- $\omega = \dfrac{2\pi}{T} = 2\pi\nu$

#### Uniform circular motion (*enakomerno kroženje*)

$$\vec{r}(t) = (r\cos(\omega t),\ r\sin(\omega t),\ 0)$$

We choose the initial time $t_0 = 0$, so $\vec{r}(0) = (r, 0, 0)$.

$$\vec{v}(t) = (\dot{x}, \dot{y}, 0) = (-r\omega\sin(\omega t),\ r\omega\cos(\omega t),\ 0)$$

$$\vec{a}(t) = \dot{\vec{v}}(t) = -\omega^2 (r\cos(\omega t),\ r\sin(\omega t),\ 0) = -\omega^2 \vec{r}$$

**Lessons** (*lekcije*):

- $\vec{a} \parallel -\vec{r}$ (acceleration points towards the centre)
- $\vec{v} \perp \vec{r}$

#### Advantage of vectors (*prednost vektorjev*)

$$r^2 = \vec{r} \cdot \vec{r}$$

← [[Dot Product|dot product]] (*skalarni produkt*)

Differentiate with respect to time … *(unfinished in notes)*

## Questions

- [ ] What follows from differentiating $r^2 = \vec{r} \cdot \vec{r}$ with respect to time? (The derivation is unfinished in the notes.)
- [ ] The notes next to the $\Delta v / \Delta t$ triangle say "you can use the Pythagorean theorem". What was this remark referring to, since the slope itself is just the ratio $\Delta v / \Delta t$?
- [ ] 

## Connections

- Course: [[Physics]]
- Exercises: [[Sources/physics/photoNotes/vaje/vaje 1.pdf|vaje 1]]

## Sources

- Handwritten notes: [[Sources/physics/photoNotes/lectures/notes 1.pdf|notes 1]]
