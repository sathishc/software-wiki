---
title: You Aren't Gonna Need It (YAGNI)
tags: [yagni, simplicity, code-quality, tdd]
created: 2026-09-25
updated: 2026-09-25
sources: [sources/clean-code-review.md, sources/beck-xp-tdd.md]
layout: default
parent: Concepts
---

# You Aren't Gonna Need It (YAGNI)

**YAGNI** — a mantra from [Kent Beck](../people/kent-beck.md)'s [Test-Driven Development (TDD)](./tdd.md)/XP world — says: *don't add
functionality until it is actually required.* It is the discipline that
defuses over-engineering: build for the *known* requirement, not for the
*imagined* one.

## The core argument

Every line of speculative code is a **liability** with no offsetting asset:

- It **costs** to write, but more it *costs to maintain* — and to *understand*.
- It **hides** the real design: a generalisation made for a hypothetical
  second use usually *mis-generalises*, and the moment the real second use
  arrives it's wrong and has to be rewritten.
- It **distracts** — effort spent on "what if" is effort *not* spent on the
  "what is."

The empirical point: **you cannot predict the requirements you will actually
get.** The ones you build ahead of time are almost never the ones that arrive.
So you've paid real cost for zero real benefit.

## The discipline, in practice

YAGNI is *not* "never design for the future" — it is "**design for what you
know, and make it easy to change when what-you-don't-know arrives.**" The two
are reconciled by *refactoring*: keep the known solution simple, and when a
second real use appears, *extract* the generalisation *then*, with tests.

This is why YAGNI is a **[Test-Driven Development (TDD)](./tdd.md)** and [Refactoring](./refactoring.md) principle, not just a
simplicity slogan: TDD's "write the simplest code that passes" *is* YAGNI made
mechanical, and refactoring is the safe way to generalise later.

## Related Pages

- [KISS](./kiss.md)
- [TDD](./tdd.md)
- [Refactoring](./refactoring.md)
- [Technical Debt](./technical-debt.md)

## Sources

- [Clean Code, Code Review & Craftsmanship](../sources/clean-code-review.md)
- [XP & TDD](../sources/beck-xp-tdd.md)

## Maps of Content

- [Code Quality](../pages/code-quality.md)
