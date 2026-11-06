---
title: DORA Metrics
tags: [dora, devops, delivery, ci-cd, observability]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/fowler-ci-cd.md]
layout: default
parent: Concepts
---

# DORA Metrics

The **DORA metrics** (DevOps Research and Assessment) are a small, canonical set
of **four** software-delivery *throughput and stability* metrics, first
published in *Accelerate: The Science of DevOps* (Forsgren, Humble, Kim, 2018).
They are the standard *evidence* that delivery performance is **measurable** and
that it **correlates with business outcomes** — the empirical backbone of
[Delivery](../pages/delivery.md) and of [Continuous Integration & Continuous Delivery (CI/CD)](./ci-cd.md).

## The four keys

| Metric | What it measures | Direction |
|---|---|---|
| **Deployment frequency** | How often you release to production | Higher is better |
| **Lead time for changes** | Time from *commit* to *production* | Lower is better |
| **Change-fail rate** | Fraction of changes that cause a failure (or require rollback) | Lower is better |
| **Time to restore service** (MTTR) | How fast you *recover* after an incident | Lower is better |

## Why the four are chosen (and the remarkable finding)

These four were selected because they capture the two things a delivery system
must balance — **speed** (the first two) and **stability** (the last two) — in a
way that *correlates with revenue, profitability, and time-to-market.* The
*striking* finding from *Accelerate* is that **the top-performing quartile is
*more* stable, not *less***: teams with the *highest* deployment frequency and
*shortest* lead time also have the *lowest* fail rate and *fastest* recovery.

That **breaks the assumed trade-off** ("if you ship faster you *must* ship more
bugs") and is the *core* justification for CI/CD and for investing in delivery:
**you can have *both* speed and reliability**, but only by improving the whole
system (small batches, fast feedback, automated pipelines, [Observability](./observability.md))
— you *cannot* buy one without the other.

## How to use them (the honest caveats)

- They are **leading indicators of a *system*, not a *person*.** Do **not** use
  them as individual performance metrics — that is a well-documented failure
  mode (Goodhart's law: a metric becomes a *target* and stops being a good
  measure). They are for *improving the system*, tracked *per team*, not per
  engineer.
- **Track *trends*, not point-in-time scores.** The point is to see whether the
  system is *getting better*; a single number in a vacuum tells you little.
- They *complement* (don't replace) **[Observability](./observability.md)**: DORA measures the
  *delivery* system; observability measures the *running* system.

## Related Pages

- [Continuous Integration/CD](./ci-cd.md)
- [Observability](./observability.md)

## Sources

- **[CI/CD, DORA & DevOps](../sources/fowler-ci-cd.md)**

## Maps of Content

- [Delivery](../pages/delivery.md)

## See also

- [Continuous Integration & Continuous Delivery (CI/CD)](ci-cd.md)
- [Observability](observability.md)
- [Batch Size](batch-size.md)
- [Cost of Delay](cost-of-delay.md)
- [Code Review](code-review.md)
