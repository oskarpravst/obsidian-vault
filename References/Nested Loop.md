---
type: "[[Concepts]]"
status: developed
aliases:
  - Gnezdena zanka
  - Gnezdene zanke
---

# Nested Loop

## Definition

A **nested loop** (*gnezdena zanka*) is a loop inside the body of another loop. For every iteration of the outer loop the inner loop runs completely.

## Explanation

- Typical pattern: the **outer** loop goes over rows or candidates, the **inner** loop does the work for one of them.
- If the outer loop runs $n$ times and the inner $m$ times, the inner body runs $n \cdot m$ times. Two nested loops over $n$ give $O(n^2)$ ([[Time Complexity|time complexity]]).
- The inner loop's counter often depends on the outer one (e.g. row `i` has `i` stars).
- `break` inside the inner loop leaves **only the inner loop**.

## Examples

**Multiplication table** (Programming 1, lecture 3): `i` is the row, `j` the column, and `printf` aligns the numbers.

**Prime numbers** (lecture 3): the outer loop goes over candidates, the inner loop over possible divisors.

**Piramida** (lab exercises, week 3): for each row, one inner [[For Loop|for loop]] prints spaces and a second one prints stars.

**Kleptomanka Anka** (lab exercises, week 3): three nested `for` loops list all combinations `a-b-c` of a lock.

## Connections

- [[2026-10-22 - Loop Examples, break and switch - 3]] — prime numbers, multiplication table (Programming 1)
- [[2026-10-26 - Exercises for Control Structures - 3]] — Piramida, Kleptomanka Anka (Programming 1)
- [[For Loop]], [[While Loop]], [[Time Complexity]], [[Prime Number]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/03_krmilniKonstrukti_h.pdf|03 Krmilni konstrukti]] (Luka Fürst)
