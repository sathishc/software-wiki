---
title: Work-in-Progress (WIP) Limits
tags: [lean, flow, queueing, economics]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/reinertsen-product-development-flow.md]
layout: default
parent: Concepts
---

# Work-in-Progress (WIP) Limits

A **WIP limit** is a cap on how many items may be in progress at once in a
part of the system. [Donald G. Reinertsen](../people/donald-reinertsen.md)
treats WIP constraints as one of the main tools for controlling flow: they
bound the size of [queues](./queueing-and-utilization.md) directly, and so
bound the time work spends waiting.

## The mechanism

Work in progress and cycle time are linked. For a steady flow, more items in
progress means each item waits longer before it finishes. [Little's Law](./littles-law.md)
states the exact relation. Capping WIP therefore caps cycle time, and a short
cycle time is what gets feedback and value to the customer sooner.

## What the principles say

As reported in summaries of the book, WIP constraints control cycle time and
flow, and they force the rate of work arriving at a stage to match the rate it
can be completed. Reinertsen also discusses WIP *ranges* as a way to decouple
the batch sizes of adjacent processes, so that a stage working in larger
batches does not stall a stage working in smaller ones.

## Trade-off with utilisation

A WIP limit means some people will sometimes be idle. This looks like waste to
a manager focused on utilisation, but it is the slack that keeps queues short.
Reinertsen's point, developed in [Queueing & Utilization](./queueing-and-utilization.md),
is that a small amount of idle capacity is cheap compared with the delay that
high utilisation causes.

## Practice in software

WIP limits are the core of [kanban](../pages/lean-product-development.md), and they
show up in engineering as limits on open pull requests, in-flight stories per
team, and concurrent feature branches. These connect to the
[Batch Size](./batch-size.md) discussion: a WIP limit and a smaller batch size
usually work together.

## Worked example

A team of three developers working on a board with stages "in progress",
"review", and "done" has eight items in progress. Each person is holding about
three items, switching between them, and none finishes quickly. With a limit
of three items in progress across the team, the team must finish something
before starting the next item. Work finishes sooner, the review stage is no
longer overloaded, and the team's throughput stays about the same while the
average time per item falls. Little's Law gives the reason: if throughput is
fixed, cutting work in progress cuts cycle time in direct proportion.

## Choosing a limit

A reasonable starting point is the number of people in the stage, plus a small
margin, and then adjust based on observed flow. The limit should be set for
each stage or flow, not for each person, because the constraint is the queue
between stages. Setting it too low starves the team and leaves people idle,
which is a visible signal that the limit needs raising. Setting it too high
does nothing useful.

## Blocked work and the limit

Work that is blocked still counts. An item waiting on a dependency or an
external answer occupies a slot. Teams often find it useful to mark blocked
items explicitly and to escalate them, since a limit that is full of blocked
work stops everything else.

## When not to use it

Work that is truly independent, with no shared stage and no queue, does not
need a limit. Unplanned operational work, such as incidents, is often better
handled by a separate capacity than by squeezing it into a shared limit.

## Common mistakes

Teams often set a WIP limit but do not enforce it, which turns it into a
suggestion. Another is to set the limit per person, which lets the queue
between people grow unchecked. A third is to raise the limit whenever the
team is busy, which is exactly the situation the limit was meant to prevent.

## Related

[Cost of Delay](./cost-of-delay.md) gives the economic reason to limit WIP, and
[Delivery](../pages/delivery.md) covers the delivery-side view.
