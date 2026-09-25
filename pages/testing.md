---
title: Testing & Quality
tags: [moc, testing, tdd, quality]
created: 2026-09-25
updated: 2026-09-25
sources: [sources/beck-xp-tdd.md, sources/feathers-legacy-code.md, sources/fowler-ci-cd.md]
layout: default
parent: Pages
---

# Testing & Quality

> A curated map of the *safety net* that makes every other practice in this
> wiki *possible* — from the smallest unit test to the pipeline that runs them.
> **Tests are the enabler**: you *cannot* [Refactoring](../concepts/refactoring.md), *cannot* do [Test-Driven Development (TDD)](../concepts/tdd.md),
> and *cannot* [Code Review](../concepts/code-review.md) with confidence unless you have them.

## The one-line idea

A **green test suite at any moment is the *proof* that the code *works now*.**
That single property — *known-good, continuously verified* — is the *load-
bearing* wall under [Refactoring](../concepts/refactoring.md), [Test-Driven Development (TDD)](../concepts/tdd.md), and [Continuous Integration & Continuous Delivery (CI/CD)](../concepts/ci-cd.md) all stand. Test
quality is the *foundation layer* of software quality.

## How the pieces fit

```
        ┌──────────────────────────────────────────────────────────┐
        │                Test-Driven Development                   │
        │     (Red → Green → Refactor — the *discipline*)          │
        └────────────────────────────┬─────────────────────────────┘
                                     │  the loop *is* a unit test
                                     ▼
   ┌────────────────────────────────────────────────────────────────────┐
   │                         Unit Tests  (the base)                     │
   │   isolated · fast · deterministic · independent  →  the safety net │
   └────────────────────────────────────────────────────────────────────┘
                                     │  wrapped by
                                     ▼
   ┌────────────────────────────────────────────────────────────────────┐
   │                        Integration Tests  (the seams)              │
   │   correctly-built units, wired together, against the real boundary │
   └────────────────────────────────────────────────────────────────────┘
                                     │  crowned by
                                     ▼
   ┌────────────────────────────────────────────────────────────────────┐
   │                  End-to-End / UI Tests  (the tip)                  │
   │   a few, for the *critical* user journeys; slow & expensive        │
   └────────────────────────────────────────────────────────────────────┘
                                     │  the whole pyramid is *run by*
                                     ▼
   ┌────────────────────────────────────────────────────────────────────┐
   │                     Continuous Integration / CD                    │
   │   every merge *builds + runs the whole pyramid* automatically      │
   └────────────────────────────────────────────────────────────────────┘
```

The **[Test Pyramid](../concepts/test-pyramid.md)** is the *shape*: a *broad* base of fast [Unit Testing](../concepts/unit-testing.md), a *narrower* middle of *integration*, a *small* tip of *e2e*.
Everything in this map is a *view* of that shape.

## The synthesis (where these fit together)

- **[Unit Testing](../concepts/unit-testing.md)** is the *base* — fast, isolated, the *safety net*.
  *Isolated, fast, deterministic, independent* are the four properties that
  make it a *unit* test (and what *you check* in [Code Review](../concepts/code-review.md)).
- **[Test-Driven Development (TDD)](../concepts/tdd.md)** is the *discipline* — *write the test *before* the code*,
  *simplest code that passes*, *clean it up*. TDD is *four* jobs in one:
  *spec, safety-net, documentation, and (the big one) **design pressure**.*
- **[Test Pyramid](../concepts/test-pyramid.md)** is the *proportion* — *allocate* your *testing budget*
  so *feedback stays fast* as the suite grows. It is a *feedback-latency*
  model: *the higher a test sits, the slower it is.*
- **[Continuous Integration & Continuous Delivery (CI/CD)](../concepts/ci-cd.md)** is the *runner* — the pipeline that *builds + runs the whole
  pyramid* on *every merge*, so that "the tests pass" is *always* the *current*
  truth.
- **[Code Review](../concepts/code-review.md)** is the *human layer* — the *second pair of eyes* on what
  the tests *don't* check (design, intent, *should-this-even-exist*).

The **unifying thread** is **feedback speed**: the *whole* map is one machine
for *shrinking the loop* between *"I made a change"* and *"I know whether it
was a good one."* That same loop, *shrunk*, reappears at every scale — a
*[Test-Driven Development (TDD)](../concepts/tdd.md) loop* (minutes), a *[Refactoring](../concepts/refactoring.md) loop* (minutes), a *[Continuous Integration & Continuous Delivery (CI/CD)](../concepts/ci-cd.md)*
pipeline (minutes–hours), and *[DORA Metrics](../concepts/dora-metrics.md)* (the *measured* version of
all of it).

## The key people

- **[Kent Beck](../people/kent-beck.md)** — [Test-Driven Development (TDD)](../concepts/tdd.md) and *XP*; the *feedback-everything* origin.
- **[Michael Feathers](../people/michael-feathers.md)** — the *brownfield* reality: *legacy code is code
  without tests*; *characterization tests* and *seams* are how you *add* the
  net to code that *lacks* it.

## Recommended reading order

1. **[Testing & Quality](./testing.md)** (you are here — the map).
2. **[Unit Testing](../concepts/unit-testing.md)** — the *base* (and *why* it's the *linchpin*).
3. **[Test-Driven Development (TDD)](../concepts/tdd.md)** — the *discipline* (and the *design* payoff of test-first).
4. **[Test Pyramid](../concepts/test-pyramid.md)** — the *proportion* (and *why* "more e2e" is a trap).
5. **[Continuous Integration & Continuous Delivery (CI/CD)](../concepts/ci-cd.md)** — the *runner* (the *automatic* half).

## Related Maps of Content

- [Code Quality](./code-quality.md) — the *craft* that tests *protect*.
- [Delivery](./delivery.md) — the *measured* outcome of all of this
  ([DORA Metrics](../concepts/dora-metrics.md)).
