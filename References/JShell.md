---
type: "[[Concepts]]"
status:
aliases:
  - jshell
---

# JShell

## Definition

**JShell** is Java's interactive shell (REPL, *read–eval–print loop*). It runs single Java statements and expressions in the terminal and prints their value immediately, without writing a class and `main`.

## Explanation

- Start it with `jshell` in the terminal; leave it with `/exit`.
- It is the quickest way to test what an expression gives: integer division, overflow, `++`, arrays.
- The value of an expression is shown as `$1 ==> …`, a declared variable as `a ==> …`, and errors and exceptions are reported right away.

## Examples

```text
jshell> 5 / 3
$1 ==> 1

jshell> int[] t = new int[3];
t ==> int[3] { 0, 0, 0 }
```

## Connections

- [[2026-10-08 - Introduction to programming - 1]] — testing Java code in the terminal, [[Integer Overflow|overflow]] examples (Programming 1)
- [[2026-10-15 - Control Structures - 2]] — `++` and `--` in JShell (Programming 1)
- [[2026-11-05 - Arrays, Searching and Sorting - 5]] — arrays and `ArrayIndexOutOfBoundsException` in JShell (Programming 1)
- [[Java]], [[JVM]]

## Sources

- [JShell User's Guide — Oracle](https://docs.oracle.com/en/java/javase/21/jshell/introduction-jshell.html)
