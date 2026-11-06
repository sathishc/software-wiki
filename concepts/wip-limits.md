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

## Related

[Cost of Delay](./cost-of-delay.md) gives the economic reason to limit WIP, and
[Delivery](../pages/delivery.md) covers the delivery-side view.
