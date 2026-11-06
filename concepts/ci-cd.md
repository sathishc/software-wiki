---
title: Continuous Integration & Continuous Delivery (CI/CD)
tags: [ci-cd, devops, delivery, deployment, testing]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/fowler-ci-cd.md]
layout: default
parent: Concepts
---

# Continuous Integration & Continuous Delivery (CI/CD)

**CI/CD** is the *delivery* practice of merging small changes **frequently**
and *automating* the work that turns a change into production — the **build,
test, package, and deploy** steps — so that getting a change into production is
**cheap, fast, and low-risk** rather than a periodic, high-stress event. It is
the operational backbone of [Delivery](../pages/delivery.md) and the mechanism behind the
[DORA Metrics](./dora-metrics.md).

## Continuous Integration (CI)

**Continuous integration** is the *merging* half: every working copy is
merged into a shared mainline **many times a day**, and **every merge triggers
an automated build + test** (Fowler, 2002). The defining idea:

> Integrate and test *frequently* so that problems are found *quickly* and are
> *easy to isolate* — the cost of an integration bug scales with *how long* it
> has gone unfound.

The three pillars: a **version-control system** (a shared trunk everyone merges
into), an **automated build** (one command, reproducible), and an **automated
test suite** that must *pass* before a merge lands. The *point* is to keep the
**feedback loop** (from "I changed code" to "I know it integrates") to minutes,
not weeks.

## Continuous Delivery / Continuous Deployment

The *deployment* half, with two related but distinct ends:

- **Continuous delivery (CD)** — every change that *passes the full automated
  pipeline* is **one step away** from production. You *can* release at any
  moment, at low cost, with confidence; the *release* itself is a deliberate
  (often human) decision.
- **Continuous deployment** — every *passing* change is released to
  production **automatically**, with no human gate. This is only *safe* when the
  pipeline and the [Observability](./observability.md) in production are strong enough that an
  automated release is *trustworthy* and *fast to roll back* if wrong.

## Why it's the delivery lever

The *Accelerate* evidence (the origin of the [DORA Metrics](./dora-metrics.md)): **small batch
size + short lead time** is what makes *deployment frequency* high and
*change-fail rate* low **at the same time**. The counterintuitive, and
central, finding: the teams that ship *most* frequently are the **most stable,
not the least** — speed and reliability are *correlated*, not in tension. A
team that ships once a quarter in a giant, high-risk release is *both* slow and
fragile; a team that ships continuously is *both* fast and resilient. That is
the whole argument for CI/CD, and it is why CI/CD is the *mechanism* by which
[Delivery](../pages/delivery.md) happens — see [DORA Metrics](./dora-metrics.md) for how you *measure* whether it's
working.

## Related Pages

- [DORA Metrics](./dora-metrics.md)
- [Observability](./observability.md)
- [Code Review](./code-review.md)
- [Test Pyramid](./test-pyramid.md)

## Sources

- **[CI/CD, DORA & DevOps](../sources/fowler-ci-cd.md)**

## Maps of Content

- [Delivery](../pages/delivery.md)

## See also

- [DORA Metrics](dora-metrics.md)
- [Batch Size](batch-size.md)
- [Observability](observability.md)
- [Code Review](code-review.md)
- [Test Pyramid](test-pyramid.md)
- [Test-Driven Development (TDD)](tdd.md)
