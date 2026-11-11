---
type: "[[Concepts]]"
status: developed
aliases:
  - Zanka do
  - do-while
  - Do loop
---

# Do-while Loop

## Definition

The `do` loop runs its body first and checks the condition after it:

```java
do {
    stavki
} while (pogoj);
```

- The statements run.
- If the condition is met, the process repeats (the statements run again and the condition is checked again).
- Otherwise the program continues with the statement after the loop.

**The statements always run at least once.** Note the semicolon after `while (pogoj)`.

## Explanation

- Use it when something must happen before it can be checked — typically reading input and repeating until it is correct.
- Compared with a [[While Loop|while loop]], it avoids writing the first read twice (once before the loop and once inside it).
- **Scope trap:** the body is a [[Block|block]], so a variable declared inside it does **not** exist in the condition. Declare it before the loop:

```java
int poskus = 0;
do {
    poskus = sc.nextInt();
} while (izbranoStevilo != poskus);
```

  Writing `int poskus = sc.nextInt();` inside the body is a compile error ([[Variable Scope|scope]]).
- Like `while`, use it when the number of steps is not known in advance; a [[For Loop|for loop]] is not suitable for guessing, because there is no counter.

## Examples

The question about the universe — `while` vs. `do` (Programming 2):

```java
// while: the question has to be written twice
System.out.print("Vnesi odgovor na vprasanje o ...");
int odgovor = sc.nextInt();
while (odgovor != 42) {
    System.out.print("Vnesi odgovor na vprasanje o ...");
    odgovor = sc.nextInt();
}
```

```java
// do: the question is written once
int odgovor;
do {
    System.out.print("Vnesi odgovor na vprasanje o ...");
    odgovor = sc.nextInt();
} while (odgovor != 42);
```

Guessing a random number (Programming 3): the loop repeats `while (izbranoStevilo != poskus)`; the number of guesses is not known in advance.

## Connections

- [[2026-10-15 - Control Structures - 2]] — `do` loop, the universe example (Programming 1)
- [[2026-10-22 - Loop Examples, break and switch - 3]] — guessing a number, scope of variables in the body (Programming 1)
- [[2026-10-26 - Exercises for Control Structures - 3]] — lab exercises (Programming 1)
- [[2026-11-09 - Exercises for Arrays, Searching and Sorting - 5]] — lab exercises (Programming 1)
- [[While Loop]], [[For Loop]], [[Variable Scope]], [[Block]]

## Sources

- `programming_1/prosojnice/03_krmilniKonstrukti_h.pdf` (L. Fürst), slides 32–33
