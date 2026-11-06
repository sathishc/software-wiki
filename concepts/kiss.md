---
title: Keep It Simple (KISS)
tags: [kiss, simplicity, code-quality, craftsmanship]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/clean-code-review.md]
layout: default
parent: Concepts
---

# Keep It Simple (KISS)

**KISS** — "Keep It Simple, Stupid" — is the principle that a *simpler* design
is almost always preferable to a complex one, *where they achieve the same
result*. It is a design *constraint* (a constraint on how much you build), not
a goal to be maximised.

## The two readings

1. **Original (Karl Janzen, US Navy, 1960):** simple systems are *more reliable*
   — fewer parts, fewer failure modes. In software: fewer moving parts means
   fewer bugs, faster to understand, faster to change.
2. **Pragmatic (design):** when two designs meet the requirements, choose the
   one with less abstraction, fewer dependencies, less cleverness.

## Why it's a constraint, not a goal

The trap is treating "simple" as *as simple as possible*, which produces a
different failure mode: **too simple** to handle the real problem, so you bolt
on complexity later — and the bolted-on version is usually *more* complex than
the simple thing you should have written the first time. KISS is best read as
**"keep it as simple as it can be *and still do the job*."**

That framing is exactly why [Keep It Simple (KISS)](./kiss.md) and [You Aren't Gonna Need It (YAGNI)](./yagni.md) are siblings: KISS says
*don't build more than the job needs now*, YAGNI says *don't build for the job
you think you'll have*.

## Where it shows up

- One function that does the thing, instead of a three-layer abstraction for a
  one-line transform.
- A plain `if` where a strategy-pattern-with-five-implementations was proposed
  for one known case.
- A boring, well-understood technology for a problem a fancy framework only
  *might* need.

Simplicity is the *individual* expression of [Clean Code](./clean-code.md): a clean function
is a KISS function.

## Related Pages

- [YAGNI](./yagni.md)
- [Clean Code](./clean-code.md)
- [Technical Debt](./technical-debt.md)

## Sources

- [Clean Code, Code Review & Craftsmanship](../sources/clean-code-review.md)

## Maps of Content

- [Code Quality](../pages/code-quality.md)

## See also

- [You Aren't Gonna Need It (YAGNI)](yagni.md)
- [Don't Repeat Yourself (DRY)](dry.md)
- [Clean Code](clean-code.md)
- [Code Smells](code-smells.md)
