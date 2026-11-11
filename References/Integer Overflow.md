---
type: "[[Concepts]]"
status: developed
aliases:
  - Prekoračitev obsega
  - Overflow
---

# Integer Overflow

## Definition

Integer overflow happens when the result of an integer operation lies outside the range of its type. Java integer types have a **fixed width**, so the result **wraps around** to the other end of the range — and Java does **not** report it (no compiler error, no exception).

| Type | Range |
|---|---|
| `byte` | $[-2^7, 2^7 - 1]$ |
| `short` | $[-2^{15}, 2^{15} - 1]$ |
| `int` | $[-2^{31}, 2^{31} - 1] = [-2147483648, 2147483647]$ |
| `long` | $[-2^{63}, 2^{63} - 1]$ |

## Explanation

In mathematics we imagine integers on an endless straight line. An `int` has only 32 bits, so there are only $2^{32}$ values, arranged **in a circle**: after `Integer.MAX_VALUE` comes `Integer.MIN_VALUE`.

Technically: if an integer addition overflows, the result is the low-order bits of the exact mathematical sum in two's complement (JLS §15.18.2). The integer operators "do not indicate overflow or underflow in any way" (JLS §4.2.2).

**How to avoid it:**

- Use a wider type, e.g. `long` instead of `int` — with at least one `long` operand (`L` suffix) the operation is computed in `long`.
- When an overflow must not go unnoticed, `Math.addExact`, `Math.multiplyExact`, … throw an `ArithmeticException` instead of wrapping (Java API).

**Common mistakes:**

- Writing the result into a `long` is not enough — `long x = 1000000000 + 2000000000;` still overflows, because the addition is done in `int` **before** the assignment.
- Overflow during a calculation is not a compile error. The compiler only rejects values it can see are out of range: `int c = 3000000000;` → *integer number too large*, `int c = 3000000000L;` → *incompatible types: possible lossy conversion from long to int*.

## Examples

From [[2026-10-08 - Introduction to programming - 1|Programming 1, lecture 1]]:

```text
jshell> 1000000000 + 2000000000
$1 ==> -1294967296

jshell> 1000000000L + 2000000000
$2 ==> 3000000000

jshell> Integer.MAX_VALUE + 1
$3 ==> -2147483648
```

$3000000000 - 2^{32} = 3000000000 - 4294967296 = -1294967296$ — one full turn around the circle.

## Connections

- [[2026-10-08 - Introduction to programming - 1]] — numeric types, overflow example, `long` as the solution
- [[2026-10-19 - Exercises for Control Structures - 2]] — `int` overflow of `potenca` for an 18-digit number (Programming 1)
- [[JShell]]

## Sources

- `programming_1/prosojnice/01_02_uvod_h.pdf` — ranges of integer types (slide 21)
- Java Language Specification, §4.2.2 *Integer Operations* and §15.18.2 *Additive Operators* — docs.oracle.com/javase/specs
- Java API, `java.lang.Math.addExact` — docs.oracle.com
