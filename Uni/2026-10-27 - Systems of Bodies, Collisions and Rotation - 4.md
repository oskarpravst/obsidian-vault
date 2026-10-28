---
type: "[[Lectures]]"
course: "[[Physics]]"
date: 2026-10-27
week: "4"
---

# 2026-10-27 - Systems of Bodies, Collisions and Rotation

## Main Idea

The theorem of conservation of [[Momentum|momentum]] from the last lecture is extended to a **system of bodies** (*sistem teles*): only external forces change the total momentum, which moves like a single body of mass $m$ at the [[Centre of Mass|centre of mass]]. If the [[Impulse|impulse]] of the external forces is zero, the total momentum is conserved. This is used for Newton's cradle, the [[Inelastic Collision|inelastic]] and [[Elastic Collision|elastic collision]] of two carts, and the [[Rocket Equation|rocket engine]]. The motion of a system splits into the motion of the centre of mass and the rotation around it. To describe rotation we take the [[Cross Product|cross product]] of Newton's 2nd law with $\vec{r}$, which gives the [[Torque|torque]] (*navor*) and the [[Moment of Inertia|moment of inertia]] (*vztrajnostni moment*): $\vec{M}_z = J\,\vec{\alpha}$. The lecture ends with the kinetic energy of a rigid body and [[Rolling|rolling]].

## Notes

### Momentum of a system of bodies (*gibalna količina sistema teles*)

$$\int_{t_z}^{t_k} \vec{F}\,dt = \Delta\vec{G}$$

→ for a **system of bodies** (*sistem teles*) Newton's 2nd law holds for the whole system, with the acceleration $\vec{a}^*$ of the centre of mass:

$$\vec{F}_z = m \cdot \vec{a}^* \quad\longrightarrow\quad \int_{t_z}^{t_k} \vec{F}_z\,dt = \Delta\vec{G}^s = \vec{G}_k^s - \vec{G}_z^s$$

Example (*zgled*): Newton's cradle (*Newtonova gugalnica*).

![[Physics 4 system of bodies.svg]]

For $N = 3$ bodies:

$$\vec{G}^s = m \cdot \vec{v}^* = \sum_{i=1}^{N} m_i \vec{v}_i, \qquad \vec{G}^s = \sum_{i=1}^{3} \vec{G}_i$$

$$\vec{v}^* = \frac{\sum_{i=1}^{N} m_i \vec{v}_i}{m}, \qquad m = \sum_{i=1}^{N} m_i$$

$\vec{v}^*$ … velocity of the centre of mass, $\vec{r}^*$ … its position.

→ Case (*primer*): $\int_{t_z}^{t_k} \vec{F}_z\,dt = 0$ (a bomb — *bomba*).

### Conservation of momentum (*ohranitev gibalne količine*)

Examples (*zgledi*):

$$0 = \Delta\vec{G}^s \;\implies\; \sum_{i=1}^{N} m_i \vec{v}_i^{\,z} = \sum_{i=1}^{N} m_i \vec{v}_i^{\,k}$$

The momentum at the beginning equals the momentum at the end (*gib. kol. na začetku = na koncu*).

**Newton's cradle** (*Newtonova gugalnica*):

$$\vec{v}_1^{\,z} \neq 0 \implies \vec{v}_N^{\,k} \neq 0$$

$$m_1 \vec{v}_1^{\,z} = m_N \vec{v}_N^{\,k}$$

It does not matter what happens in between (*ni važno, kaj se dogaja vmes*).

**Air track** (*zračna klop / drča*) — we neglect friction (*zanemarimo trenje*). Collision of two carts (*trk dveh vozičkov*).

### ① Inelastic collision (*neelastičen / neprožni trk*)

Both carts stick together (*oba vozička se sprimeta*).

![[Physics 4 inelastic collision.svg]]

**Case 1** (*primer 1*), along $x$: $v_1^z = v_z$, $v_2^z = 0$:

$$m_1 v_1^z + m_2 v_2^z = (m_1 + m_2)\,v_k$$

$$v_k = \frac{m_1}{m_1 + m_2}\,v_z$$

Special cases (*poseben primer*):

- $m_1 = m_2$:
  $$v_k = \frac{1}{2}\,v_z = \frac{v_z}{2}$$
- $m_1 \gg m_2$ ($m_2 = m$, $m_1 = M$):
  $$v_k = \frac{M}{M + m}\,v_z = \frac{1}{1 + \frac{m}{M}}\,v_z, \qquad \frac{m}{M} \sim 10^{-6}$$
  $$v_k \simeq v_z$$
- $m_1 \ll m_2$ ($m_1 = m$, $m_2 = M$):
  $$v_k = \frac{m}{M + m}\,v_z = \frac{\frac{m}{M}}{1 + \frac{m}{M}}\,v_z$$
  where we neglect (*zanemarimo*) the $\frac{m}{M}$ in the denominator:
  $$v_k \simeq \frac{m}{M}\,v_z \simeq 0 \quad \text{(goes towards 0 — *proti 0 gre*)}$$

### ② Elastic collision (*elastični / prožni trk*)

![[Physics 4 elastic collision.svg]]

**Conservation of momentum** (*ohranitev G.K.*), along $x$:

$$m_1 v_1^z + m_2 v_2^z = m_1 \underline{v_1^k} + m_2 \underline{v_2^k}$$

→ Case: $v_1^z$, $v_2^z$ are known (*poznamo*). The equation has 2 unknowns (*enačba ima 2 neznanki*) — 1 equation is not enough (*1 enačba, torej ni dovolj*). Here we use the theorem of conservation of energy (*tukaj uporabimo izrek o ohranitvi energije*).

**Conservation of energy** (*ohranitev energije*):

$$A_z = 0 \implies \Delta W_k^s = 0 \implies W_k^z = W_k^k$$

$$\frac{1}{2} m_1 v_{1z}^2 + \frac{1}{2} m_2 v_{2z}^2 = \frac{1}{2} m_1 v_{1k}^2 + \frac{1}{2} m_2 v_{2k}^2$$

(a system of 2 equations with 2 unknowns — *sistem 2 enačb z 2 neznankama*). When the smoke clears we get (*ko se dim razkadi, dobimo*):

$$v_{1k} = \frac{m_1 - m_2}{m_1 + m_2}\,v_{1z} + \frac{2 m_2\,v_{2z}}{m_1 + m_2}$$

$$v_{2k} = \frac{m_2 - m_1}{m_1 + m_2}\,v_{2z} + \frac{2 m_1\,v_{1z}}{m_1 + m_2}$$

These are the equations for an elastic collision (*to so enačbe za elastični trk*).

**Case 1** (*primer 1*): $m_1 = m_2 = m$

$$v_{1k} = 0 + 1 \cdot v_{2z}$$

$$v_{1k} = v_{2z}, \qquad v_{2k} = v_{1z}$$

The carts exchange velocities (*vozička zamenjata hitrosti*).

**Case 2** (*primer 2*): $m_1 \ll m_2$, written with $m_1 = m$, $m_2 = M$:

$$v_{1k} = \frac{m - M}{m + M}\,v_{1z} + \frac{2M}{m + M}\,v_{2z}$$

$$v_{1k} \simeq \frac{-M}{M}\,v_{1z} + \frac{2M}{M}\,v_{2z}$$

$$v_{1k} \simeq -v_{1z} + 2 v_{2z}$$

→ Example (*zgled*): $v_{2z} = 0$, $v_{1z} = v_z$

![[Physics 4 ball bounce.svg]]

$$v_{1k} = -v_{1z} \implies \text{bounces back (*odboj nazaj*)}, \qquad v_{2k} \simeq 0$$

$$v_{2k} \simeq v_{2z} + \underbrace{\frac{2m}{M}\,v_{1z}}_{\approx\,0}$$

A good trick (*dober trik*) — **Galileo's cannon** (*Galilejev top*). The same is used in space (*isto se uporablja v vesolju*).

### Rocket engine (*raketni motor*)

![[Physics 4 rocket.svg]]

In time $\Delta t$ the rocket of mass $m(t) + \Delta m$ ejects gas of mass $\Delta m$. Along $x$:

$$(m(t) + \Delta m)\,v_z = m(t)\,v_k - \Delta m\,v_{plin}$$

$$m(t)\,\Delta v = \underbrace{(v_{plin} + v_z)}_{\text{relative velocity of the gas}}\,\Delta m$$

- $\Delta v$ … change of the rocket's velocity (*sprememba hitrosti rakete*)
- $v_{plin} + v_z$ … relative velocity of the gas with respect to the rocket (*relativna hitrost plina glede na raketo*)

$$m(t)\,\Delta v = v_{rel} \cdot \Delta m \quad / : \Delta t$$

$$m(t)\,a = v_{rel} \cdot \frac{\Delta m}{\Delta t} = v_{rel} \cdot \Phi_m \qquad [\text{kg/s}]$$

$\Phi_m = \dfrac{\Delta m}{\Delta t}$ … **mass flow rate** (*masni tok*) — the amount of gas ejected per second (*količina plina, ki ga zbruha na sekundo*).

$$\boxed{m(t)\,a = v_{rel} \cdot \Phi_m}$$

$v_{rel}$ and $\Phi_m$ are a matter of the engine (*stvar motorja*). The mass of the rocket decreases:

$$m(t) = m_{zač} - \Phi_m\,\Delta t \qquad \text{or in general} \qquad m(t) = m_{zač} - \int_{t_z}^{t_k} \Phi_m(t)\,dt$$

### Theorem on the motion of a system of bodies (*izrek o gibanju sistema teles*)

The motion of a system can be split into 2 parts (*gibanje sistema lahko razdelimo na 2 dela*):

1. **motion of the centre of mass** (*gibanje masnega središča*): $\vec{F}_z = m\,\vec{a}^*$ — the point of application of the forces is at the centre of mass (*prijemališče sil je v masnem središču*)
2. **motion around the centre of mass** (*gibanje okrog masnega središča*) — circular motion / rotation (*kroženje / vrtenje*)

![[Physics 4 rotation about centre of mass.svg]]

**Example: a system with a force couple** (*zgled: sistem z dvojico sil*) — a "pathological" case (*patološki primer*), $N = 2$:

![[Physics 4 force couple.svg]]

$$m_1 = m_2 = m, \qquad \vec{F}_{1z} = -\vec{F}_{2z} = \vec{F}_z$$

At the beginning the system is at rest (*na začetku miruje*). Newton's 2nd law:

$$\left.\begin{aligned} \vec{F}_{1z} &= m_1 \vec{a}_1 \\ \vec{F}_{2z} &= m_2 \vec{a}_2 \end{aligned}\right\} + \quad \vec{F}_z = 0 \;\implies\; m\,\vec{a}^* = 0 \;\implies\; \vec{r}^* = 0$$

The centre of mass does not move, so this **does not describe the rotation** (*to ne opiše vrtenja*).

### Torque (*navor*)

How do we describe rotation? (Implementation of Newton's 2nd law — *implementacija N.Z.*) We have to multiply vectorially (*vektorsko moramo množiti*) by $\vec{r}$, the position vector of the point of application of the force (*krajevni vektor prijemališča sile*), measured from the axis (*os*):

$$\vec{r} \times \vec{F}_z = \vec{r} \times m\,\vec{a}$$

**[[Torque]]** (*navor*):

$$\vec{M}_z = \vec{r} \times \vec{F}_z \qquad [\text{N}\,\text{m} \neq \text{J}]$$

![[Physics 4 torque.svg]]

$$M = |\vec{r} \times \vec{F}| = r\,F \sin\theta$$

- $M = 0$ when $\theta = 0$: $\vec{F}$ parallel to $\vec{r}$ would only pull the body (*samo vlekli bi ga*).
- $F_\perp = F \sin\theta$, $r_\perp = r \sin\theta$
- We look for $F_\perp$, the component that rotates the system (*iščemo $F_\perp$, ki sistem vrti*).

#### Force couple (*dvojica sil*)

$$\vec{M}_1 = \vec{r}_1 \times \vec{F}_1, \qquad \vec{M}_2 = \vec{r}_2 \times \vec{F}_2$$

$$\vec{F}_1 = -\vec{F}_2 = -\vec{F}, \qquad \vec{r}_2 = -\vec{r}_1 = \vec{r}$$

$$\vec{M}_1 = (-\vec{r}) \times (-\vec{F}) = \vec{r} \times \vec{F}, \qquad \vec{M}_2 = \vec{r} \times \vec{F}$$

$$\vec{M}_s = \vec{M}_1 + \vec{M}_2 = 2\,(\vec{r} \times \vec{F})$$

#### Right-hand side: $\vec{r} \times m\vec{a}$

Since we are talking about circular motion (*ker govorimo o kroženju*), the acceleration is the angular acceleration times the radius (*kotni pospešek × radij*):

$$\vec{a} = \vec{a}_t = \vec{\alpha} \times \vec{r}$$

When the smoke clears (*ko se dim razkadi*):

$$\vec{r} \times m\,(\vec{\alpha} \times \vec{r}) = m r^2\,\vec{\alpha}$$

$$\vec{M} = \vec{r} \times \vec{F}_z = m r^2\,\vec{\alpha}$$

![[Physics 4 point mass rotation.svg]]

The same problem as for linear motion (*isti problem kot pri premem gibanju*) — for a **point body** (*točkasto telo*).

### System of N bodies — moment of inertia (*sistem N teles — vztrajnostni moment*)
	
A rigid body (*togo telo*) is made of atoms (*atomi*). For each atom:

$$\vec{M}_{iz} = m_i r_i^2\,\vec{\alpha}$$

where $r_i$ is the distance from the axis of rotation (*razdalja od osi kroženja*).

![[Physics 4 rigid body atoms.svg]]

For $N$ atoms (*N atomov*):

$$\underbrace{\sum_{i=1}^{N} \vec{M}_{iz}}_{\vec{M}_z} = \underbrace{\left(\sum_{i=1}^{N} m_i r_i^2\right)}_{J}\vec{\alpha}$$

$\vec{\alpha}$ is the same for all atoms, because they rotate with the same angular velocity (*ker se vrti z enako kotno hitrostjo*).

$J$ … **[[Moment of Inertia|moment of inertia]]** (*vztrajnostni moment*):

$$J = \sum_{i=1}^{N} m_i r_i^2 \qquad\longrightarrow\qquad J = \int_{V} r^2\,dm, \qquad \rho\,dV = dm \qquad [\text{kg}\,\text{m}^2]$$

![[Physics 4 mass element.svg]]

**Example: moment of inertia about the body's own axis** (*vztrajnostni moment okrog lastne osi — skozi m.s.*):

![[Physics 4 moments of inertia.svg]]

| body | $J$ |
|---|---|
| sphere (*sfera*) | $J = \frac{2}{5}\,mR^2$ |
| cylinder (*valj*) | $J = \frac{1}{2}\,mR^2$ |
| cylindrical shell / ring (*plašč valja / obroč*) | $J = mR^2$ (as if it were a point mass — *kot bi bilo točkasto*) |

### Newton's 2nd law for a rigid body (*II. N.Z. za togo telo*)

$$\vec{M}_z = J \cdot \vec{\alpha}$$

Kinetic energy:

$$W_k = \underbrace{\frac{1}{2}\,m\,v^{*2}}_{\text{motion of the centre of mass}} + \frac{1}{2}\,J\,\omega^2$$

$\omega$ … angular velocity (*kotna hitrost*).

[[Work]]:

$$A = \int_{\vec{r}_z}^{\vec{r}_k} \vec{F}_z \cdot d\vec{s} + \int \vec{M}_z \cdot d\vec{\varphi}$$

### Rolling (*kotaljenje*)

$$v^* = \omega \cdot r$$

![[Physics 4 rolling.svg]]

$$2\pi = \omega\,t_0 \quad / \cdot r$$

$$2\pi r = v\,t_0$$

## Questions

- [ ] 

## Connections

- Course: [[Physics]]
- Previous lecture: [[2026-10-20 - Forces, Work, Energy and Momentum - 3]] — momentum and impulse ($\int \vec{F}_z\,dt = \Delta\vec{G}$), work and kinetic energy
- [[2026-10-13 - Circular Motion and Newton's Laws - 2]] — circular motion ($\omega$, $\alpha$, $a_t$)
- [[Cross Product]] — torque $\vec{M} = \vec{r} \times \vec{F}$
- [[Integral]] — moment of inertia $J = \int r^2\,dm$, mass of the rocket
- [[Momentum]], [[Impulse]], [[Work]]
- Exercises: [[Sources/physics/photoNotes/vaje/vaje 4.pdf|vaje 4]] — minimum force on an incline with friction (task 3.2), maximum speed in a curve (3.3), work, power and energy, loop-the-loop with a braking force and a rolling ball (4.1), rotational kinetic energy, conservation of momentum

## Sources

- Handwritten notes: [[Sources/physics/photoNotes/lectures/lecture 4.pdf|lecture 4]]
- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), sections 8.1–8.2 (impulse, collisions), 9.1 (centre of mass), 9.3 (torque), 9.4 (moment of inertia, Table 9.1, rolling), 9.5 (force couple)
