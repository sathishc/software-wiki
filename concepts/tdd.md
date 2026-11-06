---
title: Test-Driven Development (TDD)
tags: [tdd, testing, quality, xp, refactoring]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/beck-xp-tdd.md]
layout: default
parent: Concepts
---

# Test-Driven Development (TDD)

**TDD** is the discipline of writing a *failing* test **before** you write the
code that satisfies it — then writing the *simplest* code that passes, then
cleaning up. Popularised by [Kent Beck](../people/kent-beck.md) in [Extreme Programming](./xp.md) and the Agile movement.
The three-step loop, repeated constantly:

1. **Red** — write a small *failing* test that specifies a slice of desired
   behaviour.
2. **Green** — write the *minimum* code to make it pass (resist over-building;
   this is [You Aren't Gonna Need It (YAGNI)](./yagni.md) made mechanical).
3. **Refactor** — clean the code (remove duplication, improve names) while the
   test stays green. Then start the loop again.

## The four jobs the test does at once

TDD is often misunderstood as "write lots of tests." It is *four* things in one
discipline:

- **Specification** — writing the test first forces you to *articulate what
  "done" means* before you build it. Ambiguity dies in the test.
- **Safety net** — a green suite means the code works *now*, which is what makes
  [Refactoring](./refactoring.md) safe.
- **Executable documentation** — the tests say *what the system does* far more
  precisely and more current than any prose.
- **Design pressure** — this is the subtle, highest-value one. To make a test
  *pass*, you must write *testable* code — which forces **small, loosely-
  coupled, single-responsibility** units. TDD is a *design* tool disguised as a
  testing habit. You cannot easily test a god class; TDD nudges you to never
  write one.

## What TDD is *not*

- It is **not** 100% coverage. Coverage is a by-product, never the goal.
- It is **not** "write all the end-to-end tests first." That inverts the
  [Test Pyramid](./test-pyramid.md): TDD lives at the *unit* level (fast, isolated), and the
  integration/e2e layers are added around it, not in place of it.

## Related Pages

- [Unit Testing](./unit-testing.md)
- [Test Pyramid](./test-pyramid.md)
- [Refactoring](./refactoring.md)
- [Kent Beck](../people/kent-beck.md)

## Sources

- [XP & TDD](../sources/beck-xp-tdd.md)

## Maps of Content

- [Testing & Quality](../pages/testing.md)

## See also

- [Unit Testing](unit-testing.md)
- [Refactoring](refactoring.md)
- [Test Pyramid](test-pyramid.md)
- [Extreme Programming](xp.md)
- [Ports and Adapters (Hexagonal Architecture)](ports-and-adapters.md)
- [Clean Code](clean-code.md)
