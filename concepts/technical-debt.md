---
title: Technical Debt
tags: [technical-debt, code-quality, refactoring, craftsmanship]
created: 2026-09-25
updated: 2026-09-25
sources: [sources/feathers-legacy-code.md, sources/fowler-refactoring.md, sources/clean-code-review.md]
layout: default
parent: Concepts
---

# Technical Debt

**Technical debt** is a *metaphor* (coined by **Ward Cunningham**, ~1992) for
the long-term cost of choosing a *faster, easier, or less correct* way of doing
something *now* in exchange for *paying it off later.* Like financial debt, it
is deliberate and useful in the short term — *if and only if* it is eventually
repaid.

## The metaphor, precisely

- **Taking on debt** — a deliberate, *intentional* shortcut (skip a test to hit
  a deadline; hardcode a value; bypass an abstraction) is a *good* use of the
  metaphor: you consciously trade speed for future cost.
- **The interest** — this is the part people miss. **Debt accrues interest**:
  the more you build on top of a shortcut, and the longer it sits, the *more
  expensive every change* that touches it becomes. A small debt ignored for a
  year is a large debt.
- **Paying it off** — refactoring, adding tests, adding the missing abstraction.
  *This* is where [Refactoring](./refactoring.md) and [Unit Testing](./unit-testing.md) live.

## The two kinds

- **Strategic (deliberate)** — a *known, accepted* trade-off: "we're shipping
  this weekend, we'll pay this off next sprint." Manageable *if* it is tracked
  and repaid.
- **Accidental (unintentional)** — debt taken on *without realising* it was
  debt (nobody noticed the code was rotting). This is the dangerous kind: it
  compounds invisibly because nobody is *counting* it.

## Why the metaphor is (deliberately) flawed

Ward Cunningham has said the metaphor is *wrong but useful*, and the failure
modes matter:

1. **Debt isn't visible** — real debt is in a ledger; technical debt is buried
   in code. Without *explicit* tracking (a debt list, a "tech debt" sprint),
   it is assumed away.
2. **It's not optional** — in finance you *may* or may not repay. In software,
   the "principal" (the code) is the *product*; you cannot delete the debt, you
   can only *stop the bleeding* or *refactor it down*.
3. **Pressure to never repay** — management reads "debt" as "we can ignore it,"
   so the interest compounds forever. The fix is to make debt *measurable and
   visible* so repayment competes for the same budget as features.

## Related Pages

- [Refactoring](./refactoring.md)
- [Unit Testing](./unit-testing.md)
- [Code Smells](./code-smells.md)
- [Michael Feathers](../people/michael-feathers.md)

## Sources

- [Working Effectively with Legacy Code](../sources/feathers-legacy-code.md)
- [Refactoring](../sources/fowler-refactoring.md)
- [Clean Code, Code Review & Craftsmanship](../sources/clean-code-review.md)

## Maps of Content

- [Code Quality](../pages/code-quality.md)
