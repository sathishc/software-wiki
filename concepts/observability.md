---
title: Observability
tags: [observability, devops, delivery, deployment, testing]
created: 2026-09-25
updated: 2026-09-25
sources: [sources/fowler-ci-cd.md]
layout: default
parent: Concepts
---

# Observability

**Observability** is the property of a *running* system: the ability to **infer
its internal state from its external outputs** — without having to *be* inside
it, and *especially* in a production incident, where you cannot reproduce the
state in a lab. It is the *feedback* half of fast [Delivery](../pages/delivery.md): **you cannot
shrink your recovery time if you cannot tell what is wrong.**

## The three pillars

| Pillar | What it is | Answers |
|---|---|---|
| **Logs** | Discrete, timestamped *events* (a structured record of what happened) | *What* happened, *when*, with context |
| **Metrics** | Quantitative values *over time* (counters, gauges, histograms) | *How much / how fast* (latency, error rate, throughput) |
| **Traces** | *Correlated* records of a single request's path *through* the system | *Where* in the flow did it slow down or fail |

Logs tell you *what* happened at a point; metrics tell you *how* a system is
behaving *over time* (and let you alert); traces let you follow a *single
request* across services to find the *specific* hop that misbehaved. In a
distributed system ([Microservices](./microservices.md)), **traces are what make it possible to
answer "which of the twenty services did this go through, and where did it
stall?"**

## Why it's the enabler of speed

This is the *deep* link to [Delivery](../pages/delivery.md) and [DORA Metrics](./dora-metrics.md): the top-quartile
teams *shipped fast and stayed stable* **because they could *see* what was
happening** — fast enough to *detect* a bad release in seconds and *roll it
back* (a low *time to restore service*), and *understandable* enough to diagnose
a new problem that no one had seen before. Observability is the difference
between:

- **"The dashboard went red, we can't see *why*, we're guessing"** (not
  observable) — slow, risky recovery.
- **"The dashboard went red, *this* metric spiked, *this* trace shows the error
  in *this* service, we rolled back in 4 minutes"** (observable) — fast,
  confident recovery.

That is why **you do not get to skip observability** and still be able to ship
continuously: **fast delivery without observability is fast *breakage*.**

## Related Pages

- [Continuous Integration/CD](./ci-cd.md)
- [DORA Metrics](./dora-metrics.md)
- [Microservices](./microservices.md)

## Sources

- **[CI/CD, DORA & DevOps](../sources/fowler-ci-cd.md)**

## Maps of Content

- [Delivery](../pages/delivery.md)
