---
title: Queueing & Utilization
tags: [lean, flow, queueing, economics, variability]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/reinertsen-product-development-flow.md]
layout: default
parent: Concepts
---

# Queueing & Utilization

In product development, work spends most of its life **waiting**, not being
worked on. Reinertsen's core diagnostic is that the queue, not the worker, is
where most of the economic damage happens. Every item in a queue accrues
[cost of delay](./cost-of-delay.md), and the queue's length is what determines
how long each item waits.

## The utilization trap

Queueing theory has a counterintuitive result that Reinertsen puts at the
centre of the book. As a resource approaches full utilisation, the expected
queue length grows non-linearly, and then explodes. A team that is 95% busy
has far more waiting work than one that is 80% busy, even though it is only
slightly "more productive." Maximising utilisation therefore maximises queues
and delay.

This is why the book argues against managing for busy-ness. Keeping
spare capacity is not waste; it is the slack that lets work move through
without waiting.

## Variability in the queue

Variability is the other half of the mechanism. Irregular arrivals and uneven
task durations create queues even when average load looks fine. Reinertsen's
point is that variability is not always bad and can sometimes be exploited,
but it must be managed where it accumulates, which is in queues. Shrinking
queues absorbs variability instead of passing it downstream.

## Practical implications

Three levers follow from the mechanism. You can reduce queue size by
[limiting work in progress](./wip-limits.md). You can reduce the size of each
queued item with [smaller batches](./batch-size.md). You can shorten how long
items wait through cadence and faster feedback, which the
[Lean Product Development](../pages/lean-product-development.md) map covers.

## Relation to Little's Law

[Little's Law](./littles-law.md) gives the exact relation between the amount
of work in a system, its throughput, and the time each item spends in it. It
is the bookkeeping that makes the queueing argument concrete.

## Connection to software delivery

Long-lived branches, large merges, and review backlogs are queues. The
[Delivery](../pages/delivery.md) map's preference for small, frequent changes is
the same utilisation-and-queue argument applied to code.
