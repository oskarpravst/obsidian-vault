---
type: "[[Concepts]]"
status: developed
aliases:
  - return
  - Stavek return
---

# Return Statement

## Definition

`return izraz;` ends the execution of a [[Method|method]] and gives the value of `izraz` back to the caller (*klicatelj*). The method call is replaced by the returned value.

## Explanation

- Instead of `void`, the header contains the type `T` of the returned value. The value of `izraz` must be assignable to `T`.
- The caller can store the result in a variable whose type `T` is assignable to: `int o = obseg(3, 4);`.
- In a `void` method `return;` (without a value) leaves the method early. `break` only works in a loop or `switch`.
- `return` leaves the method immediately, even from inside a loop. A search can return the index as soon as it finds the element.
- A method can return a [[Boolean|boolean]] expression directly: `return a == b;`.

## Examples

**Perimeter** (Programming 1, lecture 4): `obseg(a, b)` returns `2 * (a + b)`.

**Searching** (lecture 5): `dvojiskoIskanje` returns `s` as soon as `t[s] == x`, and `-1` after the loop if the element is not there.

## Connections

- [[2026-10-29 - Methods and Recursion - 4]] — `return`, returned type, `return;` in `void` methods (Programming 1)
- [[2026-11-02 - Exercises for Methods and Recursion - 4]] — methods that return the length of a Collatz sequence and the GCD (Programming 1)
- [[Method]], [[Parameter]], [[Binary Search]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/04_metode_h.pdf|04 Metode]] (Luka Fürst)
