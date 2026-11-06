---
title: Refactoring
tags: [refactoring, code-quality, code-smells, technical-debt]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/fowler-refactoring.md, sources/feathers-legacy-code.md]
layout: default
parent: Concepts
---

# Refactoring

**Refactoring** is a *controlled change to existing code that alters its
internal structure while preserving its observable behaviour.* Both halves are
essential: it changes the design **and** it must not change what the program
does. A change that alters behaviour is a bug or a feature; a change that
doesn't improve the design is churn. Only the intersection is a *refactor.*

## Why it matters

Code is **read far more often than it is written** — by many people, over many
years. Messy code is a *tax* paid on every read and every future change.
Refactoring is how you pay down that tax *as you go*, so the codebase stays
approachable. It is the operational counterpart to [Technical Debt](./technical-debt.md): debt is
the *state* you're in, refactoring is the *repayment* you do.

## The catalogue

The discipline is made practical by a **catalogue of small, named, behaviour-
preserving moves** (Fowler's *Refactoring*). Each is tiny and safe on its own:

- **Extract Method** — split a long function into a named helper.
- **Rename** — the highest value-per-minute refactor; a good name is free
  documentation.
- **Move Function / Move Field** — relocate behaviour to the type that best
  owns it (kills [Code Smells](./code-smells.md) like Feature Envy).
- **Replace Conditional with Polymorphism** — turn a type-`switch` into a
  per-subclass method.
- **Separate Query from Modifier** — a function asks *or* it changes; not both.

You apply them **one at a time, committing and running tests after each**, so
any regression is caught in the step that caused it.

## The two enablers (why it's safe)

Refactoring is *only* safe because of two things that travel together:

1. **A strong [Unit Testing](./unit-testing.md) suite** — the safety net that *proves* behaviour
   is preserved. No tests, no refactoring: you'd be changing a black box.
2. **Small steps** — never a "big cleanup." One refactoring, one commit, tests
   green. That's the loop that makes [Test-Driven Development (TDD)](./tdd.md) and refactoring the same activity
   seen from two ends.

This is the deep link in this wiki: **tests and refactoring are mutually
dependent** — you need tests to refactor safely, and you need refactorable
code to write tests.

## Related Pages

- [Code Smells](./code-smells.md)
- [Unit Testing](./unit-testing.md)
- [TDD](./tdd.md)
- [Technical Debt](./technical-debt.md)
- [Martin Fowler](../people/martin-fowler.md)

## Sources

- **[Refactoring](../sources/fowler-refactoring.md)**
- [Working Effectively with Legacy Code](../sources/feathers-legacy-code.md)

## Maps of Content

- [Code Quality](../pages/code-quality.md)
- [Testing & Quality](../pages/testing.md)

## See also

- [Code Smells](code-smells.md)
- [Technical Debt](technical-debt.md)
- [Unit Testing](unit-testing.md)
- [Test-Driven Development (TDD)](tdd.md)
- [Clean Code](clean-code.md)
- [SOLID](solid.md)
