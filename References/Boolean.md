---
type: "[[Concepts]]"
status: developed
aliases:
  - boolean
  - Logični tip
  - Logični izraz
---

# Boolean

## Definition

`boolean` is the Java type of **logical values**: `true` or `false`. A **logical expression** (*logični izraz*) such as `3 < 4` has a value of this type. The name comes from George Boole and [[Boolean Algebra|Boolean algebra]].

## Explanation

- Every condition in `if`, `while`, `do` and `for` must be of type `boolean`. Java does not accept `0` and `1` as conditions.
- **Comparison:** `==` compares, `=` assigns. `3 = 3` is a compile error.
- **Logical operators:** `&&` (and), `||` (or), `!` (not). `&&` has precedence over `||`. They use [[Short-circuit Evaluation|short-circuit evaluation]].
- A `boolean` variable can be used as a **flag** that remembers whether something happened, e.g. `prastevilo` in the prime numbers program.
- A method can return the value of a logical expression directly, `return a == b;`, instead of `if (a == b) return true; else return false;`.
- In a new `boolean[]` array all elements are `false` (the sieve of Eratosthenes relies on this).
- `boolean` cannot be used as the expression of a `switch`.

## Examples

```java
boolean b = 4 > 5;   // false
boolean c = !b;      // true
3 == 3.0             // true: int is converted to double
```

## Connections

- [[2026-10-15 - Control Structures - 2]] — logical expressions, `boolean`, logical operators (Programming 1)
- [[2026-10-22 - Loop Examples, break and switch - 3]] — flag `prastevilo` (Programming 1)
- [[2026-10-29 - Methods and Recursion - 4]] — returning a logical expression directly (Programming 1)
- [[Boolean Algebra]], [[Propositional Logic]], [[Short-circuit Evaluation]], [[Conditional Statement]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/03_krmilniKonstrukti_h.pdf|03 Krmilni konstrukti]] (Luka Fürst)
