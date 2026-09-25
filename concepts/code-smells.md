---
title: Code Smells
tags: [code-smells, code-quality, refactoring]
created: 2026-09-25
updated: 2026-09-25
sources: [sources/fowler-refactoring.md]
layout: default
parent: Concepts
---

# Code Smells

A **code smell** is a *heuristic signal* in code that something may be wrong
— a fast, pattern-based indicator that a deeper problem is likely nearby. The
name comes from the idea that you *smell* the problem and then *investigate*;
a smell is a **clue, not a diagnosis, and never a rule to blindly apply.**

## What a smell is *not*

- It is **not a bug** — smelly code can run perfectly.
- It is **not a lint error** — most smells are structural, not syntactic; a
  compiler won't flag them.
- It is **not automatically bad** — a smell is a *worth-looking-here* flag.
  Context decides whether the underlying issue is real.

## A representative catalogue (Fowler)

| Smell | Signal | Typical fix (a [Refactoring](./refactoring.md)) |
|---|---|---|
| **Duplicate Code** | The same logic appears in two or more places | Extract shared method / [Don't Repeat Yourself (DRY)](./dry.md) |
| **Long Function** | One function does many things | Extract Method |
| **Feature Envy** | A method reaches into another object's data more than its own | Move the method to the object it uses |
| **Data Clumps** | The same cluster of fields/params travels together | Introduce Parameter Object / Value Object |
| **Primitive Obsession** | Primitives/types where a small type would express intent | Replace with a dedicated type |
| **Magic Numbers** | Hardcoded constants with no name | Replace with named constants |
| **Shotgun Surgery** | One change forces edits across many files | Move the scattered responsibilities together |
| **God Class** | One type knows and does too much | Split into cohesive types ([SOLID](./solid.md): SRP) |

## Why they matter

Smells are the *starting point* of [Refactoring](./refactoring.md): you *smell* a problem, you
*investigate* to confirm the underlying issue, you *apply the named refactor*
that addresses it. They turn the vague "this code feels icky" into an
actionable, teachable, *repeatable* process — which is exactly what makes
[Code Quality](../pages/code-quality.md) a practice rather than a vibe. Smells are also what
[Code Review](./code-review.md) surfaces: a reviewer's job is half to *smell* problems the
author's over-familiarity hid.

## Related Pages

- [Refactoring](./refactoring.md)
- [Clean Code](./clean-code.md)
- [Technical Debt](./technical-debt.md)

## Sources

- [Refactoring](../sources/fowler-refactoring.md)

## Maps of Content

- [Code Quality](../pages/code-quality.md)
