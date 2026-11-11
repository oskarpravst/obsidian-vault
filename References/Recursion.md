---
type: "[[Concepts]]"
status: developed
aliases:
  - Rekurzija
  - Recursive method
  - Rekurzivni klic
---

# Recursion

## Definition

**Recursion** (*rekurzija*) is when a [[Method|method]] calls itself (*rekurzivni klic*). Every recursive method needs a **base case** that is solved directly and a **recursive case** that reduces the problem to a smaller instance of itself.

## Explanation

- A **recurrence relation** (*rekurenčna enačba*) from mathematics translates directly into a recursive method. Base cases become `if` branches with a direct `return`; the recurrence becomes the recursive call.
- Without a base case (or if the problem does not get smaller) the calls never end and the program crashes with a `StackOverflowError`.
- Recursion is the programming twin of [[Mathematical Induction|mathematical induction]]: the base case is the base of the induction, and the recursive call trusts the "induction hypothesis" for smaller inputs.
- **It can be very slow** when the same subproblems are recomputed many times (Fibonacci). [[Memoization]] remembers results in an [[Array|array]] so that each one is computed once.
- Every recursion can also be written with a loop, e.g. the GCD with a [[While Loop|while loop]].

## Examples

**Fibonacci** (Programming 1, lecture 4):

$$F_n = \begin{cases} 0 & n = 0 \\ 1 & n = 1 \\ F_{n-2} + F_{n-1} & \text{otherwise} \end{cases}$$

The direct translation (`Fibonacci`) works but is very inefficient, because whole subtrees of calls repeat. Lecture 5 fixes it with memoization (`FibonacciMemo`). See [[Fibonacci Sequence]].

**Greatest common divisor** (lab exercises, week 4): `gcd` is the sheet's formula written as a recursive method, the [[Euclidean Algorithm|Euclidean algorithm]].

**Piramida v.3** (lab exercises, week 3): a recursive version of the pyramid, only for interest.

## Connections

- [[2026-10-26 - Exercises for Control Structures - 3]] — recursive Piramida v.3 (Programming 1)
- [[2026-10-29 - Methods and Recursion - 4]] — recursive call, Fibonacci (Programming 1)
- [[2026-11-02 - Exercises for Methods and Recursion - 4]] — recursive `gcd` (Programming 1)
- [[2026-11-05 - Arrays, Searching and Sorting - 5]] — Fibonacci with memoization (Programming 1)
- [[Method]], [[Fibonacci Sequence]], [[Memoization]], [[Mathematical Induction]], [[Euclidean Algorithm]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/04_metode_h.pdf|04 Metode]] (Luka Fürst); [[Sources/programming_1/prosojnice/05_tabele_h.pdf|05 Tabele]], Fibonacci with memoization pp. 38–42
