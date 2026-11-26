---
type: "[[Courses]]"
course: "[[Calculus]]"
code:
university: FRI
semester: "1"
year: 1
professor: "[[Žiga Virk]]"
status: active
---

# Calculus

## Overview


## Questions

- [ ] 

Open questions from this course's lectures:

```query
path:Uni [course:"Calculus"] task-todo:/\[ \]\s+\S/
```

## Concepts

## Lectures

![[Lectures.base#Course]]

## Exam

1st colloquium (*1. kolokvij*): **2026-12-02**. Recent papers have 4 problems × 25 points in 90 min, with 1 A4 formula sheet and no calculator. Scope confirmed in [[2026-11-25 - Partial Derivatives, Directional Derivative, Gradient and Gradient Descent - 8|lecture 8]]: everything up to what the exercises (*vaje*) cover in the week of 2026-11-23 (*na kolokviju vse do kar delamo ta teden na vajah*), not the lectures. Check the vaje of that week (vaje 7) for where it stops. The past papers agree: since 2019 they test complex numbers, sequences, series and continuity, and no derivatives except one tangent (2023).

### Topics

- Induction, absolute value, supremum and infimum — [[2026-10-11 - Numbers - 1]], vaje 1
- Complex numbers: Cartesian form, equations with $\bar z$, $\operatorname{Re}$, $\operatorname{Im}$, $|z|$, regions in the plane — [[2026-10-11 - Numbers - 1]], vaje 2
- Polar form, De Moivre, $n$-th roots, polynomials with real coefficients — [[2026-10-14 - Polar Form of Complex Numbers - 2]], vaje 3
- Sequences: monotone, bounded, $\varepsilon$–$N$, computing limits, $e$-type limits — [[2026-10-21 - Spectral Decomposition and Sequences - 3]], [[2026-10-28 - Limits of Sequences - 4]], vaje 3–4
- Recursive sequences: induction + monotone convergence theorem, fixed points — [[2026-10-28 - Limits of Sequences - 4]], vaje 5
- Series: geometric, telescoping, comparison, ratio, root and Leibniz test, absolute convergence — [[2026-11-04 - Series and Convergence Tests - 5]], vaje 5
- Functions: domain, injectivity, inverse, limits ($\frac{\sin x}{x}$), continuity with parameters — [[2026-11-11 - Limits of Functions, Continuity and Zeros of Continuous Functions - 6]]

### Typical problems

Based on the 1st colloquia 2019–2023 (5 papers, 20 problems). Older papers (2011–2018) follow the same pattern but also have tangents and functions of two variables, which are now in the 2nd colloquium (only practise the tangent ones if derivatives are covered by then). Each recent paper has:

1. **Complex numbers** (5/5): (a) an equation with $\bar z$, $\operatorname{Re}$, $\operatorname{Im}$ or $|z|$, solved with $z = x + iy$ (2020, 2021, 2023) or by factoring (2022); (b) all roots of $w^n = c$ in polar form, drawn as a regular $n$-gon (2019, 2020, 2021, 2022).
2. **Recursive sequence** (3/5 in a row, 2021–2023; 2019 an induction identity instead): prove by induction that it is monotone and bounded, solve $a = f(a)$ for the candidates and pick the right limit.
3. **Series** (5/5): geometric series with a parameter $x$ → where it converges, its sum, and $x$ for a given sum (2021, 2022, 2023); ratio / root test with $n^2$, $n^n$, $n!$ (2021, 2022, 2023); telescoping series (2019); series built from a sequence with an $e$-type limit (2020).
4. **Function** (5/5): constants $a, b$ for continuity with $\frac{\sin(ax)}{x}$, arctan and log limits (2019, 2020, 2021, 2022, 2023); domain, injectivity (an even function is not injective), inverse on a restricted domain (2021, 2022, 2023); sketch; extending $f$ by a constant outside $D_f$ (2022, 2023).

Most likely in 2026: the same four problems.

### Past exams

- 1st colloquia: [[Sources/calculus/kolokvijiIzpiti/kolokvij1/2023-24/oma-k1-2324.pdf|2023/24]] (with solutions), [[Sources/calculus/kolokvijiIzpiti/kolokvij1/2022-23/oma-k1-2223-resitve.pdf|2022/23]] (with solutions), [[Sources/calculus/kolokvijiIzpiti/kolokvij1/2021-22/oma-k1-2121.pdf|2021/22]], [[Sources/calculus/kolokvijiIzpiti/kolokvij1/2020-21/oma-k1-2021.pdf|2020/21]] ([[Sources/calculus/kolokvijiIzpiti/kolokvij1/2020-21/oma-k1-2021-resitve.pdf|solutions]]), [[Sources/calculus/kolokvijiIzpiti/kolokvij1/2019-20/oma-k1-1920.pdf|2019/20]], [[Sources/calculus/kolokvijiIzpiti/kolokvij1/2018-19/oma-k1-1819.pdf|2018/19]], [[Sources/calculus/kolokvijiIzpiti/kolokvij1/2017-18/oma-k1-1718.pdf|2017/18]], [[Sources/calculus/kolokvijiIzpiti/kolokvij1/2016-17/oma-k1-1617.pdf|2016/17]], [[Sources/calculus/kolokvijiIzpiti/kolokvij1/2015-16/oma-k1-1516.pdf|2015/16]], [[Sources/calculus/kolokvijiIzpiti/kolokvij1/2014-15/oma-k1-1415.pdf|2014/15]], [[Sources/calculus/kolokvijiIzpiti/kolokvij1/2013-14/oma-k1-1314.pdf|2013/14]], [[Sources/calculus/kolokvijiIzpiti/kolokvij1/2012-13/oma-k1-1213.pdf|2012/13]], [[Sources/calculus/kolokvijiIzpiti/kolokvij1/2011-12/oma-k1-1112.pdf|2011/12]] (pages 1–2 are Calculus, the rest is Discrete structures)
- Written exams with colloquium-1 problems (*računski izpiti*): [[Sources/calculus/kolokvijiIzpiti/racunski_izpit1/2021-22/oma-ri1-2122.pdf|ri1 2021/22]] (#1 complex, #2 series), [[Sources/calculus/kolokvijiIzpiti/racunski_izpit1/2023-24/oma-ri1-2324.pdf|ri1 2023/24]] (#1 sequence), [[Sources/calculus/kolokvijiIzpiti/racunski_izpit1/2020-21/oma-pred-2021.pdf|predrok 2020/21]] (#1 recursive sequence, graphically), [[Sources/calculus/kolokvijiIzpiti/racunski_izpit2/2023-24/oma-ri2-2324.pdf|ri2 2023/24]] (#1 complex, #2 recursive sequence, with solutions), [[Sources/calculus/kolokvijiIzpiti/racunski_izpit2/2021-22/oma-ri2-2122.pdf|ri2 2021/22]] (#1 recursive sequence), [[Sources/calculus/kolokvijiIzpiti/racunski_izpit2/2020-21/oma-ri2-2021.pdf|ri2 2020/21]] (#1 complex, #2 recursive sequence), [[Sources/calculus/kolokvijiIzpiti/racunski_izpit3/2020-21/oma-ri3-2021.pdf|ri3 2020/21]] (#1 induction, #2 continuity), [[Sources/calculus/kolokvijiIzpiti/racunski_izpit3/2021-22/oma-ri3-2122.pdf|ri3 2021/22]] (#1 induction, #2 continuity), [[Sources/calculus/kolokvijiIzpiti/racunski_izpit3/2023-24/oma-ri3-2324.pdf|ri3 2023/24]] (#1 complex)
- Problem collection: [[Sources/calculus/zbirka_oma.pdf|zbirka OMA]]

### Study plan — 1st colloquium

Mock exams are kept unseen until the end: **2022/23** and **2023/24** (both have solutions in the file).

Until 11-24 physics comes first ([[Physics]] colloquium on 11-25), so Calculus gets about 45–60 min a day. From 11-26 Calculus is the main subject (2–3 h a day). **Core** is the daily minimum; **Extra** only when there is time left. "K1 2021/22 #1a" means 1st colloquium 2021/22, problem 1a.

- [ ] Tue 11-17 — Complex numbers I (Cartesian form)
	- Core: notes L1 (complex part); redo vaje 2 (regions, equations with $\bar z$); K1 2020/21 #1a; K1 2021/22 #1a
	- Extra: K1 2013/14 #1; ri2 2023/24 #1
- [ ] Wed 11-18 — Lecture 7 (go through it the same evening); complex numbers II (roots)
	- Core: notes L2; redo vaje 3 (roots $z^3 = \ldots$); K1 2019/20 #2b; K1 2018/19 #1b
	- Extra: K1 2014/15 #1; K1 2012/13 #2
- [ ] Thu 11-19 — Complex numbers III (mixed)
	- Core: K1 2020/21 #1b; K1 2021/22 #1b; K1 2017/18 #1; K1 2015/16 #1
	- Extra: ri1 2021/22 #1; ri2 2020/21 #1; vaje 3 (polynomial with real coefficients)
- [ ] Fri 11-20 — Induction (light day: physics mock 1)
	- Core: redo vaje 1 (sums, divisibility, $n! > 2^n$); K1 2019/20 #1
	- Extra: ri3 2020/21 #1; ri3 2021/22 #1
- [ ] Sat 11-21 — Recursive sequences I
	- Core: notes L3–L4 (monotone convergence theorem); redo vaje 5 (first problem, $a_{n+1} = \frac{a_n^2 + 4}{5}$); K1 2017/18 #2; K1 2016/17 #2
	- Extra: K1 2015/16 #2; predrok 2020/21 #1
- [ ] Sun 11-22 — Recursive sequences II (light day: physics mock 2)
	- Core: K1 2021/22 #2; K1 2014/15 #2
	- Extra: K1 2013/14 #2; K1 2011/12 #3; ri2 2023/24 #2 (with solution)
- [ ] Mon 11-23 — Limits of sequences
	- Core: redo vaje 4 (rational limits, $\sqrt{n+1} - \sqrt{n}$, $e$-type limits); K1 2020/21 #2a; K1 2012/13 #1a
	- Extra: ri1 2023/24 #1; K1 2018/19 #2
- [ ] Tue 11-24 — No Calculus (physics tomorrow)
	- Extra: 20 min, start the formula sheet (complex numbers, sequences)
- [ ] Wed 11-25 — Physics colloquium; Lecture 8 in the evening if there is energy
- [ ] Thu 11-26 — Series
	- Core: notes L5; redo vaje 5 (telescoping, geometric series) and vaje 6; K1 2021/22 #3; K1 2019/20 #3; K1 2020/21 #2b
	- Extra: ri1 2021/22 #2; K1 2011/12 #4; K1 2012/13 #1b–c
- [ ] Fri 11-27 — Functions: continuity, injectivity, inverse
	- Core: notes L6–L7; redo vaje 6–7; K1 2021/22 #4; K1 2020/21 #3; K1 2019/20 #4; K1 2017/18 #3
	- Extra: K1 2016/17 #3; K1 2015/16 #3; K1 2012/13 #4; ri3 2020/21 #2; ri3 2021/22 #2; tangents (K1 2016/17 #4, K1 2014/15 #3) only if derivatives are included
- [ ] Sat 11-28 — **Mock 1: 2022/23**, 90 min, then mark it with the solutions
- [ ] Sun 11-29 — Fix the mistakes from mock 1; weak topics; finish the formula sheet (1 A4)
- [ ] Mon 11-30 — **Mock 2: 2023/24**, 90 min, then mark it with the solutions
- [ ] Tue 12-01 — Fix the mistakes from mock 2; redo one problem of each of the 4 types; sleep

## Readings

## Assignments

- [ ]

## Projects

## People

## Related

## Notes
