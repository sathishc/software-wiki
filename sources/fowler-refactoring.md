---
title: "Refactoring — Martin Fowler (2001)"
tags: [sources, refactoring, code-quality, code-smells, martin-fowler]
source: https://martinfowler.com/articles/refactoring.html
ingested: 2026-09-25
---

# Refactoring — Source Notes

**Book:** Refactoring: Improving the Design of Existing Code (1st ed. 2001, 2nd ed. 2018)
**Author:** Martin Fowler (with Kent Beck)

**Reference URLs captured:**
- https://martinfowler.com/articles/refactoring.html (Fowler's companion article)
- https://refactoring.com/catalog/ (the catalogue of refactorings)
- https://en.wikipedia.org/wiki/Refactoring

---

## What a refactor is

Refactoring (in the plural, *refactorings*) is a controlled change to an
existing codebase that alters its **internal structure** while preserving its
**observable behaviour**. Both of these must hold:

1. It **does not add a new feature** (no behavioural change).
2. It **makes the code easier to understand** and harder to break (it improves
   the design).

If either is violated, the change is a bug or a feature, not a refactor.

## Why bother

Fowler's argument: **code is read far more often than it is written.** Well-
read code is a compounding asset; messy code is a tax on every future change.
Refactoring pays for itself by making the *next* change cheaper and safer. This
is the same economics as [Technical Debt](../concepts/technical-debt.md) — you choose to repay interest so
the principal stays manageable.

## Smells

A **code smell** is a heuristic indicator in the code that something may be
wrong — a signal worth investigating, not a rule to blindly apply. Fowler's
catalogue lists dozens (Duplicate Code, Long Function, Feature Envy,
Data Clumps, Primitive Obsession, Magic Numbers, ...). Smells are where you
*start* a refactor; they are not the goal.

## The catalogue of refactorings

Refactorings are small, well-understood, behaviour-preserving moves. The
catalogue is the operational heart of the book. Representative ones, grouped:

- **Extract Method** — split a long function into a named helper.
- **Move Function / Move Field** — relocate behaviour to the type that best
  owns it (reduces smells like Feature Envy).
- **Replace Conditional with Polymorphism** — replace a long `switch` on type
  with a method in each subclass.
- **Introduce Parameter Object** — bundle a recurring cluster of parameters.
- **Separate Query from Modifier** — a function should either ask a question
  or change state, not both.
- **Rename** — often the highest value-per-minute refactor.

## How to refactor safely (the mechanics)

You only *can* refactor confidently because of two enablers:

1. **A good [Unit Testing](../concepts/unit-testing.md) suite** — the safety net that proves behaviour is
   preserved. Fowler: "Refactoring is *only* safe if you have tests."
2. **Small steps** — apply one catalogue refactoring at a time, committing and
   running tests after each. A large one-shot "clean up" is how you break
   things you can't see you broke.

This coupling — **refactoring depends on tests, and tests depend on
refactorable code** — is the engine behind [Test-Driven Development (TDD)](../concepts/tdd.md): the discipline of keeping
code in a state where you *can* keep improving it.

---
*Note: synthesis of Fowler's article and the public catalogue; the book's 50+
refactorings are a reference in their own right.*
