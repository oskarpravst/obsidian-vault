---
type: "[[Concepts]]"
status: developed
aliases:
  - Zanka for
---

# For Loop

## Definition

The `for` loop repeats its body while a condition holds, and keeps the counter handling in one line:

```java
for (inicializacija; pogoj; posodobitev) {
    stavki
}
```

It is a shorthand for a `while` loop:

```java
inicializacija;
while (pogoj) {
    stavki
    posodobitev;
}
```

## Explanation

Order of execution: initialisation (once) → check the condition → body → update → check the condition → … until the condition is `false`.

**Scope exception:** a variable declared in the initialisation exists only until the end of the loop body — normally a variable exists until the end of its block.

**`for` vs. `while`/`do`** (slides, p. 42):

- `for` — walking through an interval; the number of steps is known in advance.
- `while`/`do` — repeat until a condition is met; the number of steps is not known in advance.

**Common mistake:** the update must change the variable. `stevilo + 1` only computes a value and does not compile ("not a statement"); use `stevilo++` or `stevilo += 1`.

## Examples

Sequence from `a` to `b` (inclusive):

```java
for (int stevilo = a; stevilo <= b; stevilo++) {
    System.out.println(stevilo);
}
```

The same with `while`:

```java
int stevilo = a;
while (stevilo <= b) {
    System.out.println(stevilo);
    stevilo++;
}
```

Capital letters of the English alphabet — `'A'` to `'Z'` have consecutive ASCII codes:

```java
for (char crka = 'A'; crka <= 'Z'; crka++) {
    System.out.print(crka);
}
// ABCDEFGHIJKLMNOPQRSTUVWXYZ
```

## Connections

- [[2026-09-22 - Introduction to Academic Studies - 0]] — for loops in the first problem-solving example (Programming 1)
- [[2026-10-15 - Control Structures - 2]] — `for` loop, sequence example (Programming 1)
- [[2026-10-19 - Exercises for Control Structures - 2]] — a `for` loop over an interval (Programming 1)
- [[2026-10-22 - Loop Examples, break and switch - 3]] — a `for` loop over characters (Programming 1)
- [[2026-10-26 - Exercises for Control Structures - 3]] — nested `for` loops in Piramida (Programming 1)
- [[2026-11-02 - Exercises for Methods and Recursion - 4]] — lab exercises (Programming 1)
- [[2026-11-09 - Exercises for Arrays, Searching and Sorting - 5]] — loops over arrays (Programming 1)
- [[While Loop]], [[Do-while Loop]], [[Infinite Loop]]

## Sources

- `programming_1/prosojnice/03_krmilniKonstrukti_h.pdf` (L. Fürst), slides 39–43
