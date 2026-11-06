---
title: Functional Programming
tags: [functional-programming, architecture, design-patterns]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/fowler-refactoring.md]
layout: default
parent: Concepts
---

# Functional Programming

**Functional programming (FP)** is a style built on two core moves:

1. **Pure functions** — a function whose result depends *only* on its inputs and
   that performs no observable side effects (no I/O, no mutation of shared state).
2. **Immutability** — data is not modified in place; a "change" produces a new
   value, so every existing reference stays valid.

From those two moves, the rest follows: **referential transparency** (a call can
be replaced by its value, anywhere), **composition** (functions are first-class
values — you *build* behaviour by combining functions rather than assembling
objects), and **declarative style** (you say *what* maps a collection, not *how*
the loop steps).

## Where it comes from

Lambda calculus and Lisp (1950s–60s); the practical descendants — ML, Haskell,
Erlang/Elixir, Scala, Clojure — and the *import* of the style into mainstream
languages: JavaScript (`map`/`filter`/`reduce`, `const`), Kotlin, Swift, Rust
(`immutable by default`), C#.

## Why it matters for software engineering

- **Testing.** A pure function is the *ideal* unit of [Unit Testing](./unit-testing.md):
  same input → same output, always, so tests need no fixtures, no mocks, no
  ordering. This is why FP codebases get *high test coverage with little
  test code* — and why [Test-Driven Development](./tdd.md) is more natural in
  an FP style (there is little mutable state to drive behaviour).
- **Concurrency.** The majority of classic concurrency bugs are *aliasing* bugs:
  two threads mutate shared state. Immutability makes that class of bug
  *unrepresentable* — data can be shared freely without locks. (See
  [Architecture & Design](../pages/architecture.md) — boundaries still matter for
  *where* side effects happen.)
- **Simplifying design patterns.** Many object-oriented [Design Patterns](./design-patterns.md)
  exist to manage *shared mutable state* (Flyweight, Proxy, State). In a pure
  functional core they often *dissolve* — a Strategy pattern becomes "pass the
  function", a Factory with no side effects becomes a lazy value. The
  relationship is complementary: the *tactical* core of [SOLID](./solid.md)
  (small, pure, single-purpose functions; immutable value objects) is exactly
  where OO and FP agree.
- **Refactoring safety.** Referential transparency is what makes
  [Refactoring](./refactoring.md) *mechanically* safe: replacing an expression
  with its value is always a valid step. Mutation is the main reason refactors
  go wrong in practice.

## The pragmatic stance (and the trade-off)

Almost no large codebase is *pure* — I/O, databases, and time *are* the job.
The working pattern in the mainstream is **functional core, imperative shell**:
a large pure middle (easy to test, reason about, and parallelise) with side
effects isolated at the edges (boundaries, adapters, CLI, I/O).

Trade-off: the learning curve (point-free style, type-level tricks), and stack
traces/expressiveness for *sequential* UI logic where object graphs are natural.
Take the *ideas* (purity, immutability, composition) — not the *culture*
(mandatory monads).

## Related Pages

- [Design Patterns](./design-patterns.md) — many OO patterns dissolve under purity
- [SOLID](./solid.md) — the tactical overlap (small pure units, immutable values)
- [Unit Testing](./unit-testing.md) — purity is what makes tests trivial
- [Refactoring](./refactoring.md) — referential transparency = safe transformation steps
- [Code Quality](../pages/code-quality.md) — this map

## See also

- [Unit Testing](unit-testing.md)
- [Design Patterns](design-patterns.md)
- [Clean Code](clean-code.md)
