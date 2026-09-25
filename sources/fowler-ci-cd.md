---
title: "CI/CD, DORA & The DevOps Practice — Fowler, Forsgren et al."
tags: [sources, ci-cd, dora, devops, observability, deployment]
source: https://en.wikipedia.org/wiki/Continuous_integration
ingested: 2026-09-25
---

# CI/CD, DORA & DevOps — Source Notes

**Works:** *Continuous integration* (Fowler, 2002); *Continuous delivery*
(Fowler); **Accelerate: The Science of DevOps** (Forsgren, Humble, Kim, 2018)
— origin of the DORA metrics.

**Reference URLs captured:**
- https://martinfowler.com/articles/continuousIntegration.html
- https://martinfowler.com/bliki/ContinuousDelivery.html
- https://en.wikipedia.org/wiki/Continuous_integration
- https://en.wikipedia.org/wiki/Continuous_delivery
- https://dora.dev/research/ (DORA four keys)

---

## Continuous Integration (CI)

**Continuous integration** is the practice of merging all working copies into
a shared mainline *frequently* (many times a day), with **every merge
automatically built and tested** so integration problems are found within
minutes, not weeks. Fowler's defining quote:

> "The best practice ... is to integrate and test frequently so that problems
> are found quickly and are easy to isolate."

The three pillars: a **version-control system**, an **automated build** (one
command), and an **automated test suite** that must pass before merging.

## Continuous Delivery / Deployment

- **Continuous delivery (CD)** extends CI: every change that passes the
  automated pipeline is *one step away* from production (you can release at any
  time, at low cost, with confidence).
- **Continuous deployment** goes further: every passing change is released to
  production *automatically*, with no human gate.

The enabling insight from *Accelerate*: **reducing batch size and lead time**
(see [Delivery](../pages/delivery.md)) makes *deployment frequency* high and *change-fail rate*
low simultaneously — the two are **negatively correlated with the need for
safety** (a common misconception is that you must choose speed *or* safety; the
data says you can have both).

## The DORA four keys (from *Accelerate*)

The **DORA** (DevOps Research and Assessment) metrics, first published in
*Accelerate* (Forsgren, Humble, Kim, 2018), are the canonical evidence that
software delivery performance is measurable and correlated with business
outcomes:

1. **Deployment frequency** — how often you ship.
2. **Lead time for changes** — time from commit to production.
3. **Change-fail rate** — the fraction of changes that cause a failure.
4. **Time to restore service** (MTTR) — how fast you recover after an incident.

Top-quartile teams are measured in **minutes** for lead time and **hours** for
recovery; bottom-quartile in **months**. The remarkable finding: the top
quartile is **more stable, not less**. This is the empirical backbone of
[DORA Metrics](../concepts/dora-metrics.md).

## Observability

Delivery speed *requires* [Observability](../concepts/observability.md) — the ability to infer a system's
internal state from its external outputs (logs, metrics, traces). **You cannot
shrink your recovery time if you cannot tell what is wrong.** The three
pillars — **logs** (discrete events), **metrics** (quantitative over time), and
**traces** (correlated request paths) — let a team answer "why is it slow or
broken?" without guessing. Pairing fast delivery with *feedback* is the whole
point: fast delivery is only fast if you *find out it was fast* from the
system, not from a postmortem.

---
