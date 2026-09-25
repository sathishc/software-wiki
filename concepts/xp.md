---
title: Extreme Programming
tags: [xp, agile, testing, tdd, delivery]
created: 2026-09-25
updated: 2026-09-25
sources: [sources/beck-xp-tdd.md]
layout: default
parent: Concepts
---

# Extreme Programming

**Extreme Programming (XP)** — named by [Kent Beck](../people/kent-beck.md) and the
initial community (Beck, Ward Cunningham, Ron Jeffries, Chuck Cohn, Martin
Fowler, Ken Auer, Dave Thomas; 1998–99, *Extreme Programming Explained*, 1999) —
is a development *method* whose name is a joke: take practices that were *known*
and *good* — but which most teams only applied *partially* and *occasionally* —
and apply them **immediately, continuously, and to the extreme**.

The classic practice set: the *planning game*, *small releases*, a working model,
[Test-Driven Development](./tdd.md), *refactoring*, *pair programming*,
*collective code ownership*, [Continuous Integration](./ci-cd.md), a 40-hour week,
an *on-site customer*, and shared coding standards.

## Why it matters

XP is the **ancestor of most of this wiki's testing and delivery practices**.
Specifically, it is the origin of:

- **TDD** — the red/green/refactor loop as a *daily habit*, not an occasional safety net.
- **Refactoring as a first-class activity** — "you refactor *because* the tests let you",
  which is exactly the dependency described in [Refactoring](./refactoring.md).
- **Continuous integration** — merge-to-main *many times a day* with a green build as the
  contract, later elaborated in [CI/CD](./ci-cd.md).
- **Pair programming** — the human-scale counterpart of [Code Review](./code-review.md):
  review *while* writing, not after.
- **Small releases** — the economic logic that [DORA Metrics](./dora-metrics.md) later
  *measured* (frequent, small deliveries → stability, not fragility).

## The "extreme" is in the *degree*, not the novelty

Each XP practice existed before 1999 in some form (tests, pairs, CI). The novelty
was the **degree**: tests *first* (not some), releases *weekly* (not quarterly),
pairs *always* (not for handoffs), integration *continuously* (not nightly).
That is the transferable insight: **practices are dose-dependent** — half-applied
they often *hurt* (e.g., tests written after the fact that encode the current
bug; pairs used only for the hard parts).

## What has survived, and what hasn't

**Survived** (now standard practice): TDD, refactoring, CI, pair programming,
small batches, an *inspectable* working system.

**Fell away**: the *on-site customer* (replaced by remote async product
collaboration), the *40-hour week* (the human assumption that broke at scale),
and the *small-team-only* framing. That last gap is what later thinking filled:
[X] — when the *team* must scale, you decompose the *system* along the same
boundaries that make XP's feedback loops fast (see [Bounded Context](./bounded-context.md)
and [Microservices](./microservices.md)).

## The honest caveat

XP's economics were demonstrated on *small teams building well-understood
problems* (Smalltalk, Cofense… small web apps of the era). It is a *starting
posture*, not a scaling theory — the delivery map
([Delivery](../pages/delivery.md)) is how the XP instinct generalises.

## Related Pages

- [TDD](./tdd.md) — XP's signature practice
- [Refactoring](./refactoring.md) — the other half of the XP loop
- [CI/CD](./ci-cd.md) — the continuous-integration generalisation
- [Code Review](./code-review.md) — the review practice that replaced "pairs always"
- [DORA Metrics](./dora-metrics.md) — the measured payoff of XP's delivery discipline
