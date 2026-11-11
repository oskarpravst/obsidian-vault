---
type: "[[Concepts]]"
status: developed
aliases:
  - Pogojni stavek
  - if statement
  - if-else
---

# Conditional Statement

## Definition

A **conditional statement** (*pogojni stavek*, `if`) executes a part of the program only if a condition, a [[Boolean|boolean]] expression, is `true`.

```java
if (pogoj) {
    stavki1      // when the condition holds
} else {
    stavki2      // when it does not
}
```

## Explanation

- The `else` part is optional. `if` – `else` together is **one** statement.
- **Chaining:** `if` – `else if` – … – `else`. Only **one** branch of the chain is ever executed: the first whose condition is true.
- `else if` is not a separate keyword. It is an `if` that is the single statement of an `else`, written without braces ([[Block]]).
- With only a single statement the braces can be left out, but it is safer to keep them.
- Alternatives: the [[Switch Statement|`switch` statement]] replaces a long `else if` chain that compares one value with constants, and the [[Conditional Operator|conditional operator]] `pogoj ? a : b` chooses between two values inside an expression.

## Examples

**Grade** (Programming 1, lecture 2): an `else if` chain that maps points to grades. **Leap year** (lecture 2): a combined condition with `&&` and `||`.

## Connections

- [[2026-10-15 - Control Structures - 2]] — `if`, `if` – `else`, `else if`, logical expressions (Programming 1)
- [[2026-10-22 - Loop Examples, break and switch - 3]] — `switch` as a replacement for an `else if` chain (Programming 1)
- [[Boolean]], [[Block]], [[Switch Statement]], [[Conditional Operator]], [[Short-circuit Evaluation]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/03_krmilniKonstrukti_h.pdf|03 Krmilni konstrukti]] (Luka Fürst)
