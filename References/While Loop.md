---
type: "[[Concepts]]"
status: developed
aliases:
  - Zanka while
  - while
---

# While Loop

## Definition

The `while` loop (*dokler*) repeats its body as long as the condition is `true`:

```java
while (pogoj) {
    stavki
}
```

- If the condition is met, the statements run and the condition is checked again.
- Otherwise the program continues with the statement after the loop.

The condition is checked **before** each run, so the body may run zero times.

## Explanation

- Use `while` when you **repeat until a condition is met** and do not know the number of steps in advance; for walking over an interval with a known number of steps use a [[For Loop|for loop]].
- Something in the body must eventually make the condition `false`. If the variables in the condition never change, the result is an [[Infinite Loop|infinite loop]] (*neskončna zanka*); `Ctrl + C` stops it.
- Conditions can be combined with `&&` and `||` — the same connectives as in [[Propositional Logic|propositional logic]]. "Stop when 5 numbers are read **or** the sum exceeds 42" becomes "continue while fewer than 5 are read **and** the sum is at most 42" ([[De Morgan's Laws|De Morgan]]).
- `sc.hasNextInt()` is `true` exactly when there is another number on the input, so `while (sc.hasNextInt())` reads until the input runs out (`Ctrl + D` when typing by hand).
- If the body must run at least once (e.g. ask before checking), a [[Do-while Loop|do-while loop]] is shorter.

## Examples

Running sum, stop after 5 inputs or when the sum exceeds 42 (Programming 2):

```java
int stVnosov = 0;
int vsota = 0;
while (stVnosov < 5 && vsota <= 42) {
    System.out.print("Vnesite število: ");
    int vnos = sc.nextInt();
    stVnosov = stVnosov + 1;
    vsota = vsota + vnos;
    System.out.println(vsota);
}
```

Sum of all numbers on the input (Programming 2):

```java
int vsota = 0;
while (sc.hasNextInt()) {
    int stevilo = sc.nextInt();
    vsota = vsota + stevilo;
}
System.out.println(vsota);
```

## Connections

- [[2026-10-15 - Control Structures - 2]] — `while` loop, running sums, `sc.hasNextInt()` (Programming 1)
- [[2026-10-19 - Exercises for Control Structures - 2]] — digits, walking; `while` instead of `for` (Programming 1)
- [[2026-10-22 - Loop Examples, break and switch - 3]] — `for` vs. `while`/`do` (Programming 1)
- [[2026-10-26 - Exercises for Control Structures - 3]] — reading until the input runs out (Programming 1)
- [[2026-11-02 - Exercises for Methods and Recursion - 4]] — lab exercises (Programming 1)
- [[2026-11-09 - Exercises for Arrays, Searching and Sorting - 5]] — lab exercises (Programming 1)
- [[For Loop]], [[Do-while Loop]], [[Infinite Loop]], [[Break Statement]]
- [[Propositional Logic]] — conditions with `&&`, `||`, `!` (Discrete structures)

## Sources

- `programming_1/prosojnice/03_krmilniKonstrukti_h.pdf` (L. Fürst), slides 18–28
