---
type: "[[Concepts]]"
status: developed
aliases:
  - Blok
  - Code block
---

# Block

## Definition

A **block** (*blok*) is a sequence of statements in curly braces `{ }`. It counts as a single (compound) statement.

## Explanation

- Blocks give a program its structure and hierarchy: the body of a class, a [[Method|method]], a loop or an `if` branch is a block. Blocks can be nested.
- **Every variable exists only in the block where it was declared**, from the declaration to the closing `}` ([[Variable Scope|scope]]).
- Indentation is only for readability. The compiler ignores it and looks only at the braces.
- An `if` or a loop whose body is a single statement can be written without `{ }`. That is why `else if` works: the `if` after `else` is that single statement.

## Examples

**`do` loop** (Programming 1, lecture 3): the body of the `do` is a block, so a variable declared inside it does not exist in the condition `while (...)`.

**`switch`** (lecture 3): the whole `switch` is one block, so the same variable cannot be declared in two `case`s. Putting each `case` in its own `{ }` fixes it.

## Connections

- [[2026-10-08 - Introduction to programming - 1]] — blocks and scope (Programming 1)
- [[2026-10-22 - Loop Examples, break and switch - 3]] — `do` loop and `switch` blocks (Programming 1)
- [[Variable Scope]], [[Variable]], [[Conditional Statement]], [[Switch Statement]]

## Sources

- Slides: [[Sources/programming_1/prosojnice/01_02_uvod_h.pdf|01–02 Uvod]], [[Sources/programming_1/prosojnice/03_krmilniKonstrukti_h.pdf|03 Krmilni konstrukti]] (Luka Fürst)
