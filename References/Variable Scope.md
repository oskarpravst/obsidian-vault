---
type: "[[Concepts]]"
status: developed
aliases:
  - Doseg spremenljivke
  - Scope
  - Local variable
  - Lokalna spremenljivka
---

# Variable Scope

## Definition

The **scope** of a variable is the part of the program where it can be used: from its declaration to the end of the [[Block|block]] `{ }` in which it was declared.

## Explanation

- Inside its scope a name can be declared only once. In a nested block the same name cannot be declared again.
- **Local variables** and [[Parameter|parameters]] of a [[Method|method]] exist only while the method runs, and only inside it. Another method (including `main`) cannot see them; it must receive the value through `return`.
- A variable that is needed **after** a block, or in a loop condition, must be declared **before** the block.
- The loop variable of `for (int i = ...; ...)` exists only in that loop.
- The same name in two different methods means two different variables. That is why a parameter may have the same name as the argument.

## Examples

**`do` loop** (Programming 1, lecture 3): `do { int poskus = sc.nextInt(); } while (izbranoStevilo != poskus);` is a compile error, because `poskus` does not exist in the condition. Declare `int poskus = 0;` before the loop.

**`switch`** (lecture 3): a variable declared in one `case` lives until the end of the whole `switch`, so declaring `int b` in two cases gives `error: variable b is already defined`.

**Amicable numbers** (lecture 4): `kandidat` is a local variable of `imaPrijatelja`, so `System.out.println(kandidat)` in `main` does not work.

## Connections

- [[2026-10-22 - Loop Examples, break and switch - 3]] — `do` loop and `switch` (Programming 1)
- [[2026-10-29 - Methods and Recursion - 4]] — local variables of a method (Programming 1)
- [[Block]], [[Variable]], [[Method]], [[Parameter]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/03_krmilniKonstrukti_h.pdf|03 Krmilni konstrukti]], [[Sources/programming_1/prosojnice/04_metode_h.pdf|04 Metode]] (Luka Fürst)
