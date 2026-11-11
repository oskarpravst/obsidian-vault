---
type: "[[Concepts]]"
status: developed
aliases:
  - Metoda
  - Metode
  - Function
  - Funkcija
---

# Method

## Definition

A **method** (*metoda*) is a piece of code with its own name. We **call** it by name, and its code runs. It can take [[Parameter|parameters]] and [[Return Statement|return]] a value. In other languages it is called a **function** (*funkcija*).

```java
public static T ime(T1 p1, T2 p2, ..., Tn pn) {   // header: return type, name, parameters
    ...                                          // body
}
```

## Explanation

- **Why:** code that would be repeated is written once and reused. A problem is split into subproblems, each solved by its own method, with `main` calling them.
- `main` is also a method, the main method (*glavna metoda*) where execution starts.
- **Arguments go into the parameters.** Each parameter is a **copy** of its argument, so changing a parameter does not change the caller's variable. The argument types must be assignable to the parameter types.
- `void` methods return nothing. Other methods state the type `T` of the returned value in the header and end with `return izraz;`.
- **Local variables** of a method exist only inside it ([[Variable Scope|scope]]). `main` cannot see them.
- A method can call itself: [[Recursion|recursion]].
- Several methods can share a name if their parameter lists differ: [[Method Overloading|method overloading]].

## Examples

**Plus** (Programming 1, lecture 4): a cross of `+`. The repeated vertical stroke becomes one method `navpicniKrak`, which is called twice.

**Copy of an argument** (lecture 4):

```java
public static void main(String[] args) {
    int a = 42;
    metoda(a);
    System.out.println(a);   // 42
}

public static void metoda(int a) {
    a++;
    System.out.println(a);   // 43
}
```

**Lab exercises** (week 4): Collatzovo zaporedje uses a method that returns the length of one Collatz sequence; NZD computes the greatest common divisor with a recursive method.

## Connections

- [[2026-10-29 - Methods and Recursion - 4]] — methods, parameters and arguments, `return`, recursion (Programming 1)
- [[2026-11-02 - Exercises for Methods and Recursion - 4]] — splitting tasks into methods (Programming 1)
- [[2026-11-05 - Arrays, Searching and Sorting - 5]] — methods that take arrays: `izpis`, `poisci`, `uredi` (Programming 1)
- [[2026-11-09 - Exercises for Arrays, Searching and Sorting - 5]] — lab exercises with methods (Programming 1)
- [[Parameter]], [[Return Statement]], [[Variable Scope]], [[Recursion]], [[Method Overloading]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/04_metode_h.pdf|04 Metode]] (Luka Fürst)
