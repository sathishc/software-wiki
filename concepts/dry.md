---
title: Don't Repeat Yourself (DRY)
tags: [dry, code-quality, craftsmanship, refactoring]
created: 2026-09-25
updated: 2026-09-25
sources: [sources/clean-code-review.md, sources/fowler-refactoring.md]
layout: default
parent: Concepts
---

# Don't Repeat Yourself (DRY)

**DRY** is a software-design principle: *every piece of knowledge in a system
should have a single, unambiguous, authoritative representation within that
system.* It is one of the most-quoted mantras of the [Code Quality](../pages/code-quality.md) and
craftsmanship movements.

## What "knowledge" means here

DRY is *not* "never write the same line of code twice" — that reading is a
classic misuse. **Knowledge** is a *fact, a rule, a piece of data that has one
true value.* The principle says: that fact should live in **one place**, and
everywhere else it appears should *refer* to that place.

If the string `"2026-01-01"` or the tax rate or the validation rule for an
email appears in five files and you change it in four, you just created a bug.
The bug is not the duplication of *text*; it is the duplication of *knowledge*.

## Where it bites

- A magic constant in three files → lift to one named constant.
- A validation rule in a controller and a form and a job → one function.
- A query shape in two places → one repository method.

DRY is the *motivating* principle behind the **Duplicate Code** smell and a
large part of the [Refactoring](./refactoring.md) catalogue (Extract Method, Replace
Variable with Method, Pull Up Method). It is the direct enemy of [Technical Debt](./technical-debt.md) in practice: duplication is debt that *always* eventually pays interest.

## The honest caveat (pair it with YAGNI)

Premature DRY is a real failure mode. Abstracting two similar functions that
*actually differ in intent* forces a false coupling that hurts more than the
duplication saved. The discipline is: **duplicate first, then extract when you
see the third occurrence** (the "Rule of Three"). DRY and [You Aren't Gonna Need It (YAGNI)](./yagni.md) are the two
horses; over-mate either and the system buckles.

## Related Pages

- [Refactoring](./refactoring.md)
- [YAGNI](./yagni.md)
- [Code Smells](./code-smells.md)
- [Technical Debt](./technical-debt.md)

## Sources

- [Clean Code, Code Review & Craftsmanship](../sources/clean-code-review.md)
- [Refactoring](../sources/fowler-refactoring.md)

## Maps of Content

- [Code Quality](../pages/code-quality.md)
