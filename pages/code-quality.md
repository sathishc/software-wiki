---
title: Code Quality
tags: [moc, code-quality, craftsmanship, refactoring]
created: 2026-09-25
updated: 2026-09-25
sources: [sources/clean-code-review.md, sources/fowler-refactoring.md, sources/feathers-legacy-code.md]
layout: default
parent: Pages
---

# Code Quality

> A curated map of how software stays *readable, changeable, and worth the
> investment* — the individual-and-team craft of writing code that *compounds*
> rather than rots. This is the entry point into the *quality* side of the
> wiki. It synthesises the **code-quality** domain; the deeper mechanisms live
> in the linked concept pages.

## The one-line idea

**Code is written once and read many times.** Every line you write is an *asset*
(readable, changeable) or a *liability* (confusing, change-resistant). Code
quality is the discipline of *choosing the asset side on purpose*, every day,
across the life of a codebase.

## How the pieces fit

```
        intent & simplicity                 structure
   ┌───────────────────────────┐      ┌───────────────────────────┐
   │   KISS  ·  YAGNI          │      │   SOLID  ·  Design         │
   │   (don't build the        │      │   Patterns                │
   │    thing you don't need)  │      │   (decoupling)            │
   └─────────────┬─────────────┘      └─────────────┬─────────────┘
                 │        readability               │
                 ▼                                   ▼
   ┌─────────────────────────────────────────────────────────────────┐
   │                  Clean Code  (names, small fns, honest)         │
   └──────────────────────────────┬──────────────────────────────────┘
                                  │   made mechanical by
                                  ▼
   ┌───────────────────────────┐      ┌───────────────────────────┐
   │   Refactoring  (pay the   │◄────►│   Code Smells  (the       │
   │   debt, one step at a     │      │   "where to start")       │
   │   time, tests as a net)   │      │                           │
   └─────────────┬─────────────┘      └───────────────────────────┘
                 │   accrues when you don't
                 ▼
   ┌───────────────────────────┐      ┌───────────────────────────┐
   │  Technical Debt (the tax) │◄────►│  Code Review (the culture)│
   └───────────────────────────┘      └───────────────────────────┘
```

Read the diagram **top-down for a *greenfield*** choice (simplicity →
structure → readability), and **bottom-up for a *brownfield*** rescue (debt →
smells → refactor). Both directions are the *same* practice at different
lifecycle stages.

## The synthesis (where these fit together)

- **[Keep It Simple (KISS)](../concepts/kiss.md) + [You Aren't Gonna Need It (YAGNI)](../concepts/yagni.md)** are the *restraint* — the discipline of *not*
  building what you don't need *yet*. They keep you *simple* so that
  [SOLID](../concepts/solid.md) and [Design Patterns](../concepts/design-patterns.md) are *tools you reach for when you actually
  expect variation*, not garnish.
- **[SOLID](../concepts/solid.md) + [Design Patterns](../concepts/design-patterns.md)** are the *structure* — the *how* of
  decoupling so a change ripples through *few* places.
- **[Clean Code](../concepts/clean-code.md)** is the *readability* — the *how* of making that structure
  *readable* (names, small functions, honest comments).
- **[Refactoring](../concepts/refactoring.md) + [Code Smells](../concepts/code-smells.md)** are the *maintenance* — *smell* a
  problem, *apply the named fix*, *one step at a time*. This is how a codebase
  *stays* good after it was written.
- **[Technical Debt](../concepts/technical-debt.md)** is the *economics* — the *cost* of *not* doing all the
  above, *compounding* over time.
- **[Code Review](../concepts/code-review.md)** is the *culture* — how all of the above becomes *shared*
  across a team, and how *standards* are *enforced*.

The **unifying thread** is **economics**: simplicity is *cheap to change*
([refactoring](../concepts/refactoring.md)), decoupling is *cheap to change*
([solid](../concepts/solid.md)), and *all of it* is *repaying interest* on the
debt you took to move fast ([technical-debt](../concepts/technical-debt.md)).
*Quality is not a moral position, it is a *throughput* strategy.*

## The key people

- **[Robert-Martin](../people/robert-martin.md)** — [SOLID](../concepts/solid.md), [Clean Code](../concepts/clean-code.md), the *individual* standard.
- **[Martin Fowler](../people/martin-fowler.md)** — [Refactoring](../concepts/refactoring.md), [Code Smells](../concepts/code-smells.md), the *named* moves.
- **[Michael Feathers](../people/michael-feathers.md)** — [Technical Debt](../concepts/technical-debt.md) made *operational* on the
  unglamorous, *untouchable* codebases.

## Recommended reading order

1. **[Code Quality](./code-quality.md)** (you are here — the map).
2. **[Clean Code](../concepts/clean-code.md)** — the *daily* habit (names, functions, comments).
3. **[Refactoring](../concepts/refactoring.md)** — the *maintenance* loop (and why tests make it safe).
4. **[Technical Debt](../concepts/technical-debt.md)** — the *economics* (why all of this *matters*).
5. **[Code Review](../concepts/code-review.md)** — how it becomes a *team* culture.

Then circle back to **[SOLID](../concepts/solid.md)** / **[Design Patterns](../concepts/design-patterns.md)** as the *structural*
deep-dive, and **[Keep It Simple (KISS)](../concepts/kiss.md)**/**[You Aren't Gonna Need It (YAGNI)](../concepts/yagni.md)** as the *restraint* you apply *first*.

## Related Maps of Content

- [Testing & Quality](./testing.md) — the *safety net* that makes all of this
  *possible*.
- [Architecture & Design](./architecture.md) — the *system-scale* version of the
  same economics.
- [Delivery](./delivery.md) — how quality *survives* under the *velocity*
  pressure of shipping.
