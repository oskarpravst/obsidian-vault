---
type: "[[Concepts]]"
status: developed
aliases:
  - Vennov diagram
  - Vennovi diagrami
---

# Venn Diagram

## Definition

A **Venn diagram** (*Vennov diagram*) draws each [[Set|set]] (or each logic variable) as a region, usually a circle, inside a rectangle that stands for the universal set. Every combination of "inside / outside" of the regions is one area of the picture.

## Explanation

- With $n$ regions in general position there are $2^n$ areas, including the area outside all circles.
- **In set theory** the areas show the results of $\cap$, $\cup$, $\setminus$, $+$ and the complement, and give intuition for set identities such as [[De Morgan's Laws|De Morgan's laws]]. A picture is not a proof: identities are proved with an arbitrary $x$.
- **In switching theory** each area is exactly one [[Minterm|minterm]]: inside the circle $x$ means $x$, outside means $\bar{x}$.
- For more than 3 variables circles no longer work well. The [[Veitch Diagram|Veitch diagram]] is the same idea arranged as a grid of $2^n$ cells.

## Examples

**2 variables** (Digital circuits 3): $x\bar{y}$, $xy$, $\bar{x}y$ and outside $\bar{x}\bar{y}$.

**3 variables** (Digital circuits 3): 7 areas inside the circles ($a\bar{b}\bar{c}$, $ab\bar{c}$, $\bar{a}b\bar{c}$, $abc$, $a\bar{b}c$, $\bar{a}bc$, $\bar{a}\bar{b}c$) and $\bar{a}\bar{b}\bar{c}$ outside.

**Set operations** (Discrete structures 5): intersection, union, difference and symmetric difference drawn as shaded areas of two circles, and the complement $A^c$ as everything in $S$ outside $A$.

## Connections

- [[2026-10-22 - Veitch Diagrams, Shannon Expansion and Decomposition - 3]] — the areas of a Venn diagram are the minterms (Digital circuits)
- [[2026-11-02 - Prenex Normal Form, Sets and Russell's Paradox - 5]] — drawings of set operations and the complement (Discrete structures)
- [[2026-11-09 - Set Equations, Cartesian Product and Relations - 6]] — set equations (Discrete structures)
- [[Set]], [[Minterm]], [[Veitch Diagram]], [[De Morgan's Laws]]

## Sources

- G. Fijavž, *Diskretne strukture* (FRI, 2015), 3.1–3.2 equality, inclusion and set operations: [[Sources/discrete_structures/ds.pdf#page=63|pp. 63–66]]
- [Venn diagram — Wikipedia](https://en.wikipedia.org/wiki/Venn_diagram)
