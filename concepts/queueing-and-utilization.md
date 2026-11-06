---
title: Queueing & Utilization
tags: [lean, flow, queueing, economics]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/reinertsen-product-development-flow.md]
layout: default
parent: Concepts
---

# Queueing & Utilization

In product development, work spends most of its life **waiting**, not being
worked on. [Reinertsen](../people/donald-reinertsen.md)'s core diagnostic is that the queue, not the worker, is
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

## Worked example

For a single server with random arrivals and service times, the expected
waiting time in the queue, relative to the average service time, grows with
the factor ρ / (1 − ρ), where ρ is utilisation. At 50% busy the factor is 1.
At 80% it is 4. At 90% it is 9. At 95% it is 19. So a team that moves from
80% to 95% utilisation does not get 19% slower; its waiting time roughly
quadruples relative to its service time. Nothing about the people changed.
Only the amount of spare capacity did, and the queue absorbed the difference.

## Why spare capacity is not waste

A system with slack can absorb variability when it arrives. A system with
none passes every irregular arrival straight into a queue, and the queue
delays everything behind it. The apparent inefficiency of an idle engineer is
the cost of keeping the queue short, which is usually far cheaper than the
delay it prevents.

## Diagnosing a queue

Queues are visible if you look for them. Look for work that is "in review",
"waiting for QA", "blocked on a dependency", or "ready for release" for days.
Measure the age of items in each state rather than only their count. Where
the age is large and the state is a handoff, the queue is probably the
bottleneck, even if the people in that state look busy.

## When not to use it

The queueing argument assumes the system is not fully deterministic. A
perfectly regular process with fixed arrival times and fixed durations has no
queueing delay at full utilisation, so the exponential effect does not apply.
It also says little about single items; it describes behaviour across many.

## Common mistakes

The most frequent error is to measure individual productivity and push
utilisation up, which raises queue size and cycle time together. A second is
to add people to a queue that is limited by a single approval step; the queue
stays the same length, but now more people wait. A third is to treat a small
queue as proof of health without checking the age of the items in it.

## See also

- [Little's Law](littles-law.md)
- [Work-in-Progress (WIP) Limits](wip-limits.md)
- [Batch Size](batch-size.md)
- [Cost of Delay](cost-of-delay.md)
