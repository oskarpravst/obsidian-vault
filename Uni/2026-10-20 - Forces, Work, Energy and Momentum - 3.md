---
type: "[[Lectures]]"
course: "[[Physics]]"
date: 2026-10-20
week: "3"
---

# 2026-10-20 - Forces, Work, Energy and Momentum

## Main Idea

Forces are either **dissipative** (they oppose motion: [[Friction|friction]], static friction, air resistance) or **[[Conservative Force|conservative]]** (gravity, the spring force). The lecture covers the spring force and [[Newton's Law of Universal Gravitation|Newton's law of gravitation]], and then uses them for the forces in [[Circular Motion|circular motion]] ([[Centripetal Force|centripetal force]], satellites). Multiplying [[Newton's Laws|Newton's 2nd law]] by a small displacement $d\vec{s}$ and integrating gives [[Work|work]] and [[Kinetic Energy|kinetic energy]]. The work of conservative forces is replaced by [[Potential Energy|potential energy]]. Integrating the 2nd law over time instead gives [[Momentum|momentum]] and [[Impulse|impulse]].

## Notes

### Dissipative and conservative forces

**Dissipative forces** (*disipativne sile*) "oppose" motion (*"nasprotujejo" gibanju*):

1. [[Friction]] (*trenje*): $\vec{v} \neq 0$
2. Static friction (*lepenje*): $\vec{v} = 0$
3. Air resistance (*zračni upor*)

**Conservative forces** (*konzervativne sile*):

1. Gravitation / force of gravity (*gravitacija / sila teže*)
2. Elastic forces / spring force (*elastične sile / sila vzmeti*)

### ② Spring force (*sila vzmeti*)

- cause (*vzrok*): an external force (*zunanja sila*)
- effect (*posledica*): deformation / extension of the spring (*deformacija / raztezek vzmeti*)

![[Physics 3 spring.svg]]

$$x:\quad F_z = k \cdot \Delta x \qquad [k] = \text{N/m}$$

$k$ … spring constant (*koeficient vzmeti / raztezni koeficient*)

**Action of the spring on its surroundings** (*delovanje vzmeti na okolico*, Newton's 3rd law):

$$\vec{F}_v = -\vec{F}_z$$

$$\vec{F}_v = -k\,\Delta\vec{x}$$

$\Delta\vec{x}$ points in the direction of the extension (*smer raztezka*):

- $\Delta x < 0 \implies$ compression (*skrček*)
- $\Delta x > 0 \implies$ extension (*raztezek*)

### ① Gravitation (*gravitacija*)

![[Physics 3 gravitation two bodies.svg]]

$$F_g = G\,\frac{m_1 \cdot m_2}{r^2}, \qquad |\vec{F}_{g\,1\to2}| = |\vec{F}_{g\,2\to1}|$$

- The force is **attractive** (*privlačna sila*) and acts along the line between the bodies (*deluje na zveznici med telesi*) — between their centres of mass (*med težišči*).
- $G$ … gravitational constant (*gravitacijska konstanta*):
  $$G \simeq 6{,}67 \cdot 10^{-11}\ \left[\frac{\text{N}\,\text{m}^2}{\text{kg}^2}\right]$$

Does gravity act on antiparticles repulsively or attractively (*Ali gravitacija na antidelce deluje odbojno ali privlačno?*)? **Attractively** (*privlačno*).

#### Force of gravity on Earth (*sila teže — Zemlja*)

![[Physics 3 Earth gravity.svg]]

The gravitational force on a person (*sila gravitacije na človeka*) on the surface:

$$F_g = G\,\frac{M_Z \cdot m_č}{R_Z^2} = g \cdot m_č$$

$$\implies F_g(r > R_Z) = m_č \cdot g \cdot \frac{R_Z^2}{r^2}$$

**Cavendish** — torsion balance (*torzijska tehtnica*), the experiment that measured $G$.

#### Digging into the Earth (*kopanje v Zemljo*)

What happens to the force of gravity when we start digging into the Earth? All the forces from the mass above you cancel out (*vse sile nad tabo se odštejejo*).

![[Physics 3 spherical shell.svg]]

In a thin spherical shell (*sferična lupina*, $\Delta r \ll r$) the forces of all the pieces $\Delta m$ on a body inside add up to $\sum \vec{F}_g = 0$.

- We only have to take into account the mass under our feet (*moramo upoštevati samo maso pod našimi nogami*).
- In the middle of the Earth you would be weightless (*v breztežnosti*).
- → [[Shell Theorem|shell theorem]]

#### Beyond Newton

- **[[Gravitational Lensing|Gravitational lens]]**: one galaxy in front of another (*1. galaksija pred drugo*) — it acts as if there were a lens (*kot bi delovala leča*).
- Mercury's orbit does not (slightly) agree with Newton's equations (*Merkurjeva orbita se ne ujema z Newtonovimi enačbami — blago*).
- What changed the path of the light from behind? Light has no mass (*svetloba nima mase*), but bodies with mass curve space (*ukrivljajo prostor*) — all 4 dimensions (*vse 4 dimenzije*).
- → general theory of gravitation (*splošna teorija gravitacije*), see [[General Relativity]]

### Forces in circular motion (*sile pri kroženju*)

**Uniform circular motion** (*enakomerno kroženje*): $\alpha = 0$, $\omega = \text{const.}$

![[Physics 3 circular motion forces.svg]]

Sizes (*velikosti*):

$$v = \omega \cdot r, \qquad a_r = \omega^2 r = \frac{v^2}{r}$$

$$\vec{F}_c = m \cdot \vec{a}_r$$

→ the condition for circular motion (*pogoj za kroženje*).

- $\vec{F}_c$ … [[Centripetal Force|centripetal force]] (*centripetalna sila*), pointing towards the centre (*proti središču*).
- The sum of all external forces on the body must be $F_c = m \cdot a_r$ (*vsota vseh zunanjih sil na telo mora biti $F_c = m \cdot a_r$*).

**Example: motion of satellites** (*zgled: gibanje satelitov*)

![[Physics 3 satellite.svg]]

$$\vec{F}_g = \vec{F}_c, \qquad \omega = \frac{2\pi}{t_0}$$

Direction ✓ (both point towards the centre), and for the size:

$$F_g = F_c \implies G\,\frac{\cancel{m}\,M_Z}{r^2} = \cancel{m}\,\omega^2 r$$

For this circular motion the mass of the satellite does not matter, only the distance and the angular velocity (*ni pomembna masa, ampak razdalja in kotna hitrost*).

**Geostationary satellite** (*geostacionarni satelit*): always above your head (*vedno nad glavo*) — the same $\omega$ as the Earth (*enako $\omega$ kot Zemlja*).

### Theorem of conservation of kinetic and potential energy (*izrek o ohranitvi kinetične in potencialne energije*)

![[Physics 3 work path.svg]]

Take a small time interval $dt$ — short enough that $\vec{F}_z$ and $\vec{v}$ do not change (*dovolj kratek, da je $\vec{F}_z$, $\vec{v}$ nespremenjen*). The **differential displacement** (*diferencialni premik*) is

$$d\vec{s} = \vec{v} \cdot dt$$

Newton's 2nd law, multiplied by $d\vec{s}$ ([[Dot Product|scalar product]] — *skalarni produkt*):

$$\vec{F}_z = m\vec{a} \quad / \cdot d\vec{s}$$

$$\vec{F}_z \cdot d\vec{s} = m\vec{a} \cdot d\vec{s}$$

$$\vec{F}_z \cdot d\vec{s} = m(\vec{a} \cdot \vec{v})\,dt$$

Add up the whole path (*seštejemo celotno pot* — definition of the [[Integral|integral]]):

$$\underbrace{\int_{\vec{r}_z}^{\vec{r}_k} \vec{F}_z \cdot d\vec{s}}_{A} = m\int_{t_z}^{t_k} (\vec{a} \cdot \vec{v})\,dt$$

$A$ … **[[Work|work]]** (*delo*), $[\text{N}\,\text{m} = \text{J}]$ — joule.

#### → Right-hand side (*desna stran*)

Example (*zgled*): $\dfrac{d}{dt}\big(x^2(t)\big) = 2 \cdot x \cdot \dot{x}(t)$

In 3D:

$$\frac{d}{dt}\big(v^2(t)\big) = \frac{d}{dt}(\vec{v} \cdot \vec{v}) = 2(\vec{v} \cdot \dot{\vec{v}}) = 2(\vec{v} \cdot \vec{a})$$

The inverse operation (*obratna operacija*):

$$\int_{t_z}^{t_k} 2(\vec{a} \cdot \vec{v})\,dt = v^2(t)\Big|_{t_z}^{t_k} = v^2(t_k) - v^2(t_z)$$

where $v(t_k)$ is the final velocity (*končna*) and $v(t_z)$ the initial velocity (*začetna*). So the right-hand side is:

$$m\int_{t_z}^{t_k} (\vec{a} \cdot \vec{v})\,dt = \underbrace{\frac{1}{2}m v_k^2}_{W_k} - \frac{1}{2}m v_z^2$$

$W_k$ … **[[Kinetic Energy|kinetic energy]]** (*kinetična energija*)

$$A = \Delta W_k = W_k^k - W_k^z$$

**Conservation theorem** (*ohranitveni izrek*): if we add work, the kinetic energy changes (*če dodajamo delo, se bo kinetična energija spremenila*).

#### Sign of the work: $A > 0$ or $A < 0$

![[Physics 3 sign of work.svg]]

$$\vec{F} \cdot d\vec{s} = F \cdot ds \cdot \cos\theta$$

**For $A < 0$:** friction and air resistance always point in the direction of $-\vec{v}$ (*so vedno v smeri $-\vec{v}$*):

$$\vec{F}_{tr} \parallel (-d\vec{s}), \qquad \cos\theta = -1 \implies A < 0$$

→ **dissipative forces**: $A < 0$ (they brake — *zavirajo*).

**Example: work in uniform circular motion** (*zgled: delo pri enakomernem kroženju*):

$$d\vec{s} = \vec{v} \cdot dt, \qquad \vec{F}_z \perp d\vec{s} \quad \left(\theta = \tfrac{\pi}{2} = 90^\circ\right)$$

$$\vec{F}_z \cdot d\vec{s} = F_z \cdot ds \cdot \cos\theta = 0$$

$$A = 0 \implies v_z^2 = v_k^2 = v^2 = \text{const.}, \qquad \Delta W_k = 0$$

#### Work of the force of gravity (*delo sile teže*)

![[Physics 3 work of gravity.svg]]

$$\vec{F}_g \cdot d\vec{s} = -F_g \cdot dz, \qquad -dz = ds \cdot \cos\theta$$

$$A_g = \int_{\vec{r}_z}^{\vec{r}_k} \vec{F}_g \cdot d\vec{s} = -\int_{h_z}^{h_k} F_g\,dz = -m g\,\Delta h = -m g\,(h_k - h_z)$$

- The work of the force of gravity is **independent of the path**; it depends only on the initial and final position (height) (*delo sile teže je neodvisno od poti, odvisno je le od začetne in končne lege — višine*).
- Consequence (*posledica*): if we start and finish at the same height, the work is 0 (*začnemo, končamo na isti višini — delo je 0*).
- $\implies$ a **[[Conservative Force|conservative force]]** (*konzervativna sila*).

The work of conservative forces is replaced by potential energy (*delo konzervativnih sil nadomesti potencialna energija*).

**[[Potential Energy|Potential energy]]** (*potencialna energija*):

$$\Delta W_{pot} = -A_{sile}$$

For the force of gravity — gravitational potential energy at the Earth's surface (*gravitacijska potencialna energija na površju Zemlje*):

$$W_p = m \cdot g \cdot h, \qquad \Delta W_p = m \cdot g \cdot \Delta h = -A_g$$

#### Our theorem (*naš izrek*)

$$A_{zun} = \Delta W_k + \Delta W_p$$

$A_{zun}$ is the work of all external forces **except the force of gravity** (*razen sile teže*), because we moved it into $W_p$ (*ker smo jo prestavili v $W_p$*).

#### Work of the spring force (*delo sile vzmeti*)

$$\vec{F}_z = k \cdot \Delta x \quad\to\quad \vec{F}_{vz} = -k \cdot \Delta x$$

Simpler notation (*lažji zapis*), with $\Delta\vec{x} = \vec{x}$:

$$\vec{F}_{vz} = -k\,\vec{x}$$

![[Physics 3 spring work.svg]]

We stretch / compress the spring (*vzmet raztegujemo / stiskamo*): $d\vec{s} = d\vec{x}$ ($\theta = 0$), so $\vec{F}_{vz} \cdot d\vec{x} = -k \cdot x \cdot dx$:

$$A_{vz} = -k\int_{x_z}^{x_k} x\,dx = -k\,\frac{x^2}{2}\Bigg|_{x_z}^{x_k} = -\left(\frac{k\,x_k^2}{2} - \frac{k\,x_z^2}{2}\right)$$

The work depends only on the initial and final position (*delo je odvisno od začetne, končne lege*). We introduce (*vpeljemo*):

$$W_{pr} = \frac{1}{2}k x^2$$

$W_{pr}$ … elastic (potential) energy (*prožnostna (potencialna) energija*).

$$A_{zun} = \Delta W_k + \Delta W_p + \Delta W_{pr} \quad (+\,\Delta W_n)$$

- $A_{zun}$ … work of all external forces except $\vec{F}_g$ and $\vec{F}_v$ (*razen $\vec{F}_g$, $\vec{F}_v$*)
- $\Delta W_n$ … internal energy (*notranja energija*)

Why a theorem and not a law? Because it does not hold in every case (*zakaj izrek in ne zakon? Ker ne velja v vseh primerih*).

### Theorem of conservation of momentum (*izrek o ohranitvi gibalne količine*)

Newton's 2nd law again, but now over time $dt$ (*spet čas $dt$*):

$$\vec{F}_z = m \cdot \vec{a} \;\to\; \int_{t_z}^{t_k} \vec{F}_z\,dt = \int_{t_z}^{t_k} m \cdot \vec{a}\,dt$$

$$\int_{t_z}^{t_k} \vec{F}_z\,dt = m(\vec{v}_k - \vec{v}_z) = m\vec{v}_k - m\vec{v}_z = \vec{G}_k - \vec{G}_z$$

**[[Momentum]]** (*gibalna količina*):

$$\vec{G} = m \cdot \vec{v} \qquad [\text{kg}\,\text{m/s}]$$

$$\underbrace{\int_{t_z}^{t_k} \vec{F}_z\,dt}_{\text{impulse of the external forces}} = \Delta\vec{G}$$

- The left side is the **[[Impulse|impulse]] of the external forces** (*sunek zunanjih sil*).
- Theorem of conservation of momentum (*izrek o ohranitvi gibalne količine*) — (a law, because it always holds — *zakon, ker velja vedno*).

## Questions

- [ ] Why does Mercury's orbit not (quite) agree with Newton's equations?
- [ ] How can light, which has no mass, be bent by a galaxy (gravitational lens)?

## Connections

- Course: [[Physics]]
- Previous lecture: [[2026-10-13 - Circular Motion and Newton's Laws - 2]] — circular motion ($a_r = \omega^2 r$), Newton's laws, force of gravity, friction
- [[Derivative]] — chain rule, $\frac{d}{dt}(v^2) = 2\,\vec{v} \cdot \vec{a}$
- [[Integral]] — work and impulse as integrals

## Sources

- Handwritten notes: [[Sources/physics/photoNotes/lectures/lecture 3.pdf|lecture 3]]
- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015), sections 6.6, 7.1–7.4, 8.1
