# Ideas

Programming practice through projects that simulate or implement concepts from my other courses. Each idea is a link: when I start a project, I click it, Obsidian creates the note, and I insert `Templates/Project Template.md` (it then shows up in [[Projects]]). The links under each idea point to the lectures, exercises and book sections where the concept comes from.

## How to see the results

- **Terminal:** draw with characters (`#`, `*`, `.`) using `System.out.print`; enough for grids, graphs and fractals.
- **SVG file:** an SVG is plain text (`<circle cx="10" cy="20" r="3"/>`), so a program can write one with `printf` and I open it in a browser. Real pictures with nothing beyond what I already know.

## Physics

- [[Projectile Motion Simulation]] — move a ball in small time steps (`v += a·dt`, `x += v·dt`), find where it lands and compare with the formula; then add air resistance. The basic technique behind every physics simulation.
	- Concepts: [[Kinematics|kinematics]], [[Newton's Laws]]
	- Lecture: [[2026-10-11 - Physical Quantities and Kinematics - 1]]; exercises [[Sources/physics/photoNotes/vaje/vaje 1.pdf|vaje 1]]
	- Book: [[Sources/physics/FRI_Fizika.pdf#page=38|Fizika (FRI)]], 5.7 *Poševni met*, p. 38; [[Sources/physics/Fundamentals of Physics, Volume 1, 12th Edition -- David Halliday & Robert Resnick & Jearl Walker -- 1, 1, 12, 2021 -- John Wiley & Sons, Incorporated -- isbn13 9781119773511 -- cd3eb591b4b8fc5bd2026b8183689455 -- Anna’s Archive.pdf#page=97|Halliday]], 4.4 Projectile Motion
- [[Planetary Orbit Simulation]] — the same step method, with the force pointing to the Sun and falling as 1/r². Draw the orbit as an SVG and check Kepler's laws (e.g. equal areas in equal times).
	- Concepts: [[Newton's Law of Universal Gravitation]], [[Kepler's Laws]], [[Angular Momentum|angular momentum]]
	- Lectures: [[2026-10-20 - Forces, Work, Energy and Momentum - 3]] (gravitation), [[2026-11-03 - Angular Momentum, Kepler's Laws, Precession and Oscillations - 5]]
	- Book: [[Sources/physics/FRI_Fizika.pdf#page=59|Fizika (FRI)]], *Keplerjevi zakoni in gibanje planetov*, pp. 59–60; [[Sources/physics/Fundamentals of Physics, Volume 1, 12th Edition -- David Halliday & Robert Resnick & Jearl Walker -- 1, 1, 12, 2021 -- John Wiley & Sons, Incorporated -- isbn13 9781119773511 -- cd3eb591b4b8fc5bd2026b8183689455 -- Anna’s Archive.pdf#page=409|Halliday]], 13.6 Planets and Satellites: Kepler's Laws
- [[Oscillator Simulation]] — a spring or a pendulum. Watch the energy: with a too large `dt` it slowly grows, though it should stay constant. Shows why a simulation is only an approximation.
	- Concepts: [[Harmonic Oscillation|harmonic oscillation]], [[Kinetic Energy|kinetic]] and [[Potential Energy|potential energy]]
	- Lecture: [[2026-11-03 - Angular Momentum, Kepler's Laws, Precession and Oscillations - 5]]
	- Book: [[Sources/physics/FRI_Fizika.pdf#page=87|Fizika (FRI)]], 10.1 *Sinusno nihanje* and 10.2 *Nekaj značilnih nihal*, pp. 87–95; [[Sources/physics/Fundamentals of Physics, Volume 1, 12th Edition -- David Halliday & Robert Resnick & Jearl Walker -- 1, 1, 12, 2021 -- John Wiley & Sons, Incorporated -- isbn13 9781119773511 -- cd3eb591b4b8fc5bd2026b8183689455 -- Anna’s Archive.pdf#page=458|Halliday]], 15.1 Simple Harmonic Motion
- [[Bouncing Balls Simulation]] — several balls in arrays `x[]`, `y[]`, `vx[]`, `vy[]` bouncing off the walls and each other; check that momentum is conserved. A bit harder.
	- Concepts: [[Momentum|momentum]], [[Elastic Collision|elastic]] and [[Inelastic Collision|inelastic collision]], [[Array|arrays]]
	- Lecture: [[2026-10-27 - Systems of Bodies, Collisions and Rotation - 4]]; exercises [[Sources/physics/photoNotes/vaje/vaje 5.pdf|vaje 5]] (elastic and perfectly inelastic collisions)
	- Book: [[Sources/physics/FRI_Fizika.pdf#page=62|Fizika (FRI)]], 8.2 *Trki in odrivi*, pp. 62–65; [[Sources/physics/Fundamentals of Physics, Volume 1, 12th Edition -- David Halliday & Robert Resnick & Jearl Walker -- 1, 1, 12, 2021 -- John Wiley & Sons, Incorporated -- isbn13 9781119773511 -- cd3eb591b4b8fc5bd2026b8183689455 -- Anna’s Archive.pdf#page=269|Halliday]], 9.7–9.8 Elastic Collisions, Collisions in Two Dimensions

## Calculus

- [[Mandelbrot Set Renderer]] — for each point c of the complex plane repeat z = z² + c and check whether it escapes. Needs only complex numbers, loops and character output; short, and the picture is surprisingly nice. **Good first project.**
	- Concepts: [[Complex Number|complex numbers]], [[Sequence|sequences]], [[Limit of a Sequence|limit of a sequence]]
	- Lectures: [[2026-10-14 - Polar Form of Complex Numbers - 2]], [[2026-10-28 - Limits of Sequences - 4]]
	- Book: [[Sources/calculus/skripta.pdf#page=31|Analiza I (skripta)]], 1.7 *Kompleksna števila*, p. 21; *Zaporedja kompleksnih števil* [[Sources/calculus/skripta.pdf#page=71|p. 61]]
- [[Sequences and Series Explorer]] — compute the first 1000 terms or partial sums and watch whether and how fast they converge. Compare the harmonic series (diverges, but very slowly) with the sum of 1/n² (converges to π²/6).
	- Concepts: [[Series]], [[Harmonic Series|harmonic series]], [[Geometric Series|geometric series]], [[Limit of a Sequence|limit of a sequence]]
	- Lectures: [[2026-10-28 - Limits of Sequences - 4]], [[2026-11-04 - Series and Convergence Tests - 5]]
	- Book: [[Sources/calculus/skripta.pdf#page=227|Analiza I (skripta)]], ch. 6 *Vrste*, p. 217; harmonic series [[Sources/calculus/skripta.pdf#page=230|p. 220]]
- [[Terminal Function Plotter]] — draw the graph of f(x) with characters inside a rectangle with axes. Practice in mapping coordinates (the same problem as the spiral keyboard in homework 2, in the other direction).
	- Concepts: [[Function|functions]]
	- Book: [[Sources/calculus/skripta.pdf#page=136|Analiza I (skripta)]], *Skiciranje grafa funkcije*, p. 126

## Discrete structures

- [[Truth Table Generator]] — for a formula such as (p ∧ q) → ¬r print every combination of values; check whether it is a tautology and whether two formulas are equivalent. First write the formula as a method, later parse it from a string.
	- Concepts: [[Truth Table|truth tables]], [[Tautology|tautologies]], [[Logical Equivalence|logical equivalence]]
	- Lectures: [[2026-10-05 - Propositional Logic - 1]], [[2026-10-19 - Valid Arguments and Inference Rules - 3]]; exercises [[Sources/discrete_structures/photoNotes/vaje/vaja1.pdf|vaja1]]
	- Book: [[Sources/discrete_structures/ds.pdf#page=9|Diskretne strukture]] (G. Fijavž), ch. 1 *Izjavni račun*, 1.1–1.5
- [[Normal Form Builder]] — build the full DNF and CNF automatically from a truth table.
	- Concepts: [[Disjunctive Normal Form]], [[Conjunctive Normal Form]], [[Functional Completeness|functional completeness]]
	- Lecture: [[2026-10-12 - Normal Forms and Complete Sets of Connectives - 2]]; exercises [[Sources/discrete_structures/photoNotes/vaje/vaje 2.pdf|vaja 2]]
	- Book: [[Sources/discrete_structures/ds.pdf#page=23|Diskretne strukture]] (G. Fijavž), 1.6 *Normalni obliki in polni nabori izjavnih veznikov*, p. 23

## Introduction to Digital Circuits

- [[Logic Gate Simulator]] — write methods `and`, `or`, `not`, `nand` and build from them a half adder, a full adder and finally an 8-bit adder. Shows how a computer adds numbers using nothing but gates.
	- Concepts: [[Logic Gate|logic gates]], [[Boolean Algebra|Boolean algebra]], [[Exclusive Or|exclusive or]], [[Sheffer Stroke|Sheffer stroke]] (NAND alone is functionally complete)
	- Lectures: [[2026-10-11 - Boolean Algebra - 1]], [[2026-10-29 - Functionally Complete Systems and Closed Classes - 4]]; exercises [[Sources/introduction_to_digital_circuits/vaje/vaja1/vaje 1.pdf|vaje 1]]
	- Book: [[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=11|ODV skripta]], *Boolova algebra in preklopne funkcije*, p. 11; bit operators in Java: [[Sources/programming_1/knjiga_koncna.pdf#page=108|Java od začetka]], 3.12 *Delo z biti*
- [[Veitch Diagram Minimiser]] — for a function of four variables print the Veitch diagram and find the groups of ones. Harder.
	- Concepts: [[Veitch Diagram|Veitch diagrams]], [[Switching Function|switching functions]], [[Minterm|minterms]], [[Prime Implicant|prime implicants]]
	- Lectures: [[2026-10-22 - Veitch Diagrams, Shannon Expansion and Decomposition - 3]], [[2026-11-05 - Minimisation of Switching Functions - 5]]; exercises [[Sources/introduction_to_digital_circuits/vaje/vaja3/vaje 3.pdf|vaje 3]]
	- Book: [[Sources/introduction_to_digital_circuits/ODV_skripta.pdf#page=33|ODV skripta]], 5.1 minimal forms and 5.2 *Veitchev postopek minimizacije*, pp. 33–36

## Programming 1

- [[Sorting Algorithms Comparison]] — implement several sorting algorithms and count comparisons on 10, 100 and 10 000 elements; see how fast a slow algorithm becomes useless.
	- Concepts: [[Insertion Sort|insertion sort]], [[Binary Search|binary search]], [[Time Complexity|time complexity]], [[Array|arrays]]
	- Lecture: [[2026-11-05 - Arrays, Searching and Sorting - 5]]
	- Book: [[Sources/programming_1/knjiga_koncna.pdf#page=152|Java od začetka]] (L. Fürst), 5.8 *Urejanje tabel*; slides [[Sources/programming_1/prosojnice/05_tabele_h.pdf|05 Tabele]], pp. 19–34
- [[Game of Life]] — a grid of cells in a 2D array that live or die depending on their neighbours. Simple rules, interesting behaviour, great practice with arrays.
	- Concepts: [[Array|arrays]], [[Nested Loop|nested loops]]
	- Lecture: [[2026-11-05 - Arrays, Searching and Sorting - 5]]
	- Book: [[Sources/programming_1/knjiga_koncna.pdf#page=162|Java od začetka]], 5.11 *Dvodimenzionalne tabele*
- [[Recursion Playground]] — Towers of Hanoi, and drawing the Sierpiński triangle as an SVG.
	- Concepts: [[Recursion|recursion]], [[Method|methods]]
	- Lecture: [[2026-10-29 - Methods and Recursion - 4]]; exercises [[2026-11-02 - Exercises for Methods and Recursion - 4]]
	- Book: [[Sources/programming_1/knjiga_koncna.pdf#page=131|Java od začetka]], 4.5 *Rekurzija*
