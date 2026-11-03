---
type: "[[Lectures]]"
course: "[[Physics]]"
date: 2026-11-03
week: "5"
---

# 2026-11-03 - Angular Momentum, Kepler's Laws, Precession and Oscillations

## Main Idea

Integrating Newton's 2nd law for rotation $\vec{M} = J\vec{\alpha}$ over time gives the **theorem of conservation of [[Angular Momentum|angular momentum]]** (*izrek o ohranitvi vrtilne količine*): the angular impulse of the torques (*sunek navorov*) equals the change of the angular momentum $\vec{\Gamma} = J\vec{\omega}$. If there is no angular impulse, $\vec{\Gamma}$ is conserved. Two experiments with a rotating chair show this. The same law follows for a point body from $\vec{\Gamma} = \vec{r} \times \vec{G}$, and it explains [[Kepler's Laws|Kepler's laws]] of planetary motion. A torque perpendicular to $\vec{\Gamma}$ changes only its direction, not its size. This is the [[Precession|precession]] of a spinning top (*vrtavka*), of the Earth's axis and of the gyroscope. The lecture ends with [[Harmonic Oscillation|harmonic oscillation]] (*harmonično nihanje*): the projection of circular motion, and a mass on a spring, whose equation $\ddot{x} = -\omega^2 x$ always has a harmonic solution.

## Notes

### Theorem of conservation of angular momentum (*izrek o ohranitvi vrtilne količine*)

#### ① From Newton's 2nd law for rotation (*iz II. N.Z. za kroženje*)

$$\vec{M} = J \cdot \vec{\alpha} \quad / \int dt$$

$$\underbrace{\int_{t_z}^{t_k} \vec{M}\,dt}_{\text{angular impulse (sunek navorov)}} = \int dt\; J \cdot \frac{d\vec{\omega}}{dt} = J\vec{\omega}_k - J\vec{\omega}_z$$

**Angular momentum** (*vrtilna količina*), written with gamma (*gama*):

$$\vec{\Gamma} = J \cdot \vec{\omega}$$

$$\int_{t_z}^{t_k} \vec{M}\,dt = \Delta\vec{\Gamma} = \vec{\Gamma}_k - \vec{\Gamma}_z$$

with the [[Moment of Inertia|moment of inertia]] $J = \sum_i m_i r_i^2$.

When the arms are spread (*razširjen*), the person rotates more slowly (*počasneje vrtel*). With the arms pulled in (*skupaj*), they rotate faster (*hitreje vrtel*):

![[Physics 5 spinning person.svg]]

#### Experiment 1 (*eksperiment 1*): rotating chair with weights

![[Physics 5 chair with weights.svg]]

The person on the chair is approximated by a cylinder:

$$J = \frac{1}{2}\,mR^2 = \frac{1}{2} \cdot 70\,\text{kg} \cdot (0{,}15\,\text{m})^2 \approx 1\,\text{kg}\,\text{m}^2$$

The weights (*uteži*) in the outstretched hands:

$$J_u = 2 \cdot 5\,\text{kg} \cdot (0{,}8\,\text{m})^2 = 6{,}4\,\text{kg}\,\text{m}^2$$

There is no angular impulse of external torques:

$$\int \vec{M}\,dt = 0 \implies \vec{\Gamma}_k = \vec{\Gamma}_z \implies J_k\vec{\omega}_k = J_z\vec{\omega}_z$$

$$\frac{\omega_k}{\omega_z} = \frac{J_z}{J_k} \approx 5$$

When the person pulls the weights in, $J$ decreases and the chair spins about 5 times faster.

#### Experiment 2 (*eksperiment 2*): the wheel (*kolo*)

![[Physics 5 wheel experiment.svg]]

A person on the rotating chair holds a spinning wheel and then turns it upside down. Indices: $v$ = the chair with the person, $k$ = the wheel; superscripts $z$/$k$ = beginning/end.

$$\Gamma_v^z = 0, \qquad \Gamma_k^z = \omega_k J_k$$

$$\Gamma_k^k = -\omega_k J_k$$

$$\implies \Gamma_v^k = 2\,\omega_k J_k$$

The total angular momentum is conserved. When the wheel's angular momentum is reversed, the chair has to take $2\,\omega_k J_k$.

#### ② For a point body (*za točkasto telo*)

![[Physics 5 point mass angular momentum.svg]]

In time $dt$ (*v času dt*), from the [[Momentum|momentum]] theorem, multiplied vectorially by $\vec{r}$ (*vektorsko množimo*):

$$\vec{F}\,dt = d\vec{G} \quad / \vec{r} \times$$

$$\underbrace{\vec{r} \times \vec{F}}_{\vec{M}}\,dt = \vec{r} \times d\vec{G} \overset{?}{=} d\vec{\Gamma}$$

By the product rule:

$$d(\vec{r} \times \vec{G}) = \underbrace{d\vec{r} \times \vec{G}}_{0} + \vec{r} \times d\vec{G}$$

because $d\vec{r} = \vec{v}\,dt$ and $\vec{G} = m\vec{v}$, so $d\vec{r} \times \vec{G} = m\,dt\;\vec{v} \times \vec{v} = 0$. With

$$\vec{\Gamma} = \vec{r} \times \vec{G} \implies \vec{M}\,dt = d\vec{\Gamma} \implies \int_{t_z}^{t_k} \vec{M}\,dt = \Delta\vec{\Gamma}$$

This derivation is useful for the motion of the planets in the Solar System (*osončje*). This is where Kepler's laws come in.

### [[Kepler's Laws]] (*Keplerjevi zakoni*)

Kepler lived before Newton (*živel pred Newtonom*).

#### 1st law: the planets move around the Sun along ellipses (*planeti se gibljejo okrog Sonca po elipsah*)

![[Physics 5 ellipse.svg]]

**Eccentricity** (*ekscentričnost*): how stretched the ellipse is (*kako raztegnjena je elipsa*):

$$\varepsilon = \frac{e}{a} \qquad (\varepsilon = 0 \;\dots\; \text{circle — } \textit{krog})$$

| body | $\varepsilon$ |
|---|---|
| Mercury (*Merkur*) | $0{,}2056$ |
| Earth (*Zemlja*) | $0{,}0167$ |
| Halley's comet (*Halleyev komet*) | $0{,}967$ |

![[Physics 5 orbit and tilt.svg]]

The gravitational force points towards the Sun, along $\vec{r}$:

$$\vec{F}_g \times \vec{r} = 0 \quad \text{(no torque — } \textit{ni navora}\text{)}$$

The ellipse has nothing to do with the seasons (*to nima veze z letnimi časi*). The seasons come from the tilt of the Earth (*nagnjenost Zemlje*). The axis is always tilted at the same angle, so at different times of the year the sunlight falls at different angles (*sončni žarki padejo pod različnim kotom*).

We have 2 kinds of angular momentum (*2 Γ imamo*):

1. around the planet's own axis (*okoli lastne osi*)
2. the orbit of the planets around the Sun (*kroženje planetov okoli Sonca*)

#### 2nd law: equal areas in equal times

![[Physics 5 swept area.svg]]

The line between the Sun and the planet (*zveznica*) sweeps out equal areas (*ploščina*) in equal times.

So for part of the year the Earth is faster, when it is closer to the Sun (*del v letu je Zemlja hitrejša, ko je bližje Soncu*).

![[Physics 5 perihelion aphelion.svg]]

- **perihelion** (*perihelij*): the point closest to the Sun (*najbližje Soncu*)
- **aphelion** (*afelij*): the point farthest from the Sun (*najbolj oddaljeno od Sonca*)

At the perihelion:

$$J_P = m r^2, \qquad \Gamma_P = J\omega = m r^2 \omega, \qquad v = \omega r \implies \Gamma_P = m\,r\,v$$

There is no torque, so $\Gamma_P = \Gamma_A$:

$$\frac{v_P}{v_A} = \frac{r_A}{r_P} = \frac{1 + \varepsilon}{1 - \varepsilon}$$

For Halley's comet this ratio is $\approx 60$: at the perihelion it is about 60 times faster than at the aphelion.

#### 3rd law

$$\frac{t_0^2}{a^3} = \text{konst.}$$

$t_0$ … orbital period (*obhodni čas*), $a$ … semi-major axis (*velika polos*)

Derivation for a circular orbit:

![[Physics 5 circular orbit.svg]]

planet: $m$, Sun: $M$

$$F_c = m\omega^2 r, \qquad F_g = \frac{G\,m\,M}{r^2}$$

$$\boxed{F_c = F_g}$$

$$m\omega^2 r = \frac{G\,m\,M}{r^2}, \qquad \omega = \frac{2\pi}{t_0}$$

$$m\,r\,\frac{(2\pi)^2}{t_0^2} = \frac{G\,m\,M}{r^2}$$

Putting the constants on one side (*konstante na eno stran*):

$$\frac{t_0^2}{r^3} = \text{konst.}$$

For a circle $a = r$. For an ellipse the derivation is harder (*za elipso je zahtevnejše*).

### Precession of a spinning top (*precesija vrtavke*)

#### Experiment 1 (*eksperiment 1*)

![[Physics 5 top precession.svg]]

The vectors lie in perpendicular planes (*ležijo na pravokotnih ravninah*). By the right-hand rule (*pravilo desne roke*):

$$\vec{M}_g = \vec{r} \times \vec{F}_g$$

![[Physics 5 precession dGamma.svg]]

$$\vec{M}_g\,dt = d\vec{\Gamma}, \qquad \vec{M}_g \perp \vec{\Gamma}_0 \implies d\vec{\Gamma} \perp \vec{\Gamma}$$

(if we look at a small enough $dt$ — *če pogledamo dovolj mali dt*)

The change of the size of the angular momentum in time $dt$:

$$d|\vec{\Gamma}|^2 = d(\vec{\Gamma} \cdot \vec{\Gamma}) = d\vec{\Gamma} \cdot \vec{\Gamma} + \vec{\Gamma} \cdot d\vec{\Gamma} = 2\,\vec{\Gamma} \cdot d\vec{\Gamma} = 0$$

because the two are perpendicular, so the [[Dot Product|dot product]] is $0$ (*ker sta pravokotna, je skalarni produkt 0*). The size of $\vec{\Gamma} = J\vec{\omega}$ stays the same, so the top keeps spinning just as fast (*ves čas se ohranja lastna hitrost*).

But its direction changes (*spreminja pa se kot*):

$$M_g\,dt = \Gamma_0\,d\varphi$$

(we already saw this for rotation — *smo že videli pri vrtenju*)

$$\frac{d\varphi}{dt} = \omega_p = \frac{M_g}{\Gamma_0}$$

$\omega_p$ … angular velocity of precession (*kotna hitrost precesije*)

#### Precession of the Earth

![[Physics 5 Earth torque.svg]]

- sphere (*sfera*): $M_g = 0$
- not a sphere ($\neq$ *sfera*): $M_g \neq 0$

The Earth rotates around its tilted axis with $t_0 = 24\,\text{h}$. The seasons are a consequence of the tilt (*posledica nagnjenosti so letni časi*). The Earth is not a perfect sphere, so the Sun's gravity has a torque on it and its axis precesses:

![[Physics 5 precession cone.svg]]

$$t_0^p = 26\,000 \text{ years}$$

The angle moves, so the seasons shift too (*kot se premika → letni časi se premikajo*).

#### Gyroscope (*giroskop*)

Precession is used for navigation (*precesija se uporablja za navigacijo*).

![[Physics 5 gyroscope.svg]]

With a gyroscope you can tell where north is, because it keeps its direction all the time (*ker ves čas ohranja smer*). The ISS uses gyroscopes.

### Oscillation (*nihanje*)

#### Experiment 1 (*eksperiment 1*): projection of circular motion

![[Physics 5 circle projection.svg]]

A point moving along a circle:

$$x(t) = r\cos(\omega t), \qquad y(t) = r\sin(\omega t)$$

When it is lit from the side, its shadow on the wall moves up and down between $-r$ and $r$:

$$y(t) = r\sin(\omega t)$$

#### [[Harmonic Oscillation]] (*harmonično / sinusno nihanje*)

![[Physics 5 pendulum.svg]]

A pendulum oscillates harmonically for small angles (*harmonično nihanje za male kote*).

$$y(t) = A\sin(\omega t + \varphi)$$

- $A$ … amplitude (*amplituda*)
- $\varphi$ … phase shift (*fazni zamik*)

![[Physics 5 sine cosine.svg]]

For the experiment it is $A\cos(\omega t)$, because

$$\sin\!\left(\omega t + \frac{\pi}{2}\right) = \cos(\omega t)$$

To describe an oscillation we need **2 initial conditions** (*2 začetna pogoja*):

$$y(t = 0), \qquad v(t = 0)$$

**Period** (*nihajni čas*):

$$t_0 = \frac{2\pi}{\omega}$$

#### Experiment 2 (*eksperiment 2*): mass on a spring (true harmonic oscillation — *pravo harmonično nihanje*)

![[Physics 5 spring oscillator.svg]]

There is no friction (*ni trenja*). The equilibrium position (*ravnovesna lega*) is $x = 0$.

Solution (*rešitev*): $x(t) = A\sin(\omega t)$

Spring force and Newton's 2nd law:

$$F = -k\,x, \qquad F = m\,a = m\,\ddot{x} = m\,\frac{d^2x}{dt^2}$$

$$m\,\ddot{x} = -k\,x$$

This is a 2nd order [[Differential Equation|differential equation]] (*diferencialna enačba 2. reda*).

Let's check whether the solution from the experiment satisfies the equation (*preverimo, če je iz eksperimenta enačba v redu*):

$$\dot{x}(t) = A\,\omega\cos(\omega t)$$

$$\ddot{x}(t) = -A\,\omega^2\sin(\omega t) = -\omega^2 x(t)$$

$$\ddot{x}(t) = -\omega^2 x(t) \implies \omega = \sqrt{\frac{k}{m}}$$

Unit check:

$$\left[\frac{1}{\text{s}}\right] = \sqrt{\frac{[\text{N}/\text{m}]}{[\text{kg}]}} = \sqrt{\frac{\text{kg}\,\text{m}}{\text{m}\,\text{s}^2\,\text{kg}}} = \left[\frac{1}{\text{s}}\right] \quad ✓$$

Whenever

$$\ddot{y}(t) = -\omega^2 y(t),$$

the solution is always harmonic oscillation, no matter what we are talking about (*rešitev je vedno harmonično nihanje, ne glede na to, o čem se pogovarjamo*).

## Questions

- [ ] In experiment 1, $J_z/J_k \approx 5$. Which $J$ values give exactly this ratio (where are the weights at the end, and is the moment of inertia of the arms included)?

## Connections

- Course: [[Physics]]
- Previous lecture: [[2026-10-27 - Systems of Bodies, Collisions and Rotation - 4]]: torque, moment of inertia, $\vec{M} = J\vec{\alpha}$, momentum theorem
- [[2026-10-20 - Forces, Work, Energy and Momentum - 3]]: gravitation $F_g = G\,m M / r^2$, momentum and impulse
- [[2026-10-13 - Circular Motion and Newton's Laws - 2]]: circular motion, $\omega$, centripetal force
- [[Cross Product]]: $\vec{\Gamma} = \vec{r} \times \vec{G}$, $\vec{M} = \vec{r} \times \vec{F}$
- [[Dot Product]]: $d|\vec{\Gamma}|^2 = 2\,\vec{\Gamma} \cdot d\vec{\Gamma}$
- [[Momentum]], [[Torque]], [[Moment of Inertia]]
- [[2026-10-14 - Polar Form of Complex Numbers - 2]] (Calculus): the same $r\cos\varphi$, $r\sin\varphi$ description of a point on a circle

## Sources

- Handwritten notes: [[Sources/physics/photoNotes/lectures/lecture 5.pdf|lecture 5]]
- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015): section 7 (Kepler's laws and planetary motion, p. 59–60), 9.6 (angular momentum, worked example 9.6.1 on perihelion and aphelion), 10.1 (sinusoidal oscillation), 10.2 (spring pendulum)
- [Axial precession — Wikipedia](https://en.wikipedia.org/wiki/Axial_precession): period of the Earth's precession ≈ 26 000 years
