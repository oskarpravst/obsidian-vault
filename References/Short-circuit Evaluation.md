---
type: "[[Concepts]]"
status: developed
aliases:
  - Kratkostično izvajanje
  - Short-circuiting
---

# Short-circuit Evaluation

## Definition

**Short-circuit evaluation** (*kratkostično izvajanje*): Java evaluates `&&` and `||` from left to right and stops as soon as the result is known.

- `p && q`: if `p` is `false`, `q` is not evaluated (`false && …` is already `false`)
- `p || q`: if `p` is `true`, `q` is not evaluated (`true || …` is already `true`)

## Explanation

- It is not only a speed-up: it lets the left condition **protect** the right one. The order of the conditions matters.
- Typical guard: check the index before reading the array, `i < t.length && t[i] < x`. If `i == t.length`, `t[i]` is never read, so there is no `ArrayIndexOutOfBoundsException`.
- Another guard: `n != 0 && x / n > 2` never divides by zero.
- It is the programming form of the logical facts $0 \land q = 0$ and $1 \lor q = 1$ ([[Boolean Algebra]]).

## Examples

**Searching in a sorted array** (Programming 1, lecture 5):

```java
while (i < t.length && t[i] < x) {
    i++;
}
return (i < t.length && t[i] == x) ? i : -1;
```

**Lab notes** (week 5): "a property of Java: `true` or something, `false` and something".

## Connections

- [[2026-10-15 - Control Structures - 2]] — logical operators and short-circuit evaluation (Programming 1)
- [[2026-11-05 - Arrays, Searching and Sorting - 5]] — the guard `i < t.length && t[i] < x` (Programming 1)
- [[2026-11-09 - Exercises for Arrays, Searching and Sorting - 5]] — from the lab notes (Programming 1)
- [[Boolean]], [[Boolean Algebra]], [[Array]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/03_krmilniKonstrukti_h.pdf|03 Krmilni konstrukti]] (Luka Fürst)
