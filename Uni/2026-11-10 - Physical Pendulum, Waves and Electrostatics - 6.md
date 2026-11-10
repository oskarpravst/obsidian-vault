---
type: "[[Lectures]]"
course: "[[Physics]]"
date: 2026-11-10
week: "6"
---

# 2026-11-10 - Physical Pendulum, Waves and Electrostatics

## Main Idea

The lecture continues with [[Harmonic Oscillation|harmonic oscillation]]. The equation $\ddot{x} + \omega^2 x = 0$ always has the solution $A\sin(\omega t + \delta)$. $\omega$ is a property of the system, and $A$ and $\delta$ depend on the initial conditions. Newton's 2nd law for rotation applied to a **physical pendulum** (*fizikalno nihalo*) gives the same equation for small angles, with $t_0 = 2\pi\sqrt{J/(mgr_*)}$. The mathematical pendulum is a special case of it. Adding damping and an external driving force gives the most general equation of oscillation and explains **resonance**. For the spring pendulum, the kinetic and elastic energy convert into each other and their sum $\frac{1}{2}kA^2$ is constant.

The second part is about [[Wave|waves]] (*valovanje*): the spreading of a disturbance through a medium, which carries energy. It covers longitudinal and transverse waves, the plane wave $y(x,t) = A\sin(kx - \omega t + \delta)$ with its time and space picture, the wave speed $c = \nu\lambda$, diffraction, Huygens' principle and superposition, and reflection at a fixed and a loose end.

The last part starts **electrostatics** (*elektrostatika*): [[Electric Charge|electric charge]] and the elementary charge $e_0$, quarks, conductors and insulators, [[Coulomb's Law|Coulomb's law]], and the electric [[Potential Energy|potential energy]], potential and [[Voltage|voltage]] (*napetost*), all built by analogy with gravitation.

## Notes

### Harmonic oscillation (continued)

$$\ddot{x} + \omega^2 x = 0$$

$\omega$ is a **property of the system** (*lastnost sistema*). The solution is an oscillation (*rešitev je nihanje*):

$$x(t) = A\sin(\omega t + \delta)$$

with the **amplitude** $A$ (*amplituda*) and the **phase** (*faza*) $\delta$. Both depend on the initial conditions (*odvisni od začetnih pogojev*).

$$\dot{x}(t) = v(t) = (A\omega)\cos(\omega t + \delta)$$

$$\ddot{x}(t) = a(t) = -(A\omega^2)\sin(\omega t + \delta)$$

$$\omega = \frac{2\pi}{t_0} = 2\pi\nu$$

![[Physics 6 harmonic oscillation.svg]]

### Physical pendulum (*fizikalno nihalo*)

A rigid body rotates about an axis (*vrtenje okrog osi*). [[Newton's Laws|Newton's 2nd law]] for rotation (*II. N. Z. za vrtenje*):

$$\vec{M}_z = J\,\vec{\alpha}$$

$$\vec{M}_z = \vec{M}_g = \vec{r}_* \times \vec{F}_g \quad \text{(in the direction of the } z \text{ axis — } \textit{v smeri z-osi}\text{)}$$

where $\vec{r}_*$ points from the axis to the centre of mass (*masno središče*, M.S.). The positive angle is counterclockwise (*nasprotni smeri urinega kazalca*), and the [[Torque|torque]] of gravity turns in the negative direction (*vrti navor v neg. smeri*):

![[Physics 6 physical pendulum.svg]]

$$M_g = -r_*\,mg\sin\varphi$$

![[Physics 6 torque of gravity.svg]]

$$-r_*\,mg\sin\varphi = J\,\alpha, \qquad \alpha = \ddot{\varphi}$$

$$J\ddot{\varphi} = -r_*\,mg\sin\varphi \quad / : J$$

$$\ddot{\varphi} + \frac{mgr_*}{J}\sin\varphi = 0$$

**Standard trick** (*standardni trik*): for small angles $\sin\varphi \approx \varphi$, an approximation (*približek*) for $\varphi \ll 1$:

$$\boxed{\ddot{\varphi} + \frac{mgr_*}{J}\,\varphi = 0}$$

$$\omega^2 = \frac{mgr_*}{J} \implies t_0 = 2\pi\sqrt{\frac{J}{mgr_*}}$$

#### How do we check this? (*kako to preverimo?*)

The idealized physical pendulum is the **mathematical pendulum** (*matematično nihalo*), a point body (*točkasto telo*) on a string:

![[Physics 6 mathematical pendulum.svg]]

$$r_* = l, \qquad J = ml^2$$

$$t_0 = 2\pi\sqrt{\frac{ml^2}{mgl}} = 2\pi\sqrt{\frac{l}{g}}$$

And what about everything else (*kaj pa z vsem ostalim*)? If we leave the equation as it is,

$$\ddot{\varphi} + \frac{mgr_*}{J}\sin\varphi = 0,$$

it is still an oscillation, but the solution is no longer simple (*še vedno je nihanje, ampak rešitev ni več preprosta*).

#### Foucault pendulum (*Foucaultovo nihalo*)

The oscillation happens with respect to the coordinates of the universe (*glede na vesoljske koordinate*). During the day, the direction of the oscillation changes (*skozi dan se smer nihanja spremeni*; all torques act on the axis — *vsi navori delujejo na os*).

#### Walking speed of dinosaurs (*hitrost hoje dinozavrov*)

It depends on the length of the legs: the leg acts as a pendulum (*noga deluje kot nihalo*).

### The most general equation of oscillation (*najbolj splošna enačba nihanja*)

$$\ddot{x} + \omega^2 x = 0 \qquad \text{harmonic oscillation — natural (} \textit{lastno}\text{): the system is left alone (} \textit{sistem pustimo pri miru}\text{)}$$

$$\ddot{x} + \omega^2 x + \underbrace{2\beta\dot{x}}_{\text{damping (dušenje)}} = \underbrace{f(t)}_{\text{external driving (zunanje vzbujanje)}}$$

With damping (no driving):

$$x(t) = e^{-\beta t}\sin(\dots)$$

Air resistance is damping (*zračni upor je dušenje*).

![[Physics 6 damped oscillation.svg]]

- With damping, the system loses energy (*z dušenjem sistem zgublja energijo*).
- With driving, we add energy (*z vzbujanjem energijo dodajamo*).

**[[Resonance]]** (*resonanca*) is the phenomenon when we match the driving frequency (*ko ujamemo frekvenco poganjanja*), like on a swing (*kot smo na gugalnici*): with the external frequency we match the natural frequency (*z zunanjo frekvenco ujamemo lastno frekvenco*). Example: the Tacoma Narrows bridge.

### Energy of the spring pendulum (*vzmetno nihalo*)

To get a local oscillation, we need 2 kinds of energy (*da pridemo do lokalnega nihanja, rabimo 2 vrsti energije*). The same holds in electromagnetism.

- **kinetic** (*kinetična*): $W_k = \frac{1}{2}mv^2 = \frac{1}{2}m\dot{x}^2 = \frac{1}{2}m\omega^2A^2\cos^2(\omega t + \delta)$
- **elastic** (*prožnostna*): $W_{pr} = \frac{1}{2}kx^2 = \frac{1}{2}kA^2\sin^2(\omega t + \delta)$
- **together** (*skupaj*): $W = W_k + W_{pr}$

With $\omega^2 = \dfrac{k}{m} \implies m\omega^2 = k$:

$$W = \frac{1}{2}kA^2\cos^2(\omega t + \delta) + \frac{1}{2}kA^2\sin^2(\omega t + \delta)$$

$$W = \frac{1}{2}kA^2 \implies \text{constant (} \textit{konstantno}\text{)}$$

The two energies add up (*energiji se seštejeta*) to a constant:

![[Physics 6 oscillator energy.svg]]

### Waves (*valovanje*)

A wave is the **spreading of a disturbance through a medium** (*širjenje motnje skozi sredstvo*). We have to understand it as energy (*razumeti moramo kot energijo*).

Sound spreads through space, but it is not wind (*zvok se širi skozi prostor ✗ to je veter*): the molecules only oscillate around their position (they do not travel — *ne potujejo*) and pass energy to each other (*med sabo prenašajo energijo*). This holds for all waves (*za vsa valovanja*).

- **Longitudinal** (*longitudinalno*): the disturbance spreads in the direction of the wave; the local oscillations are in the direction of propagation (*lokalna nihanja v smeri širjenja valovanja*).
- **Transverse** (*transverzalno*): the local oscillations are perpendicular to the direction of propagation (*pravokotno na smer širjenja*). Light is also transverse (*tudi svetloba*).

Waves on the sea are transverse (*valovi na morju transverzalno*). The speed of propagation depends on the matter (*hitrost razširjenja valovanja je odvisna od snovi*). In the sea it depends on the depth: deeper is faster than shallow (*globje hitreje kot plitvo*).

Example: a **tsunami**. Where the sea gets shallower the wave slows down, and the energy accumulates (*energija se nabira skupaj*):

![[Physics 6 tsunami.svg]]

#### Speed of wave propagation (*hitrost razširjenja valovanja*)

$c$ depends on the properties of the system, not on what we did with the excitation (*ne od tega, kar smo naredili z vzbujanjem*).

#### Plane wave (*ravni val*) — the nicest solution (*najlepša rešitev*)

$$y(x,t) = A\sin(kx - \omega t + \delta)$$

- $x$ — position (*lega*), $t$ — time (*čas*)
- $k$ — **wave number** (*valovno število*): $k = \dfrac{2\pi}{\lambda}$, with the **wavelength** $\lambda$ (*valovna dolžina*)
- $\omega$ — angular velocity (*kotna hitrost*): $\omega = 2\pi\nu = \dfrac{2\pi}{t_0}$, with the frequency $\nu$ (*frekvenca*) and the period $t_0$ (*perioda*)

![[Physics 6 plane wave 1D.svg]]

**Time picture of the wave** (*časovna slika vala*): $x = x_1$ is fixed. We hang a buoy in the water and see what happens to it (*bojo obesimo v vodi in vidimo, kaj se dogaja z njo*). One full oscillation (*poln nihaj*) takes $t_0$:

![[Physics 6 wave time picture.svg]]

**Space picture of the wave** (*krajevna slika vala*): $t = t_1$ is fixed. We take a photo (*naredimo fotografijo*): a frozen wave, a freeze frame (*zamrznjen val*). The distance between two crests is $\lambda$:

![[Physics 6 wave space picture.svg]]

#### How to express the speed from this (*kako iz tega izrazimo velikost*)

We place a surfer on the wave and film them (*postavimo surferja in ga snemamo*). On the wave, the surfer always moves at the same speed as the wave and is always at the same angle (*vedno pod enakim kotom*), so the phase is constant:

![[Physics 6 surfer.svg]]

$$kx - \omega t + \delta = \text{const.} \quad / \frac{d}{dt}$$

where $x(t)$ is the position of the surfer (*lega surferja*), so $c = v_{surf} = \dot{x}(t)$:

$$k\dot{x} - \omega + 0 = 0$$

$$kc - \omega = 0 \implies c = \frac{\omega}{k} = 2\pi\nu\,\frac{\lambda}{2\pi} = \nu\lambda$$

If the wave moved in the opposite direction ($\overleftarrow{c}$):

$$\sin(kx + \omega t + \delta)$$

#### Diffraction (*uklon*)

Plane wavefronts (*valovne fronte*), $\lambda$ apart, hit a wall with a narrow slit. Behind the slit the wave spreads in circles, also into the wave shadow (*širjenje valovanja v valovno senco*):

![[Physics 6 diffraction.svg]]

#### Huygens' principle (*Huygensovo načelo*)

Huygens turned the story around (*obrnil je zgodbo*): if we look at waves and several slits, the displacement at every point of the wave is the sum of partial waves (*delna valovanja se seštevajo*).

**[[Superposition]] of waves** (*superpozicija valovanj*):

$$y(x,t) = y_1(x,t) + y_2(x,t) + \dots$$

Every wave is composed of the waves that we get from a very narrow slit (circular waves — *krožni valovi*). An arbitrary wave (*poljubno valovanje*) is the superposition of circular waves from all points of space (*superpozicija krožnih valov iz vseh točk prostora*):

![[Physics 6 Huygens wavelets.svg]]

#### Reflection at the end of a string

![[Physics 6 reflection at ends.svg]]

At a fixed end (*fiksen konec*), the reflected pulse comes back upside down (dashed). The second drawing shows a loose end (*prost konec*).

### Electrostatics (*elektrostatika*)

**Electric charge** (*električni naboj*) is conserved in nature (*se ohranja v naravi*). Symbols $e$, $q$; unit $[\text{As}]$, ampere-second (*amper-sekunda*).

- If we rub amber with a cloth (*jantar drgnemo s krpo*), it becomes charged (*se naelektri*). The pointers move apart (*kazalci se razmaknejo*): we transferred charge to the metal device (*prenesli smo naboj na kovinsko napravo*).
- Charge causes some forces (*naboj povzroča neke sile*).
- There are 2 kinds of charge: $+$ and $-$.
- Glass rubbed with a cloth gets the opposite charge (*obratno*).
- The device is an **electroscope** (*elektroskop*), a simple experiment (*preprost eksperiment*):

![[Physics 6 electroscope.svg]]

**Elementary charge** (*osnovni naboj*) $e_0$. One electron $e^-$:

$$q_{e^-} = -e_0, \qquad e_0 = 1{,}6 \cdot 10^{-19}\,\text{As}$$

Proton and neutron:

$$q_p = +e_0, \qquad q_n = 0$$

That is why atoms are neutral (*zato so atomi nevtralni*). The charge of an atom, with the atomic number $Z$ (*vrstno število*):

$$q_{at} = Z\,q_{e^-} + Z\,q_p = Z(+e_0) + Z(-e_0) = 0$$

#### Quarks (*kvarki*)

Protons and neutrons are not elementary particles (*niso osnovni delci*): they are made of quarks (*sestavljeni so iz kvarkov*). The electron is an elementary particle. Quarks do not have the elementary charge (*nimajo osnovnega naboja*):

$$q_u = +\tfrac{2}{3}e_0, \qquad q_d = -\tfrac{1}{3}e_0$$

- proton (uud): $q_p = 2q_u + q_d = e_0$
- neutron (udd): $\implies q_n = 0$

- We know 6 kinds of quarks (*poznamo 6 vrst kvarkov*).
- The Higgs boson causes mass (*Higgsov bozon povzroča maso*).
- Smashing protons makes quarks fly in all directions (*razbijanje protonov povzroča letenje kvarkov v vse smeri*): a jet (*pljusk*).

#### Conductors and insulators

- **conductors** (*prevodniki*): the electrons move freely (*el. prosto gibajo*)
- **insulators** (*izolatorji*): they cannot move freely (*ne morejo se prosto gibati*)

#### [[Coulomb's Law]] (*Coulombov zakon*)

The electrostatic force acts between charges (*med naboji deluje elektrostatska sila*). Its direction is along the line joining the charges (*smer po zveznici nabojev*):

![[Physics 6 Coulomb law.svg]]

$$\vec{F}_{1\to2} = -\vec{F}_{2\to1} \quad \text{(III. N. Z.)}$$

$$\vec{r} = \vec{r}_2 - \vec{r}_1, \qquad r = |\vec{r}|$$

$$|\vec{F}_{1\to2}| = |\vec{F}_{2\to1}| = \frac{e_1 e_2}{r^2} \cdot \underbrace{\frac{1}{4\pi\varepsilon_0}}_{\text{some constant}} \quad [\text{N}]$$

**Influence constant** (*influenčna konstanta*):

$$\varepsilon_0 = 8{,}85 \cdot 10^{-12}\,\frac{\text{As}}{\text{Vm}} \qquad (\text{V — volt, m — metre})$$

$$[\text{V}\cdot\text{A}\cdot\text{s} = \text{J}], \qquad \left[\frac{\text{VAs}}{\text{m}} = \text{N}\right]$$

Influence (*influenca*) is the separation of charges in a metal in the presence of external charges (*razmik nabojev v kovini ob prisotnosti zunanjih nabojev*).

As a vector:

$$\vec{F}_{1\to2} = \frac{e_1 e_2}{4\pi\varepsilon_0 r^2} \cdot \left(\frac{\vec{r}}{r}\right)$$

The sign of the charges decides whether the force is attractive or repulsive (*glede na predznak nabojev privlačna ali odbojna*). $\frac{\vec{r}}{r}$ is a **normalized vector** (*normiran vektor*), $\left|\frac{\vec{r}}{r}\right| = \frac{r}{r} = 1$, the quantity for the direction (*količina za smer*). The same holds for gravitation:

$$\vec{F}_{g,1\to2} = -G\,\frac{m_1 m_2}{r^2}\left(\frac{\vec{r}}{r}\right)$$

Gravitation is attractive (*privlačna sila*): $m_1$ and $m_2$ are always positive, but charges are not necessarily positive (*naboji pa niso nujno pozitivni*).

$$(e_1 \cdot e_2) < 0 \to \text{attraction (} \textit{privlak}\text{)}, \qquad (e_1 \cdot e_2) > 0 \to \text{repulsion (} \textit{odboj}\text{)}$$

#### Electric potential energy (*električna potencialna energija*)

An upgrade (*nadgradnja*): the analogy between gravitation and the electric force. Both are [[Conservative Force|conservative forces]] (*obe sta konzervativne sile*): the final [[Work|work]] depends only on the initial and final energy (*končno delo odvisno samo od zač. in konč. energije*).

$\vec{F}_e$ is conservative $\implies$ we introduce the electric potential energy:

$$\Delta W_{ep} = -A_e = -\int_{\vec{r}_z}^{\vec{r}_k} \vec{F}_e \cdot d\vec{r}$$

We pin $e_1$ in place (*pribijemo*) and move $e_2$ from $r_1$ to $r_2$. Since the angle is $0$ ($\theta = 0$, $d\vec{s} = d\vec{r}$), $\vec{F}_e \cdot d\vec{r} = F_e\,dr$:

![[Physics 6 potential energy path.svg]]

$$\Delta W_{ep} = -\int_{r_1}^{r_2} F_e\,dr = -\int_{r_1}^{r_2} \frac{e_1 e_2}{4\pi\varepsilon_0 r^2}\,dr$$

$$= +\frac{e_1 e_2}{4\pi\varepsilon_0 r}\bigg|_{r_1}^{r_2} = \frac{e_1 e_2}{4\pi\varepsilon_0 r_2} - \frac{e_1 e_2}{4\pi\varepsilon_0 r_1}$$

$$\Delta W_{ep} = W_{ep}(r_2) - W_{ep}(r_1)$$

For 2 point charges (*za 2 točkasta naboja*):

$$W_{ep}(r) = \frac{e_1 e_2}{4\pi\varepsilon_0 r}$$

![[Physics 6 electric potential energy.svg]]

What we learn (*naučimo se*): if $W_p$ between 2 charges is positive, the force is repulsive (*odbojna*); if it is negative, it is attractive (*privlačna*).

Gravitational (*gravitacijska*):

$$W_g = -G\,\frac{m_1 m_2}{r}$$

**Convention** (*dogovor*): the electric potential energy far away is $0$, so we calculate everything with respect to $\infty$ (*vse računamo glede na* $\infty$):

$$W_{ep}(\vec{r}) = -\int_{\vec{r}_2 \to \infty}^{\vec{r}_2 = \vec{r}} \vec{F}_e \cdot d\vec{r}$$

**Why is this important?** (*zakaj pomembno?*) How drugs attach to some part of a cell (*kako se zdravila priključijo na nek del celice*), computed on a computer: we bring molecule $a$ closer to cell $b$. The potential (positive or negative) repels or attracts (*odbija / privlači*).

#### Potential and voltage (*potencial in napetost*)

$e_2$ is a **test charge** (*testni naboj*): with it we "feel the electric field" (*"otipamo el. polje"*).

**Voltage** (*napetost*):

$$\Delta V(\vec{r}_1, \vec{r}_2) = \frac{\Delta W_{ep}}{e_2}$$

Our example (*naš zgled*):

$$\Delta V = \frac{e_1}{4\pi\varepsilon_0 r_2} - \frac{e_1}{4\pi\varepsilon_0 r_1} \qquad [\text{V} - \text{volt}]$$

$$= V_{e_1}(\vec{r}_2) - V_{e_1}(\vec{r}_1)$$

$V$ is the **potential** (*potencial*): the potential energy of the test charge per unit charge, $V = W_{ep}/e_2$ (*potencialna energija testnega naboja na enoto naboja*). The difference of potentials is the voltage (*razlika potencialov je napetost*). This is the voltage in the specifications of batteries (*to je napetost v specifikacijah za baterije*).

## Questions

- [ ] How exactly does the leg length give a dinosaur's walking speed if the leg acts as a pendulum?
- [ ] Why does the plane of oscillation of the Foucault pendulum turn during the day, and what does "all torques act on the axis" mean here?
- [ ] At a loose end of a string, is the reflected pulse upright or upside down?

## Connections

- Course: [[Physics]]
- Previous lecture: [[2026-11-03 - Angular Momentum, Kepler's Laws, Precession and Oscillations - 5]]: harmonic oscillation, $\ddot{x} = -\omega^2 x$, mass on a spring
- [[2026-10-27 - Systems of Bodies, Collisions and Rotation - 4]]: torque, moment of inertia, $\vec{M} = J\vec{\alpha}$, centre of mass
- [[2026-10-20 - Forces, Work, Energy and Momentum - 3]]: conservative forces, potential energy, spring work $\frac{1}{2}kx^2$, gravitation
- [[Cross Product]]: $\vec{M}_g = \vec{r}_* \times \vec{F}_g$
- [[Dot Product]]: $\vec{F}_e \cdot d\vec{r}$
- [[Integral]]: work and potential energy
- [[Moment of Inertia]], [[Torque]], [[Differential Equation]], [[Newton's Law of Universal Gravitation]]

## Sources

- Handwritten notes: [[Sources/physics/photoNotes/lectures/lecture 6.pdf|lecture 6]]
- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015): 10.2 (physical pendulum, p. 91–92), 10.3 (mechanical energy of undamped pendulums and damping, p. 96–97), 10.4 (waves, wave speed $c = \lambda\nu$, p. 98–100), 11.1 (electric charge and Coulomb's law, p. 101), 11.3 (electric potential energy, p. 106), 11.4 (electric potential, p. 108), 19.3 (diffraction and Huygens' principle, p. 192)
