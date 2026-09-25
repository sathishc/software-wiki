---
title: Test Pyramid
tags: [test-pyramid, testing, quality, tdd, observability]
created: 2026-09-25
updated: 2026-09-25
sources: [sources/beck-xp-tdd.md, sources/fowler-ci-cd.md]
layout: default
parent: Concepts
---

# Test Pyramid

The **test pyramid** (attributed to Ham Vervloet; popularised as the
"test pyramid" by Robert C. "Uncle Bob" Martin, 2011) is a *proportional*
model of a test suite. The claim: a healthy suite has a **broad base of fast unit tests**, a
narrower middle of *integration* tests, and a **small tip of slow end-to-end
(E2E) tests.**

```
            /           /E2E\          small, slow, expensive
          / ---- \
         / INTEGR \       medium: test the seams between units
        / -------- \
       /  UNIT TESTS \   broad: fast, cheap, the base
      / -------------- \
```

## Why the shape (and not an "ice-cream cone")

- **Unit tests** are *fast and cheap* — you can have hundreds or thousands and
  run them all in seconds. They catch the *most* bugs (most bugs are logic bugs
  *inside* a unit) at the *lowest* cost and *fastest* feedback.
- **Integration tests** are *medium* — they verify that correctly-built units
  actually *work together* (the seams, the database, the API boundary).
- **E2E tests** are *slow, flaky, and expensive* to write and maintain. A few
  that cover the *critical user journeys* is enough. A *pyramid* with a huge
  E2E tip (the "ice-cream cone" — an antipattern) is a suite that is *all
  expensive* and *gives the slowest feedback* — the opposite of what you want.

## The feedback-speed logic

The pyramid is really a **feedback-latency** model: *the higher a test sits in
the pyramid, the slower it runs and the later it tells you about a bug.* So you
put the *most* tests where feedback is *fastest* (the base) and the *fewest*
where it is slowest (the tip). This is the same logic as [Test-Driven Development (TDD)](./tdd.md) (fast unit
loop) and [Continuous Integration & Continuous Delivery (CI/CD)](./ci-cd.md) (short feedback loops) — the pyramid is how you *allocate*
your testing budget so the *total* feedback stays fast even as the suite grows.

## Related Pages

- [TDD](./tdd.md)
- [Unit Testing](./unit-testing.md)
- [Continuous Integration/CD](./ci-cd.md)

## Sources

- [XP & TDD](../sources/beck-xp-tdd.md)
- [CI/CD, DORA & DevOps](../sources/fowler-ci-cd.md)

## Maps of Content

- [Testing & Quality](../pages/testing.md)
