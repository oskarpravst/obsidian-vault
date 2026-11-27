---
type: "[[Lectures]]"
course: "[[Physics]]"
date: 2026-11-24
week: "8"
---

# 2026-11-24 - Capacitor Energy, Electric Current and Semiconductors

## Main Idea

The lecture finishes [[Capacitor|capacitors]]. In a **series connection**, influence puts the same charge on every capacitor, so $\frac{1}{C} = \frac{1}{C_1} + \frac{1}{C_2}$. In a parallel connection $C = C_1 + C_2$. Charging a capacitor one small charge $de$ at a time gives its **energy** $W_e = \frac{1}{2}\frac{e^2}{C} = \frac{1}{2}CU^2$. This energy is stored in the field with the **energy density** $w_e = \frac{1}{2}\varepsilon\varepsilon_0E^2$, and the energy can travel through space as an electromagnetic wave.

**Electrodynamics** (*elektrodinamika*) is the motion of charges through matter. The [[Electric Current|electric current]] (*električni tok*) is $I = \frac{de}{dt}$, and microscopically $I = e_1 n_e S v_d$, with the density of charge carriers $n_e$ and the **drift velocity** $v_d$ (*potovalna hitrost*). The carriers are electrons in metals and **holes** (*vrzeli*) in some materials. The current density $\vec{j}_e = e_1 n_e \vec{v}_d$ and the mobility $\vec{v}_d = \mu\vec{E}$ (Drude's model) lead to [[Ohm's Law|Ohm's law]] $\vec{j}_e = \frac{1}{\zeta}\vec{E}$, and for a straight wire $U = RI$ with $R = \frac{\zeta L}{S}$. Resistors combine in series ($R = R_1 + R_2$) and in parallel ($\frac{1}{R} = \frac{1}{R_1} + \frac{1}{R_2}$), following [[Kirchhoff's Laws|Kirchhoff's laws]].

The lecture ends with [[Semiconductor|semiconductors]]. Silicon doped with donors gives an n-type semiconductor and with acceptors a p-type. Joining the two types gives a [[Diode|diode]] with a depletion layer. From this came the [[Transistor|transistor]] and the MOSFET, and CMOS is the technology of all of today's chips.

## Notes

### Capacitors in series (*zaporedna vezava*)

![[Physics 8 capacitors in series.svg]]

The two middle plates are connected to each other but not to the source. The source charges the outer plates with $+e$ and $-e$, and by **influence** (*influenca*) the charges on the middle plates redistribute into $-e$ and $+e$. So the charges are equal (*naboji so enaki*):

$$C_1:\ e_1 = e, \qquad C_2:\ e_2 = e, \qquad U = U_1 + U_2$$

$$e_1 = C_1 U_1, \qquad e_2 = C_2 U_2, \qquad e = CU$$

Capacitance of the equivalent circuit (*kapaciteta nadomestnega vezja*):

$$\boxed{\frac{1}{C} = \frac{1}{C_1} + \frac{1}{C_2}}$$

### Capacitors in parallel (*vzporedna vezava*)

![[Physics 8 capacitors in parallel.svg]]

$$U_1 = U, \qquad U_2 = U, \qquad e = e_1 + e_2 \implies \boxed{C = C_1 + C_2}$$

### Energy of a capacitor (*energija kondenzatorja*)

We charge an empty capacitor (plate area $S$, distance $d$) by moving small charges $de$ from one plate to the other. The charge on the plate is $e_p$ (*naboj na plošči*).

![[Physics 8 charging a capacitor.svg]]

At the start (*začetek*) $e = 0$, so $\vec{E} = 0$ and $U = Ed = 0$. Moving the first $de$ costs no work:

$$A_e = 0 \quad (\vec{E} = 0)$$

After that the plates carry $-de$ and $+de$, so $\vec{E} \neq 0$ and $U \neq 0$. Each further $de$ costs the work

$$A_e = de \cdot U$$

where the voltage depends on the charge $e_p$ already on the plate: $e_p = CU \to U = \frac{e_p}{C}$:

$$A_e = \frac{e_p}{C}\,de$$

With $-2de$ and $+2de$ on the plates, and so on, until the plates carry $-e$ and $+e = e_p$:

$$U = \frac{e_p}{C}, \qquad A_e = \frac{e_p}{C}\,de$$

Every time we move a small charge, we add up the work (*vsakič ko prestavimo majhen naboj, seštevamo delo*):

$$A_e = \int_0^{e} \frac{e_p}{C}\,de_p = \frac{1}{C}\,\frac{e^2}{2} = \Delta W_{ep} \qquad \left(\int x\,dx = \frac{x^2}{2}\right)$$

$$\boxed{W_e = \frac{1}{2}\,\frac{e^2}{C} = \frac{1}{2}\,CU^2}$$

**Important trick** (*pomemben trik*): insert $C = \frac{\varepsilon\varepsilon_0 S}{d}$ and $U = E\cdot d$:

$$W_e = \frac{1}{2}\,\frac{\varepsilon\varepsilon_0 S}{d}\,E^2 d^2 = \frac{1}{2}\,\varepsilon\varepsilon_0 E^2\,(S\cdot d)$$

where $S\cdot d = V_c$ is the volume between the plates (*volumen med ploščama*).

#### Energy density (*gostota energije*)

$$w_e = \frac{W_e}{V_c} = \frac{W_e}{S\cdot d} = \frac{1}{2}\,\varepsilon\varepsilon_0 E^2 \qquad \left[\frac{\text{J}}{\text{m}^3}\right]$$

$$\boxed{w_e = \frac{1}{2}\,\varepsilon\varepsilon_0 E^2} \quad \text{(for some capacitor — } \textit{za nek kondenzator}\text{)}$$

It reminds us of the spring (*spominja na vzmet*), $W = \frac{1}{2}kx^2$.

What does this mean (*kaj to pomeni*)?

![[Physics 8 energy between the plates.svg]]

We calculated the energy density between the capacitor plates, that is, the **energy in the field** (*energijo v polju*); we used up energy to build it (*porabili smo energijo*). This energy can move through space (*se lahko premika po prostoru*) → electromagnetic wave (*el.-mag. valovanje*).

### Electrodynamics: electric current (*elektrodinamika, električni tok*)

The motion of electric charges through matter (*gibanje električnih nabojev po snovi*).

![[Physics 8 wire with charge carriers.svg]]

A wire is an electric current conductor (*žica: električni tokovni vodnik*). It has $N_e$ charges in the volume $S\cdot L$. The **density of charge carriers** (*gostota nosilcev naboja*) is a property of the matter (*lastnost snovi*):

$$\frac{N_e}{V} = \frac{N_e}{SL} = n_e \qquad \left[\frac{\text{no.}}{\text{m}^3}\right]$$

Metals have free carriers, electrons (*kovine: proste nosilce elektronov*).

#### Metals and insulators

Metal = conductor of electric current (*prevodnik el. toka*): it has free charge carriers (*prosti nosilci naboja*), the electrons $e^-$. Extra electrons remain (free, in the outer orbitals — *ostanejo odvečni elektroni, prosti v zunanjih orbitalah*).

![[Physics 8 metal lattice.svg]]

The fixed atoms without their outer $e^-$ (ions) give the metal its elasticity (*to daje kovini prožnost*). The free electrons give $n_e$.

Insulators are the opposite (*izolatorji, obratno*): all $e^-$ are bound, there are no free electrons (*vsi $e^-$ so vezani, ni prostih elektronov*).

#### Electric current

In time $t$, $e$ of charge flows out of the conductor (*iz vodnika odteče e nabojev*). The **electric current** is defined as:

$$I = \frac{e}{t} \quad [\text{A}]\ \text{ampere} \qquad \implies \qquad \boxed{I = \frac{de}{dt}}\ \text{in general (} \textit{splošno}\text{)}$$

The total charge (*celoten naboj*) is $e = N_e\cdot e_1 = N_e\cdot(-e_0)$:

$$I = \frac{e}{t} = e_1 n_e\cdot\frac{SL}{t}$$

where $\frac{L}{t}$ is the time in which the last electron also has to come out (*tudi zadnji e mora priti ven*), so $\frac{L}{t} = v_d$.

![[Physics 8 drift in a wire.svg]]

Say $\vec{E} > 0$ (from an external voltage — *zun. napetost*). The force on an electron is $\vec{F}_e = (-e_0)\vec{E}$, so the electrons drift against $x$. We want to drive the positive charges in that direction (*hočemo poz. pognati v tisto smer*), so $I > 0$:

$$I = e_1 n_e S v_d$$

The current is defined as the motion of positive charges (*tok je definiran kot gibanje poz. nabojev*). "Problem" (*težava*): the current is defined with a positive charge. In the $x$ direction $I > 0$:

$$I = \underbrace{(-e_0)}_{e_1}\cdot n_e\cdot S\cdot\underbrace{(-v_d)}_{\text{opposite to } x} = +e_0\,n_e S v_d > 0$$

**Salt in water** (*sol v vodi*): positive charges move in the direction of the electric field, negative ones in the opposite direction.

#### Holes (*vrzeli*)

For a solution yes, but do positive charge carriers exist in metals (*ali obstajajo poz. nosilci nabojev v kovinah*)? **Yes.**

![[Physics 8 holes in a lattice.svg]]

The negative cores are stable (*negativna jedra so stabilna*); the holes $v^+$ move. A **"hole"** (*luknja = vrzel*) is a missing electron: an electron was taken from the outer clouds (*iz zunanjih oblakov pobrali el.*). It is a free energy state, so any electron can jump there (*prosto energijsko stanje, sem lahko skoči kakršen koli el.*).

![[Physics 8 hole hopping.svg]]

When an electron jumps into a hole, the hole moves the other way. In an external field $\vec{E}$ (*v zun. polju*) the hole moves with the field, and $|\vec{v}_v| \neq |\vec{v}_e|$.

The **Hall effect** (*Hallov pojav*) can determine the charge carriers (*lahko določi nosilce naboja*). Trick (*trik*): in iron the charge carriers are holes, in gold they are electrons (*v železu so nosilci naboja vrzeli, v zlatu pa elektroni*). Crystal → fixed distances (bonds) (*kristal → fiksne razdalje, vezi*).

#### Current density (*gostota električnega toka*)

$$j_e = \frac{I}{S} = e_1 n_e v_d \qquad \left[\frac{\text{A}}{\text{m}^2}\right]$$

Nicer (*lepše*) as a vector ($\vec{v}$ is a vector):

$$\vec{j}_e = \underbrace{e_1 n_e}_{\text{depends on the matter}}\,\vec{v}_d$$

where $\vec{v}_d$ is the direction of motion (*smer gibanja*) and depends on the matter and the external $\vec{E}$ (*odvisno od snovi in zun. $\vec{E}$*).

$$I = \vec{j}_e\cdot\vec{S} = \vec{j}_e\cdot\vec{n}\,S, \qquad \vec{j}_e\cdot\vec{n} = j_e\cos\varphi$$

![[Physics 8 current density through a surface.svg]]

#### Drude's model (*Drudejev model*)

Say $e_1 = -e_0$ ($e^-$):

$$\vec{F}_e = e_1\vec{E} = (-e_0)\vec{E}, \qquad -e_0\vec{E} = m_e\vec{a} \implies \vec{a} = -\frac{e_0\vec{E}}{m_e}$$

If we plug a hair dryer into the socket, the electrons would start to accelerate (*fen v utičnico, bodo el. začeli pospeševati*) → **this is not a good model** (*to ni vredu model*). An electron (or hole) in matter has to navigate through all the clouds of atoms (*mora navigirati skozi vse oblake atomov*), ergo the model is not simple.

**Drude's model:** metal = potential, with the fixed nuclei (crystal) in between. The particles bounce off and lose speed (*se odbijajo in izgubljajo hitrost*); in the end they travel with the "drift speed". It is a nice differential equation (*lepa diferencialna enačba*): Newton's 2nd law together with the collisions with the (ordered) crystal lattice (*II. N. z. skupaj s trki s kristalno mrežo, urejeno*).

$$\vec{v}_d \propto \vec{E}$$

The **drift velocity** (*potovalna hitrost*) is proportional to the field. The proportionality constant is the **mobility** (*gibljivost*), a property of the matter (*lastnost snovi*):

$$e^-:\ \vec{v}_d = -\mu_e\vec{E}, \qquad v^+:\ \vec{v}_v = +\mu_v\vec{E}, \qquad \mu_e \neq \mu_v$$

In general, matter with both types of charge carriers (*snov z obema tipoma nosilcev naboja*):

$$\vec{j}_e = \Big[\underbrace{(+e_0)\,n_v\mu_v}_{\text{holes}} + \underbrace{(-e_0)\,n_e(-\mu_e)}_{\text{electrons}}\Big]\vec{E}$$

Both terms are positive.

### Ohm's law (*Ohmov zakon*)

$$\boxed{\vec{j}_e = \frac{1}{\zeta}\,\vec{E} = \sigma\vec{E}}, \qquad \sigma = \frac{1}{\zeta}$$

- $\zeta$ (*ksi*) … **specific resistance** of the matter (*specifična upornost snovi*), unit $\left[\frac{\Omega\,\text{mm}^2}{\text{m}}\right]$
- $\sigma$ … **specific conductivity** (*specifična prevodnost*)

For a wire of length $L$ and cross-section $S$ with voltage $U$:

![[Physics 8 resistor as a wire.svg]]

$$|\vec{j}_e| = \frac{1}{\zeta}|\vec{E}| \implies \frac{I}{S} = \frac{1}{\zeta}\,\frac{U}{L} \implies U = \frac{\zeta L}{S}\,I$$

$$\boxed{U = R\cdot I}, \qquad R = \frac{\zeta L}{S} \quad (*)$$

$R$ is the electric **resistance** (*upor*), $\left[\frac{\text{V}}{\text{A}} = \Omega\right]$ ohm. This is Ohm's law for a straight conductor (resistance $R$ — *Ohmov zakon za ravni vodnik*).

| matter | $\zeta$ |
|---|---|
| metals (*kovine*) | $\sim 10^{-8}\ \Omega\text{m}$ (small — *majhna*) |
| insulators (*izolatorji*) | $\sim 10^{10}$–$10^{18}\ \Omega\text{m}$ |
| semiconductors (*polprevodniki*), very poor conductors: Si, Ge | $\sim 10^{3}\ \Omega\text{m}$ |

Air is an insulator, but if we put it in a strong electric field it will start to conduct. Insulators conduct in a strong enough electric field (*izolatorji prevajajo pri dovolj močnem el. polju*). Vacuum "does not conduct".

#### Drift velocity and thermal motion

In metals the typical drift velocity of $e^-$ is $v_d \sim 10^{-5}$–$10^{-4}$ m/s. The electrons form a gas, which has a temperature: they are not at rest, but move thermally because of the internal energy (*se termično premikajo zaradi not. energije*). Thermal motion of the electrons (*termično gibanje elektronov*): $v_e \sim 10^6$ m/s.

![[Physics 8 thermal motion.svg]]

Without a field the average velocity is $\bar{v} = 0$. With $\vec{E} \neq 0$ the cloud moves slowly (*oblak se počasi premika*), $\bar{v} = v_d$ (we imagine channels of water — *predstavljamo kanale vode*).

### Combining resistors (*kombiniranje uporov*)

Equivalent resistors (*nadomestni upori*), $R = ?$

#### Series connection (*zaporedna vezava*)

![[Physics 8 resistors in series.svg]]

- 1st Kirchhoff's law: $I = I_1 = I_2$ (the current is conserved — *ohranja tok*)
- $U = RI$
- 2nd Kirchhoff's law: $U = U_1 + U_2$ (the sum of the voltage drops = the external voltage — *vsota padcev napetosti = zun. nap.*)

$$R\cancel{I} = R_1\cancel{I_1} + R_2\cancel{I_2} \implies \boxed{R = R_1 + R_2}$$

This agrees with $(*)$, $R = \frac{\zeta L}{S}$: one wire of length $L = L_1 + L_2$:

![[Physics 8 wire in two pieces.svg]]

#### Parallel connection (*vzporedna vezava*)

![[Physics 8 resistors in parallel.svg]]

$$I = I_1 + I_2, \qquad U = U_1 = U_2 \implies \boxed{\frac{1}{R} = \frac{1}{R_1} + \frac{1}{R_2}}$$

### Semiconductors (*polprevodniki*)

What crystal structure (*kakšno kristalno strukturo*)? Si → 4 outer $e^-$ (group IV of the periodic table — *IV. skupina v periodnem sistemu*).

![[Physics 8 silicon lattice.svg]]

All outer $e^-$ are bound (*vsi zun. $e^-$ so vezani*):
- → like an insulator (*~ izolator*)
- → but they are weakly bound (*slabo so vezani*): if we tear off an $e^-$, we get carriers $e^-$, and $v^+$ remain (*$e^-$ odtrgamo, dobimo nosilce $e^-$ in ostanejo $v^+$*).

#### Doping (*dopiranje*)

We dope silicon: we add impurities (*dodamo primesi, nečistoče*):
- **donor impurities** (*donorske primesi*): group V, $5e^-$
- **acceptor impurities** (*akceptorske primesi*): group III, $3e^-$

![[Physics 8 doping.svg]]

a) The donor gives $4e^-$ into the lattice → one extra $e^-$ → a free, donated $e^-$ (*prosti doniran $e^-$*): a doped semiconductor of **type n**.

b) The acceptor is missing an $e^-$ → it takes one from its neighbours ("accepts" — *vzame sosedom, "akceptira"*) → free $v^+$ (*proste $v^+$*): a semiconductor of **type p**.

Good conductivity (*dobro prevodnost*): $\zeta \sim 10^{-4}\ \Omega\text{m}$, they conduct solidly (*solidno prevajajo*).

#### Diode (*dioda*)

A semiconductor element (*polprevodniški element*). The diode is the simplest one (*najbolj preprosta*): a **current rectifier** (*usmerjevalnik toka*).

![[Physics 8 diode.svg]]

If we put n and p together, the $e^-$ and $v^+$ pair up (**recombination** — *rekombinacija*) → a region without $e^-$ and $v^+$ (*območje brez $e^-$ in $v^+$*): the **depletion layer** (*depletirana plast*). Its field $\vec{E}$ gives the **blocking voltage** (*zaporna napetost*), and $I = 0$.

An external voltage can compensate this (*zunanja napetost lahko to kompenzira*). We have a valve (*imamo klapec*): if we straighten it out, it starts to flow (*če ravnamo, bo začelo teči*).

#### Transistor (*tranzistor*)

From this they made the transistor:

![[Physics 8 transistor.svg]]

Current flows only if we correctly add the extra voltage (*tok teče samo, če smo pravilno dodali dodatno napetost*) ⇒ the **gate** (*vrata*). $U \neq 0$ → current flows (*tok teče*):

![[Physics 8 voltage barrier.svg]]

Logic gates (*logična vrata*): bit 0 and 1.

#### MOSFET

**MOS**: a breakthrough in technology (*preboj v tehnologiji*), 1955 Bell Labs. Metal–oxide–semiconductor (MOS) **field-effect transistor** (FET):

![[Physics 8 MOSFET.svg]]

A metal (*kovina*) gate on SiO (insulator — *izolator*) over the semiconductor; only the field ($\vec{E}$) acts through the insulator (*samo polje*).

**Complementary MOS** (CMOS) → the technology of all of today's chips (*tehnologija vseh današnjih čipov*).

## Questions

- [ ] Why does air (an insulator) start to conduct in a strong electric field?
- [ ] What is the differential equation of Drude's model, and how does it give a constant drift velocity $v_d \propto E$?
- [ ] How does the Hall effect show whether the charge carriers are electrons or holes?
- [ ] How exactly does the extra voltage on the gate switch the current on in a transistor and in a MOSFET?

## Connections

- Course: [[Physics]]
- Exercises: [[Sources/physics/photoNotes/vaje/vaje 8.pdf|vaje 8]]: open pipe with neighbouring resonances at 240 Hz and 280 Hz, $L = \frac{c}{2\Delta\nu} = 4{,}25$ m, displacement 0,5 m outside the pipe and the pipe closed at one end, $\tilde\nu_n = \frac{c(2n-1)}{4L}$ (task 8.1); interference of two sources, constructive and destructive (*konstruktivna, destruktivna interferenca*); two wave sources on water, $c = \sqrt{gh}$, distance between them $a = 5{,}9$ m from $\frac{\delta x}{d} = \frac{\lambda}{a}$ (task 8.2); electrostatics, Coulomb's law $F_e = \frac{e_1 e_2}{4\pi\varepsilon_0 r^2}$, electrostatic energy; acceleration of a charged ball in an equilateral triangle of charges, $a = 1{,}95$ m/s² (task 9.1)
- Previous lecture: [[2026-11-17 - Electric Field, Gauss's Law and Capacitors - 7]]: parallel-plate capacitor, capacitance $C = \varepsilon\varepsilon_0 S/d$, parallel connection; its open question about capacitors in series is answered here
- [[2026-11-10 - Physical Pendulum, Waves and Electrostatics - 6]]: electric potential energy, voltage
- [[2026-11-03 - Angular Momentum, Kepler's Laws, Precession and Oscillations - 5]]: energy of a spring $\frac{1}{2}kx^2$, which the energy density resembles
- [[Integral]]: work of charging a capacitor
- [[Dot Product]]: $I = \vec{j}_e\cdot\vec{S}$
- [[Potential Energy]], [[Electric Field]], [[Voltage]], [[Electric Charge]], [[Dielectric]], [[Electromagnetic Wave]], [[Hall Effect]], [[Logic Gate|logic gates]] (Introduction to Digital Circuits)

## Sources

- Handwritten notes: [[Sources/physics/photoNotes/lectures/lecture 8.pdf|lecture 8]]
- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015): 12.1 (capacitance $e = CU$, p. 119–120), 12.2 (energy of a capacitor $W_e = e^2/2C = \frac{1}{2}CU^2$ and energy density $w_e = \frac{1}{2}\varepsilon_0E^2$, p. 123–124), 13.1 (electric current, $j = ne_1v$, thermal velocity $\sim 10^6$ m/s, mobility $v = \mu E$, p. 133–134), 13.2 (Ohm's law, $R = \zeta L/S$, $\sigma = 1/\zeta$, resistors in series and parallel, p. 135), 13.3 (Kirchhoff's laws, p. 137–139), 25 (Drude's model, p. 233), 26 (semiconductors, holes, doping, n- and p-type, table of $\zeta$, p. 235–238)
