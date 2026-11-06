---
title: Code Review
tags: [code-review, quality, craftsmanship, ci-cd, delivery]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/clean-code-review.md, sources/fowler-ci-cd.md]
layout: default
parent: Concepts
---

# Code Review

**Code review** is the practice of a *peer* examining a proposed change *before
(or shortly after) it merges.* It is the **single highest-leverage *team-level*
quality practice** in this wiki — the team-scale analogue of [Refactoring](./refactoring.md)
and the human half of the quality story that [Unit Testing](./unit-testing.md) covers
automatically.

## Why it's so high-leverage (three jobs)

1. **It catches bugs** — a *second pair of eyes* finds what the author's
   *over-familiarity* hides. The person who wrote the code has the *most* blind
   spots about it; a fresh reader does not.
2. **It spreads knowledge** — the *cheapest* way to keep a team from becoming a
   set of silos. Everyone learns everyone else's code; the *bus factor* rises
   as a *side effect* of review.
3. **It enforces the standard** — it is where the team's **"what does good look
   like"** gets made *consistent*, culture-level. A team's definition of "clean"
   ([Clean Code](./clean-code.md)) is *taught* through review, not through a document no one
   reads.

## The modern best-practice shape

The *practice* (the *how*) matters as much as the existence of review. The
shape that high-performing teams converge on:

- **Small reviews** — a *few hundred lines* max. A review of 5,000 lines is not
  a review, it's a browse; humans cannot hold that in their head. Large change
  = *split it up.*
- **Fast turnaround** — *hours, not days.* **Review latency is its own form of
  lead time** — a change sitting in "review" for three days is *delaying*
  delivery, dragging on [DORA Metrics](./dora-metrics.md)'s *lead time for changes*. A team's
  review *throughput* is a *deliverable*.
- **Kind, specific feedback** — comment *on the code*, not the *coder*; request
  *changes* rather than *judging*. Psychologically safe review is what makes
  people *want* to ask for it instead of rushing to dodge it.
- **Automated first** — *lint, format, and tests run before a human reads a
  line.* Never spend human attention on what a tool can check. (This is why
  [Continuous Integration & Continuous Delivery (CI/CD)](./ci-cd.md) and [Code Review](./code-review.md) are partners: the *pipeline* does the
  mechanical checks, the *human* does the design/reasoning checks.)

## Related Pages

- [Clean Code](./clean-code.md)
- [Code Smells](./code-smells.md)
- [Continuous Integration/CD](./ci-cd.md)
- [Robert C. Martin](../people/robert-martin.md)

## Sources

- **[Clean Code, Code Review & Craftsmanship](../sources/clean-code-review.md)**
- **[CI/CD, DORA & DevOps](../sources/fowler-ci-cd.md)**

## Maps of Content

- [Code Quality](../pages/code-quality.md)
- [Delivery](../pages/delivery.md)

## See also

- [Continuous Integration & Continuous Delivery (CI/CD)](ci-cd.md)
- [Clean Code](clean-code.md)
- [DORA Metrics](dora-metrics.md)
- [Batch Size](batch-size.md)
- [Queueing & Utilization](queueing-and-utilization.md)
- [Technical Debt](technical-debt.md)
