---
title: Batch Size
tags: [lean, flow, economics, ci-cd, delivery]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/reinertsen-product-development-flow.md]
layout: default
parent: Concepts
---

# Batch Size

**Batch size** is the amount of work released or handed off as a single unit.
In [Donald G. Reinertsen](../people/donald-reinertsen.md)'s framework, reducing
batch size is one of the most powerful and most under-used levers in product
development. It affects cycle time, variability, risk, and overhead all at once.

## What smaller batches buy

Reinertsen's principles (as reported in summaries) say that reducing batch size
reduces cycle time, and that it reduces variability in flow. A small batch
moves through the system faster, so it waits less in [queues](./queueing-and-utilization.md),
and because it moves more often the timing of each movement is more predictable.

Smaller batches also reduce **risk**. A failure in a small batch is cheap to
find and cheap to undo. A failure buried in a large batch is discovered late,
when fixing it means unpicking everything built on top.

## The cost of small batches

Small batches are not free. Each batch carries a **transaction cost**: the
setup, handoff, testing, and approval overhead. Reinertsen's argument is that
the economics favour small batches as long as the transaction cost is kept low.
So the real work is reducing the fixed cost per batch, through automation,
standard interfaces, and cheap validation, not simply deciding to do less at once.

## Why large batches grow out of control

Large batches tend to produce schedule and cost growth that is worse than
linear, because integration problems and rework compound. This is part of why
large projects so often run late and over budget.

## Software delivery

The same logic is the basis of [Continuous Integration & Continuous Delivery (CI/CD)](./ci-cd.md):
merge small changes frequently, and automate the transaction cost so that a
small batch is cheap to verify and ship. The [DORA Metrics](./dora-metrics.md)
show the empirical result: teams that ship in smaller, more frequent batches
tend to be both faster and more stable. See also the [Delivery](../pages/delivery.md)
map.

## Related

[Cost of Delay](./cost-of-delay.md) explains why waiting is expensive, and
[Work-in-Progress Limits](./wip-limits.md) is the complementary lever that
constrains how much is in flight at once.
