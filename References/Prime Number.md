---
type: "[[Concepts]]"
status: developed
aliases:
  - Praštevilo
  - Praštevila
  - Prime
---

# Prime Number

## Definition

A natural number is **prime** (*praštevilo*) if it has **exactly two divisors**: 1 and itself. 1 is not prime (it has only one divisor). Numbers greater than 1 that are not prime are **composite** (*sestavljena*).

## Explanation

- **Testing one number $k$:** it is enough to try divisors up to $\sqrt{k}$. Divisors come in pairs $d \cdot \frac{k}{d}$, symmetric around $\sqrt{k}$, so if there is a divisor above the root, there is also one below it.
- Apart from 2 all primes are odd, so after 2 only odd candidates and odd divisors need to be checked.
- To list **all** primes up to a bound, the [[Sieve of Eratosthenes|sieve of Eratosthenes]] is much faster than testing each number separately.

## Examples

**The prime numbers program, version by version** (Programming 1, lectures 3–5):

| version | idea |
|---|---|
| 1 | count all divisors of each candidate, prime if the count is 2 |
| 2 | stop at the first divisor (`break`), with a [[Boolean\|boolean]] flag `prastevilo` |
| 3 | only odd candidates and odd divisors |
| 4 | divisors only up to $\sqrt{k}$ |
| methods | the test as a [[Method\|method]] (`Prastevila5`, lecture 4) |
| last | [[Sieve of Eratosthenes\|sieve of Eratosthenes]] with a `boolean` array (`PrastevilaZadnja`, lecture 5) |

**In Discrete structures:** "$x$ is a prime number" is an example of a one-place predicate ([[Predicate Logic]]).

## Connections

- [[2026-10-19 - Valid Arguments and Inference Rules - 3]] — "$x$ is a prime number" as a predicate (Discrete structures)
- [[2026-10-22 - Loop Examples, break and switch - 3]] — versions 1–4, checking divisors up to $\sqrt{k}$ (Programming 1)
- [[2026-10-29 - Methods and Recursion - 4]] — prime numbers with methods (Programming 1)
- [[2026-11-05 - Arrays, Searching and Sorting - 5]] — the last version: the sieve (Programming 1)
- [[Sieve of Eratosthenes]], [[Nested Loop]], [[Greatest Common Divisor]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/03_krmilniKonstrukti_h.pdf|03 Krmilni konstrukti]], [[Sources/programming_1/prosojnice/04_metode_h.pdf|04 Metode]], [[Sources/programming_1/prosojnice/05_tabele_h.pdf|05 Tabele]] (Luka Fürst)
