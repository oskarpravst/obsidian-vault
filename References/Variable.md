---
type: "[[Concepts]]"
status: developed
aliases:
  - Spremenljivka
  - Spremenljivke
---

# Variable

## Definition

A **variable** (*spremenljivka*) is a named place in memory that has a **type** and stores a **value** of that type.

```java
int a;        // declaration (deklaracija): name and type, no value yet
int b = 3;    // initialization (inicializacija): the first value
b = 1;        // assignment (prirejanje): a new value
```

## Explanation

- The **type** decides which values the variable can hold and which operations are allowed: `byte`, `short`, `int`, `long`, `float`, `double`, `char`, `boolean`, `String`, arrays, …
- **Always initialize a variable before using it.** Java refuses to compile a read of a variable that might not have a value.
- A value of a wider type cannot be assigned to a narrower one without a cast (`long` → `int`), which can cause [[Integer Overflow|integer overflow]].
- A variable exists only in the [[Block|block]] where it was declared ([[Variable Scope|scope]]). [[Parameter|Parameters]] and local variables of a [[Method|method]] exist only inside the method.
- Assignment is an expression with a value, so `a = b = 5` works (assignment is right associative).

## Examples

**Overflow** (Programming 1, lecture 1): `int c = 3000000000L;` gives `incompatible types: possible lossy conversion from long to int`: a `long` cannot be put into an `int`.

**Scope in a `do` loop** (lecture 3): `poskus` must be declared before the loop, because the loop condition cannot see variables declared in the body.

## Connections

- [[2026-09-22 - Introduction to Academic Studies - 0]] — adding variables as a stage of a program (Programming 1)
- [[2026-10-08 - Introduction to programming - 1]] — declaration, initialization, assignment, types (Programming 1)
- [[Variable Scope]], [[Block]], [[Integer Overflow]], [[Parameter]], [[Array]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/01_02_uvod_h.pdf|01–02 Uvod]] (Luka Fürst)
