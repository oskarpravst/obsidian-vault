---
type: "[[Concepts]]"
status: developed
aliases:
  - Collatzova domneva
  - Collatzovo zaporedje
  - Collatz sequence
  - 3n + 1 problem
---

# Collatz Conjecture

## Definition

The **Collatz sequence** is the recursive [[Sequence|sequence]]

$$a_{n+1} = \begin{cases} \dfrac{a_n}{2}, & a_n \text{ even (*sodo*)} \\[2mm] 3a_n + 1, & a_n \text{ odd (*liho*)} \end{cases}$$

The **Collatz conjecture** (*Collatzova domneva*) claims that for every starting value $a_1 \in \mathbb{N}$ the sequence eventually reaches $1$ (and then cycles $1 \to 4 \to 2 \to 1$).

## Explanation

- The rule is trivial, but nobody has proved the conjecture. It has been checked by computer for very large starting values, but checking examples is not a proof.
- It is a good example of the difference between **testing** (a program) and **proving** (mathematics).
- In programming it is a typical [[While Loop|while loop]] task: we do not know in advance how many steps are needed.

## Examples

Starting at $6$: $6, 3, 10, 5, 16, 8, 4, 2, 1$, a sequence of length 9 (counting the start and the final 1).

**Lab exercise** (Programming 1, week 4): for $a \le n \le b$, find the $n$ with the longest Collatz sequence. For `10 20` the answer is $18$ with length $21$. The solution uses a [[Method|method]] that returns the length of one sequence.

## Connections

- [[2026-10-21 - Spectral Decomposition and Sequences - 3]] — example of a recursive sequence (Calculus)
- [[2026-11-02 - Exercises for Methods and Recursion - 4]] — task *Collatzovo zaporedje* (Programming 1)
- [[Sequence]], [[Method]], [[While Loop]]

## Sources

- [Collatz conjecture — Wikipedia](https://en.wikipedia.org/wiki/Collatz_conjecture)
