---
title: Delivery
tags: [moc, delivery, ci-cd, dora, devops]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/fowler-ci-cd.md]
layout: default
parent: Pages
---

# Delivery

> A curated map of *how software *gets from a commit to a running system in
> production, *reliably, and *how the *running* system *tells you* what's
> *happening.* This is the *operational* side of the wiki — the *system* that
> *makes* *fast + *safe* shipping *possible.*

## The one-line idea

**Fast and *safe* are *not in tension — *they are *correlated.*** The
*counterintuitive, *empirical* core of this map (from *Accelerate,* the origin
of the *[DORA Metrics](../concepts/dora-metrics.md)*): *the* teams that ship *most* *frequently* are *the
*most* *stable, not the *least.* You *can* have *both* — but only by *improving
the *whole* *system* (small *batches, *fast *feedback, *automated *pipelines,
and *[Observability](../concepts/observability.md)*), not by *trading* one for the *other.

## How the pieces fit

```
   ┌──────────────────────────────────────────────────────────────────┐
   │                    Continuous Integration  (merge)               │
   │   every change merged *frequently*; *every* merge *built + *tested│
   └───────────────────────────────────┬──────────────────────────────┘
                                       │  *every* *passing* *change* is
                                       ▼
   ┌──────────────────────────────────────────────────────────────────┐
   │            Continuous Delivery / Deployment  (release)           │
   │   *one* *step* *from* *production*  (CD)  /  *auto-released*     │
   │   (continuous *deployment) — *low* *cost, *low* *risk* *release  │
   └───────────────────────────────────┬──────────────────────────────┘
                                       │  *shipped* *to* *production*
                                       ▼
   ┌──────────────────────────────────────────────────────────────────┐
   │                     Observability  (see what's *happening)        │
   │   *logs* · *metrics* · *traces*  →  *detect* + *diagnose* +      │
   │   *restore* — the *feedback* that *makes* *fast* *safe*          │
   └───────────────────────────────────┬──────────────────────────────┘
                                       │  *measured* *by*
                                       ▼
   ┌──────────────────────────────────────────────────────────────────┐
   │                         DORA Metrics  (the *scoreboard*)         │
   │   *frequency* · *lead time* · *fail rate* · *recovery time*      │
   └──────────────────────────────────────────────────────────────────┘
```

And, *upstream* of the pipeline, **[Code Review](../concepts/code-review.md)** is the *human* quality
*gate* — the *second pair of eyes* *before* a change *enters* *CI at all.*

## The synthesis (where these fit together)

- **[Continuous Integration & Continuous Delivery (CI/CD)](../concepts/ci-cd.md)** is the *machine* — *merge *frequently, *automate the *build+
  *test+ *deploy.* It is the *mechanism* by which *small *batches* and *short
  *lead time* *become* *routine* rather than *heroic.*
- **[Observability](../concepts/observability.md)** is the *eyes* — *you cannot *shrink your *recovery time
  if you *cannot *tell what is *wrong.* It is the *feedback* that *makes* *fast
  delivery *safe, and the *reason* *top* *quartile* teams *stay* *stable.*
- **[DORA Metrics](../concepts/dora-metrics.md)** is the *scoreboard* — the *four* *canonical* *metrics*
  (*frequency, *lead time, *fail rate, *recovery time*) that *measure* the
  *system,* *per team,* *over time* — *not* *individuals* (Goodhart's *law*).
- **[Code Review](../concepts/code-review.md)** is the *human gate* *upstream* — the *where the *team's*
  "what does *good* *look like*" gets *made *consistent, *and the *where*
  *review latency* *becomes* *its own* *form of lead time.*

The **unifying thread** is **feedback, *closed***: a *delivery* *system is* a
*feedback loop, *shrunk* *end-to-end — *from* *"I changed *code"* *to* *"I know
it *integrated"* (*CI), *to* *"I know it *shipped"* (*CD), *to* *"I know how it
*behaved in *production"* (*observability), *measured* *as* *"is the *system*
*getting *better"* (*DORA). *Every* *box above is *one* *link in that loop,
and *the* *whole* *point is to *keep *that loop *short.*

## The key people

- **[Martin Fowler](../people/martin-fowler.md)** — the *defining* *articles* on *CI* and *CD* (*the*
  *bliki* *essays* that *named* and *explained* the *practice).
- **Genevieve *Forsgren, *Nurse Humble, *Maxim *Kim** — *Accelerate* (*the*
  *origin* of the *DORA* *metrics*; *the* *evidence* that *speed* and *reliability
  are *correlated, not *in *tension.)

## Recommended reading order

1. **[Delivery](./delivery.md)** (you are here — the map).
2. **[Continuous Integration & Continuous Delivery (CI/CD)](../concepts/ci-cd.md)** — the *machine* (and *why* *small *batches* is *the* *lever).
3. **[DORA Metrics](../concepts/dora-metrics.md)** — the *scoreboard* (and *the* *remarkable* *finding*).
4. **[Observability](../concepts/observability.md)** — the *eyes* (and *why* *you cannot* *skip* it).
5. **[Code Review](../concepts/code-review.md)** — the *human gate* *upstream* (and *the* *latency* *tax*).

## Related Maps of Content

- [Code Quality](./code-quality.md) — the *craft* that *survives* the
  *velocity* *pressure* *of shipping.*
- [Architecture & Design](./architecture.md) — the *boundaries* that *delivery
  ships across* (*services* and *APIs* are *delivery* *units*).
- [Lean Product Development](./lean-product-development.md) — the *economic*
  case behind *small batches* and *fast feedback*: why *queues* and *cost of
  delay*, not *busyness*, decide how *quickly* *value* *ships*.

## See also

- [Building Software with AI Agents](./ai-agents-software-engineering.md) — how agent-built code is tested, reviewed and delivered.
