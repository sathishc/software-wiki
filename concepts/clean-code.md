---
title: Clean Code
tags: [clean-code, code-quality, craftsmanship, solid]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/clean-code-review.md]
layout: default
parent: Concepts
---

# Clean Code

**Clean Code** is the name Robert C. Martin [Robert-Martin](../people/robert-martin.md) gave to *readable,
well-structured, honest-about-intent* code — and to the handbook of the same
name (2008). The central claim is that **readability is a feature**: code is
written once and *read* many times, by many people, over years, so the cost of
a confusing line is paid on every single read.

## What "clean" means (the book's prescriptions)

- **Names** — intention-revealing, unambiguous, informative. The single
  highest-leverage move; a good name *is* the cheapest documentation. (A bad
  name compounds; a good name is free.)
- **Functions** — small, do *one thing*, sit at *one level of abstraction*,
  and have descriptive names. "Do one thing" is [SOLID](./solid.md)'s SRP at the
  function level.
- **Comments** — explain *why* (a decision, a non-obvious constraint), never
  *what* (the code shows the what). A comment that contradicts the code is a
  lie; a comment that paraphrases the code is noise.
- **Formatting** — a *shared, mechanical* convention, enforced by the tool, so
  humans argue about *design* instead of whitespace.
- **Error handling** — in *one* place, never swallowed, returns an error
  rather than a magic value.

## Where it sits

Clean Code is the **individual-contributor** layer of [Code Quality](../pages/code-quality.md). It is
the *same economics* as [Refactoring](./refactoring.md) and [Technical Debt](./technical-debt.md), expressed at
the scale of a function rather than a codebase: every line is either an asset
(readable) or a liability (confusing), and the choice is made *when you write
it.* [Robert-Martin](../people/robert-martin.md)'s [SOLID](./solid.md) principles are the *design-structure* half;
Clean Code is the *reading* half.

## Related Pages

- [SOLID](./solid.md)
- [DRY](./dry.md)
- [KISS](./kiss.md)
- [Code Review](./code-review.md)
- [Robert C. Martin](../people/robert-martin.md)

## Sources

- [Clean Code, Code Review & Craftsmanship](../sources/clean-code-review.md)

## Maps of Content

- [Code Quality](../pages/code-quality.md)

## See also

- [Refactoring](refactoring.md)
- [Code Smells](code-smells.md)
- [SOLID](solid.md)
- [Don't Repeat Yourself (DRY)](dry.md)
- [Keep It Simple (KISS)](kiss.md)
- [You Aren't Gonna Need It (YAGNI)](yagni.md)
- [Code Review](code-review.md)
