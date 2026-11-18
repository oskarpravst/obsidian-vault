---
type: "[[Lectures]]"
course: "[[Physics]]"
date: 2026-11-17
week: "7"
---

# 2026-11-17 - Electric Field, Gauss's Law and Capacitors

## Main Idea

The lecture replaces action at a distance with the **[[Electric Field|electric field]]** (*električno polje*): a charge changes the space around itself, and another charge feels this change. The field strength is $\vec{E} = \vec{F}/e_2$ with the unit V/m, and the fields of several sources add as vectors ([[Superposition|superposition]]). The field is described with **field lines** (*silnice*) and with **equipotential surfaces** (*ekvipotencialne ploskve*), and the two are always perpendicular.

An [[Electric Dipole|electric dipole]] has total charge $0$, but in a homogeneous field it feels a torque $\vec{M} = \vec{p}_e \times \vec{E}$ and has the energy $W_e = -\vec{p}_e \cdot \vec{E}$ (the microwave oven). The number of field lines is proportional to the charge, which leads to [[Gauss's Law|Gauss's law]] $e = \oint (\varepsilon_0 \vec{E}) \cdot d\vec{S}$.

In a metal the charges move to the surface, the surface is an equipotential surface and there is no field inside (Faraday cage, Van de Graaff generator). In an insulator the molecules polarize and weaken the field by the factor $\varepsilon$ (*dielektričnost*). Gauss's law gives the field of a charged plate and of the **parallel-plate [[Capacitor|capacitor]]** (*ploščati kondenzator*), its voltage $U = Ed$ and capacitance $C = \varepsilon\varepsilon_0 S/d$, and how capacitors combine in parallel.

## Notes

### From Coulomb's law to the field

[[Coulomb's Law]] from the last lecture:

$$\vec{F}_c = \frac{e_1 e_2}{4\pi\varepsilon_0 r^2}\,\frac{\vec{r}}{r}$$

![[Physics 7 two charges.svg]]

How can one particle act on another particle (*kako lahko en delec deluje na drug delec*)?

1. **Action at a distance** (*delovanje na daljavo*).

The correct description is the **concept of the field** (*koncept polja*), with 2 processes:

1. The particle with charge changes the properties of the space around itself: it creates the electric field (*ustvari el. polje*). Every point in space has properties that the charge changes. The charge $e_1$ is the **source of the electric field** (*izvor el. polja*).
2. The other particle feels this change (*drugi delec čuti to spremembo*).

A particle does not feel itself (*samega sebe delec ne čuti*).

### Describing the field

1. **with field lines** (*opis polja s silnicami*), a) below: the force is tangent to the field line (*sila je tangentna na silnico*)
2. **with equipotential surfaces** (*opis polja z ekvipotencialnimi ploskvami*), b), see [[#Equipotential surfaces]]

![[Physics 7 field lines of a point charge.svg]]

![[Physics 7 force tangent to field line.svg]]

**Convention** (*dogovor*): field lines come out of positive charges (*silnice izhajajo iz pozitivnih nabojev*).

$$\vec{F}_{e,1\to2} = \underbrace{\frac{e_1}{4\pi\varepsilon_0 r^2}\,\frac{\vec{r}}{r}}_{\text{we can call this the field}} \cdot\, e_2 = \vec{E}_1 \cdot e_2$$

$\vec{E}_1$ is the **electric field strength** (*jakost el. polja*), unit $\left[\frac{\text{V}}{\text{m}}\right]$:

$$\vec{E}_1 = \frac{\vec{F}_{1\to2}}{e_2}$$

**[[Superposition]]** (summing gives the final effect — *seštevanje je končen učinek*): the strengths of electric fields also add (*tudi pri el. se jakosti polj seštevajo*).

### Several sources of the field (*več izvorov polja*)

![[Physics 7 superposition of fields.svg]]

$$\vec{E}(\vec{r}) = \vec{E}_1(\vec{r}) + \vec{E}_2(\vec{r}) + \vec{E}_3(\vec{r}) \qquad \text{(vector addition — } \textit{vektorsko seštevanje}\text{)}$$

### Electric dipole (*električni dipol*)

Example: two charges $e_1 = +e$ and $e_2 = -e$ at distance $\vec{d}$:

![[Physics 7 electric dipole.svg]]

$$\vec{E}_d = \vec{E}_1 + \vec{E}_2$$

Hydrogen atom (*vodikov atom*): if we take these two charges (looking from far away — *če gledamo daleč stran*), the total charge is $0$. In reality the charges are separated (*v resnici sta naboja razmaknjena*), and this is how the hydrogen atom can interact with its surroundings (*interaktira z okoljem*). The dipole moment is $> 0$, so we have a net effect (*imamo net učinek*). One would think the total field is zero, but it is not (*celotno polje bi mislil, da je nič, ampak ni*).

#### Dipole in a homogeneous field

Lesson (*lekcija*): what forces act on a dipole (what is relevant here — *kaj je tukaj relevantno*)?

Parallel field lines = **homogeneous field** (*homogeno polje*): wherever we place a charge, the force is the same, and all forces point in the same direction (*vse sile kažejo v isto smer*).

![[Physics 7 dipole in homogeneous field.svg]]

A couple of forces (*dvojica sil*):

$$\sum \vec{F}_z = \vec{F}_+ + \vec{F}_- = 0$$

The centre of mass (M.S.) is at rest, but we can have rotation of the dipole (*imamo lahko rotacijo*):

$$\vec{M}_+ = \vec{r}_+ \times \vec{F}_+ = \frac{\vec{d}}{2} \times e\vec{E}$$

$$\vec{M}_- = \vec{r}_- \times \vec{F}_- = \left(-\frac{\vec{d}}{2}\right) \times (-e\vec{E}) = \frac{\vec{d}}{2} \times e\vec{E}$$

$$\vec{M}_z = \vec{M}_+ + \vec{M}_- \neq 0 \;=\; \vec{d} \times e\vec{E}$$

$\vec{d}$ and $e$ are properties of the dipole (*lastnost dipola*):

$$\vec{M}_z = (e\,\vec{d}) \times \vec{E}$$

$$\boxed{\vec{M}_z = \vec{p}_e \times \vec{E}} \qquad [\text{Asm}]$$

$\vec{p}_e = e\vec{d}$ is the **electric dipole moment** (*električni dipolni moment*).

Atoms and molecules have dipole moments (*atomi, molekule imajo dipolne momente*).

**Microwave oven** (*mikrovalovna pečica*): microwaves are an electromagnetic wave (*el.-mag. valovanje*) that acts on the dipole molecules of water. The field rotates the water molecule, then the field turns around and rotates it in the other direction, … it accelerates it (*pospešuje*). The energy is transferred into the matter and creates internal energy (*notranjo energijo*) by shaking the water dipoles (*s tresenjem dipolov vode*). That is why heating works very well on water, but not on dry things (*ne pa na suhih stvareh*).

#### Energy of the dipole

$$\vec{M}_z = 0 \iff \vec{p}_e \parallel \vec{E}$$

![[Physics 7 dipole angle.svg]]

$$\Delta W_e(\varphi) = \int_{\varphi_z}^{\varphi_k} M_z\,d\varphi = \int_{\varphi_z}^{\varphi_k} p_e E\sin\varphi\,d\varphi$$

$$\Delta W_e(\varphi) = -p_e E\cos\varphi\,\Big|_{\varphi_z}^{\varphi_k} = \underbrace{(-p_e E\cos\varphi_k)}_{W_e(\varphi_k)} - \underbrace{(-p_e E\cos\varphi_z)}_{W_e(\varphi_z)}$$

for a rotation (*za zasuk*). The **energy of the electric dipole** (*energija el. dipola*):

$$\boxed{W_e(\varphi) = -\vec{p}_e \cdot \vec{E}}$$

It is largest when $\vec{p}_e$ and $\vec{E}$ point in opposite directions (*nasprotno obrnjena*) and smallest when they are aligned (*poravnana*).

### Field lines and Gauss's law

Flax seeds (charged) in oil (*lanena semena, naelektrena, v olje*) show the field lines; the oil is there so they do not fly around (*da ne opletajo*): the resistance slows them down (*upor zavira*).

How many field lines (*koliko silnic*)? The number of field lines is proportional to the charge of the source (*št. silnic $\propto e$ v izvoru*):

![[Physics 7 field lines and charge.svg]]

$$\vec{E} = \frac{e}{4\pi\varepsilon_0 r^2}\,\frac{\vec{r}}{r}$$

Magnitude (*velikost*):

$$E = \frac{e}{4\pi\varepsilon_0 r^2} \;\propto\; \frac{\text{no. of field lines}}{\text{area of the sphere } (4\pi r^2)}$$

$$(\varepsilon_0 E)\underbrace{(4\pi r^2)}_{S} = e$$

So $E$ can also be measured as the number of field lines per unit area (*št. silnic / ploskovna enota*).

When the smoke clears (*ko se dim razkadi*), we get **[[Gauss's Law|Gauss's law]] for the electric field** (*Gaussov zakon za el. polje*), where we only count the field lines (*samo štejemo silnice*):

$$e = \oint_S (\varepsilon_0\vec{E}) \cdot d\vec{S}$$

$\varepsilon_0\vec{E} = \vec{D}$ is the **density of the electric field** (*gostota el. polja*), and $d\vec{S} = dS\,\frac{\vec{r}}{r}$ points along the **outer normal** (*zunanja normala*, out of the surface):

![[Physics 7 Gauss sphere.svg]]

### Equipotential surfaces

Describing the field with equipotential surfaces (*opis polja z ekvipotencialnimi ploskvami*). The potential:

$$V_1 = \frac{W_{e,1\to2}}{e_2}$$

For a point charge (*točkast naboj*):

$$W_{ep} = \frac{e_1 e_2}{4\pi\varepsilon_0 r} = \underbrace{\frac{e_1}{4\pi\varepsilon_0 r}}_{V_1 \text{ potential}} \cdot\, e_2, \qquad V_1 = \frac{W_{ep}}{e_2}$$

$V_1(r)$ for different $r$:

![[Physics 7 equipotential surfaces.svg]]

On each circle $\Delta V_1 = 0$, so $e_2$ has the same energy at every point of it (*enaka energija*). An **equipotential surface** (*ekvipotencialna ploskev*) is the set of all points in space that have the same potential.

For gravitation: contour lines (*izohipse*), curves of equal height (*krivulje z enako višino*).

Potentials also add (*tudi potenciali se seštevajo*); a potential is like only the height of a hill or valley (*samo višina hriba / doline*).

**Thought** (*razmislek*):

$$\Delta W_{ep} = -\int_{\vec{r}_z}^{\vec{r}_k} \vec{F}_e \cdot d\vec{r} \implies \Delta V_1 = \frac{\Delta W_{ep}}{e_2} = \underbrace{-\int_{\vec{r}_z}^{\vec{r}_k} \vec{E}_1 \cdot d\vec{r}}_{\text{link between field strength and potential}}$$

The reverse relation (*obratno relacijo*) we get with the **gradient**.

If the displacement is perpendicular to the field, the change is $0$ (*če premik pravokotno, bo sprememba 0*): field lines are perpendicular to equipotential surfaces.

$$\text{equipotential surfaces} \perp \text{field lines}$$

### Conductors in the electric field

Thought: we take a metal and put a charge $e$ on it. In conductors (*prevodniki*) the electrons move freely through the metal. How will the charges distribute over the metal (*kako se bodo porazdelili po kovini*)?

![[Physics 7 charge on conductors.svg]]

They arrange themselves so that the sum of all forces on each individual free particle is zero (if they do not move — *če se nič ne premikajo*): the force of the neighbours is zero parallel to the surface (*sila sosedov = nič, vzporedno s površino*). From the surface the charge must not escape (*iz površine ne more pobegniti*):

$$\vec{F}_e = -e_0\vec{E}_z$$

So the field must be perpendicular to the surface (*polje mora biti takšno*): $\vec{E}_z \perp$ surface, and the surface is an equipotential surface.

![[Physics 7 field at metal surface.svg]]

- The surface of a metal is an equipotential surface (**always** — *vedno*).
- Inside the metal there is no field (*v notranjosti kovine polja ni*). This phenomenon is the **Faraday cage** (*Faradayeva kletka*): all the charge goes to the surface, and the electric field inside is $0$.
- **Influence** (*influenca*): the redistribution of charges in a metal (*porazdelitev nabojev v kovini*). Why don't phones work in tunnels (*zakaj v tunelih ne delujejo telefoni*)? "Because of influence."

#### Van de Graaff generator of voltage / charge (*generator napetosti / naboja*)

![[Physics 7 Van de Graaff generator.svg]]

Inside the sphere the field is $0$ (*notri bo polje 0*). Is there a limit to how much charge we can squeeze onto the sphere (*ali je omejitev, koliko naboja lahko stlačim na sfero*)? In theory no. In practice there are no ideal insulators except vacuum: the sphere charges so much that the air starts to conduct (*zrak začne prevajati*).

### Insulators: polarization of matter (*polarizacija snovi*)

An **insulator** (*izolator*) has no free charges, but the molecules of an insulator can have a dipole moment. In the field, electric dipoles form (*nastanejo el. dipoli*), and with its own field the matter polarizes in the opposite direction and weakens the field (*se polarizira v nasprotni smeri, oslabi*): it becomes a bit weaker.

**Electric field in matter** (*el. polje v snovi*):

![[Physics 7 polarization.svg]]

Polarization (dipoles) of matter $\implies$ weaker field in matter (*šibkejše polje v snovi*):

$$\vec{E}(\vec{r}) = \frac{e}{4\pi\varepsilon_0\,\varepsilon\,r^2}\,\frac{\vec{r}}{r}$$

$\varepsilon$ is the **dielectric constant of the matter** (*dielektričnost snovi*), $\varepsilon \geq 1$ (the field is always weaker — *polje je vedno šibkejše*). Matter with a dielectric constant reduces the field (insulators — *izolatorji*).

### Parallel-plate capacitor (*ploščati kondenzator*)

#### 1 metal plate with area $S$ (*kovinska plošča, površine S*)

Charge $+e$; $\vec{E}$ is homogeneous and perpendicular to the surface ($\perp$ *ploskev*). We use Gauss's theorem (*Gaussov izrek*): the body is a cylinder (*valj*), and the surface is the surface of the cylinder.

![[Physics 7 one charged plate.svg]]

$$e = \oint_S (\varepsilon_0\vec{E}) \cdot d\vec{S} \qquad \text{(the field is constant — } \textit{polje je konstantno}\text{)}$$

The mantle (*plašč*) has a normal $\perp$ to the field, so it contributes nothing (*nič ne prispeva*); only the two outer faces remain (*ostaneta samo zunanji ploskvi*):

$$e = 2\varepsilon_0 E S_0 \implies \boxed{E = \frac{e}{2\varepsilon_0 S_0} = \frac{\sigma}{2\varepsilon_0}} \quad (*)$$

with the **surface charge density** (*ploskovna gostota naboja*) $\sigma = \dfrac{e}{S_0}$.

#### 2 metal plates (*kovinski plošči*)

![[Physics 7 parallel plate capacitor.svg]]

$\vec{E}$ is homogeneous. Only the inner surface (*notranja ploskev*) of the cylinder has a field through it; outside, $\vec{E} = 0$ (*zunaj*):

$$e = 1\cdot\varepsilon_0 E S_0$$

$$\boxed{E = \frac{e}{\varepsilon_0 S_0} = \frac{\sigma}{\varepsilon_0}} = 2 \times \text{(1 plate)}$$

Gauss's theorem (*Gaussov stavek*): $e$ = the charge inside the cylinder (*naboj znotraj valja*). For a cylinder around both plates $e = 0$, so the field outside is also $0$ (*torej polje zunaj tudi 0*).

This must not hold (*ne sme veljati!*), it is wrong: the electric field cannot pass through the metal (*električno polje ne more čez kovino*); the notebook marks the field outside as "$2\times$" and "sum $= 0$":

![[Physics 7 wrong capacitor field.svg]]

#### Capacitor with a dielectric

We fill the capacitor with a dielectric ($\varepsilon$ — *napolnimo kondenzator z dielektrikom*):

$$\vec{E} = \frac{\sigma}{\varepsilon_0\,\varepsilon} \qquad \text{weaker field (} \textit{šibkejše polje}\text{)}$$

**Voltage between the plates** (*napetost med ploščama*):

$$U = \Delta V = -\int_{\vec{r}_z}^{\vec{r}_k} \vec{E} \cdot d\vec{r}$$

![[Physics 7 capacitor voltage.svg]]

$$U = \Delta V = -E \cdot d, \qquad |\vec{E}| = \frac{U}{d}$$

#### Capacitance (*kapaciteta kondenzatorja*)

A calculation trick that we need in electronics (*računski trik, ki ga rabimo v elektroniki*):

$$C = \frac{e}{U}$$

with the charge on the capacitor (*naboj na kondenzatorju*) $e$ and the voltage on the plates (*napetost na ploščah*) $U$.

$$e = \varepsilon\varepsilon_0 S E, \qquad |\vec{E}| = \frac{U}{d}$$

$$e = \underbrace{\frac{\varepsilon\varepsilon_0 S}{d}}_{C}\,U, \qquad C\left[\frac{\text{As}}{\text{V}} = \text{F}\right] \text{ — farad}$$

### Combining capacitors (*kombinirana vezja*)

If we have several capacitors, how do we combine them (*kako kondenzatorje kombiniramo*)? We look for the **total or equivalent capacitance** of the circuit (*skupna oz. nadomestna kapaciteta vezja*).

#### Parallel connection (*vzporedno vezana*)

![[Physics 7 capacitors in parallel.svg]]

Thought (*razmislek*): two capacitors in parallel act as one capacitor whose plate is split into $S_1$ and $S_2$, $S = S_1 + S_2$:

$$C = \varepsilon_0\varepsilon\,\frac{S}{d} \implies C_1 = \varepsilon\varepsilon_0\,\frac{S_1}{d}, \qquad C_2 = \varepsilon\varepsilon_0\,\frac{S_2}{d}$$

$$\boxed{C = C_1 + C_2}, \qquad e = e_1 + e_2, \qquad U_1 = U_2$$

#### Series connection (*zaporedno*)

![[Physics 7 capacitors in series.svg]]

$C = ?$ Thought: are the two capacitors connected with the surroundings or not (*ali sta povezani z okolico ali ne*)? (The notes end here.)

## Questions

- [ ] What is the equivalent capacitance of two capacitors in series, and why does it matter whether the middle plates are connected with the surroundings?
- [ ] How exactly does influence stop phones from working in tunnels?
- [ ] How do we get the field strength from the potential with the gradient?

## Connections

- Course: [[Physics]]
- Exercises: [[Sources/physics/photoNotes/vaje/vaje 7.pdf|vaje 7]]: harmonic oscillation $\ddot{x} + \omega^2 x = 0$, $x = A\sin(\omega t + \delta)$ and a rod hanging on a spring (task 7.2, unfinished). The colloquium covers everything up to and including oscillation (*do sem pišemo kolokvij*). Then waves $y = y_0\sin(\omega t - kx + \delta)$, $k = \frac{2\pi}{\lambda}$, $c = \lambda\nu = \frac{\omega}{k}$, the wave equation, and standing waves from adding the right- and left-moving wave with the boundary conditions. Task 8.1: a pipe with neighbouring resonances at 240 Hz and 280 Hz, giving $l = 4{,}25$ m
- Previous lecture: [[2026-11-10 - Physical Pendulum, Waves and Electrostatics - 6]]: electric charge, Coulomb's law, electric potential energy, potential and voltage
- [[2026-10-27 - Systems of Bodies, Collisions and Rotation - 4]]: torque, couple of forces, centre of mass
- [[2026-10-20 - Forces, Work, Energy and Momentum - 3]]: conservative forces, potential energy, gravitation
- [[Cross Product]]: $\vec{M} = \vec{p}_e \times \vec{E}$
- [[Dot Product]]: $W_e = -\vec{p}_e \cdot \vec{E}$, $\vec{E} \cdot d\vec{S}$
- [[Integral]]: Gauss's law, voltage
- [[Torque]], [[Potential Energy]], [[Conservative Force]], [[Newton's Law of Universal Gravitation]], [[Electric Charge]], [[Voltage]], [[Faraday Cage]], [[Dielectric]]

## Sources

- Handwritten notes: [[Sources/physics/photoNotes/lectures/lecture 7.pdf|lecture 7]]
- M. Ambrožič, I. Drevenšek Olenik, M. Vilfan, *Fizika* (FRI, 2015): 11.2 (electric field, p. 104), 11.4 (field of a charged plate $E = \sigma/2\varepsilon_0$ and Gauss's law, p. 114–115), 11.5 (equipotential surfaces, dipole, p. 116–117), 11.6 (voltage $U = -Ed$, p. 118), 12.1 (capacitor, $C = \varepsilon_0 S/d$, Van de Graaff generator and Faraday cage, p. 119–122), 12.4 (dielectric constant, polarization, dipole moment $\vec{p} = e\vec{r}$ in Asm, $C = \varepsilon\varepsilon_0 S/d$, p. 130–131)
