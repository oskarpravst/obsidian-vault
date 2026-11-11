---
type: "[[Concepts]]"
status: developed
aliases:
  - Parametri
  - Argument
  - Argumenti
---

# Parameter

## Definition

A **parameter** (*parameter*) is a variable in the header of a [[Method|method]]. An **argument** (*argument*) is the value given in the call. **Arguments go into the parameters**, in order.

```java
public static void metoda(T1 p1, T2 p2) { ... }   // parameters
metoda(a1, a2);                                    // arguments
```

## Explanation

- The parameter gets a **copy** of the argument's value. Changing the parameter inside the method does not change the caller's variable.
- The argument types must be **assignable** to the parameter types: an `int` can go into a `long` parameter, but a `long` cannot go into an `int` parameter.
- A parameter may have the same name as the argument, because they are two separate variables.
- Parameters are local variables of the method ([[Variable Scope|scope]]).
- Methods with the same name but different parameter lists are different methods ([[Method Overloading|overloading]]).
- For an [[Array|array]] the copied value is a reference to the same array, so changing `t[i]` inside the method changes the caller's array.

## Examples

```java
public static void narisi(int n) { ... }

int a = 3;
narisi(a);    // 3 is copied into n
long b = 7;
narisi(b);    // compile error: long cannot be copied into int
```

**Plus** (Programming 1, lecture 4): the length of an arm `n` becomes a parameter, then a method gets several parameters.

## Connections

- [[2026-10-29 - Methods and Recursion - 4]] — parameters and arguments, copies, assignable types (Programming 1)
- [[2026-11-02 - Exercises for Methods and Recursion - 4]] — methods with parameters in the lab tasks (Programming 1)
- [[Method]], [[Return Statement]], [[Variable Scope]], [[Method Overloading]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/04_metode_h.pdf|04 Metode]] (Luka Fürst)
