---
title: Lean Product Development
tags: [moc, lean, flow, economics, queueing]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/reinertsen-product-development-flow.md]
layout: default
parent: Pages
---

# Lean Product Development

> A curated map of how product development creates economic value through
> *flow*. Its core claim is that the thing to manage is not utilisation or
> effort, but the time work spends waiting, and the cost of that waiting.

## The one-line idea

**Manage the flow of value, not the busyness of people.** Reinertsen's
second-generation lean argument is that queues, not workers, dominate
development performance, and that the economics of delay should decide what
gets done next.

## How the pieces fit

The chain runs from economics to mechanics to practice. [Cost of Delay](../concepts/cost-of-delay.md)
says what waiting costs and so sets the priority. [Queueing & Utilization](../concepts/queueing-and-utilization.md)
explains why waiting happens and why high utilisation makes it explode.
[Little's Law](../concepts/littles-law.md) gives the exact bookkeeping that ties
work in progress to cycle time. The two levers that act on that bookkeeping are
[Work-in-Progress Limits](../concepts/wip-limits.md), which cap how much is in
flight, and [Batch Size](../concepts/batch-size.md), which shrinks each unit that
moves. Put together, the map says: decide by cost of delay, limit work in
progress, shrink batches, and accept some idle capacity as the price of short
queues.

## Reading order

1. [Cost of Delay](../concepts/cost-of-delay.md) — the economic question that
   every other principle answers to.
2. [Queueing & Utilization](../concepts/queueing-and-utilization.md) — the
   mechanism behind delay.
3. [Little's Law](../concepts/littles-law.md) — the arithmetic linking queues to
   cycle time.
4. [Work-in-Progress Limits](../concepts/wip-limits.md) — the first control lever.
5. [Batch Size](../concepts/batch-size.md) — the second control lever.

## Key people

- **[Donald G. Reinertsen](../people/donald-reinertsen.md)** — author of
  *The Principles of Product Development Flow* (2009) and the source for every
  concept on this map.

## Connections to software delivery

Reinertsen's ideas are the economic basis for the software practices already in
the wiki. Small batches and fast feedback are what [Continuous Integration & Continuous Delivery (CI/CD)](../concepts/ci-cd.md)
automates. The [DORA Metrics](../concepts/dora-metrics.md) are an empirical test
of the claim that smaller, more frequent flow improves both speed and stability.
The [Delivery](./delivery.md) map covers the operational side, and
[Technical Debt](../concepts/technical-debt.md) can be read as a queue of deferred
work that keeps accruing interest.

## Analysis: where the wiki stood, and what this adds

Before this ingest the wiki held four Maps of Content, five people, twenty
concepts, and seven source notes. Nothing covered economics, queueing, or flow
as subjects in their own right. The delivery and code-quality maps touched flow
only implicitly, through small changes and lead time, without the economic or
queueing reasoning behind them. This page and its five concept pages fill that
gap, and the Reinertsen person page and source note give the economic framing
its provenance.

Several gaps remain. There is no concept page on variability, which the book
treats as a separate lever. There is no page on pull systems or kanban as a
practice, though WIP limits point toward them. Cadence, synchronisation, and
decentralised control are also unrepresented. Finally, the Reinertsen source
note is compiled from secondary summaries, so its principle codes should be
verified against the book before anyone cites them.

A lint pass found no orphan pages and no broken relative links among the new
files. It also surfaced problems that predate this ingest and were left
unchanged: several lines in `index.md` have malformed link syntax (for example
the [Domain-Driven Design](../concepts/domain-driven-design.md) and Robert Martin entries), and some existing pages
contain stray emphasis markers. These are recorded here for a separate cleanup.
