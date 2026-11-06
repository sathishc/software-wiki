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

## Worked example

Consider a team that releases a feature once a month, and so batches a month
of work into one release of roughly 1,200 changed lines. A bug found in
production takes weeks to trace, because it could be in any of dozens of
changes. Now consider the same team releasing every day, with batches of
about 40 lines. A bug is usually traced to a single day's change, and the fix
ships the same day. The total work is about the same, but the second team
learns in hours and the first learns in weeks. The difference is not effort;
it is the size of the unit that moves.

## The transaction cost trade-off

Smaller batches are not free. Every batch has a fixed cost to move: writing
the release note, running the deployment, getting a review, handing off to
another person. If that fixed cost is large, small batches cost more in total,
which is why the knob is only useful when the transaction cost is reduced.
Automation, standard interfaces, and cheap validation are how teams push the
fixed cost down far enough that small batches win.

## Batches hide in unexpected places

A small pull request that waits three days for review is still a large batch
in terms of time. The batch is the set of changes waiting for the same
reviewer, not the diff. The same holds for a stack of ten small changes merged
together on Friday. Batching often reappears at the handoffs, so reducing the
batch in one stage can leave the queue in the next stage intact.

## When not to use it

When there is no feedback loop to speed up and no risk that is cheaper to
discover early, the batch size may matter little. Some work has a natural
unit that cannot be split without losing meaning, such as a regulatory
change that must go live atomically.

## Common mistakes

Teams often shrink the release but not the review, or split the work into
small tickets but keep the same release train. Another mistake is to treat
batch size as a rule to apply without measuring transaction cost, which
produces many tiny batches that each cost more than they save.

## Related

[Cost of Delay](./cost-of-delay.md) explains why waiting is expensive, and
[Work-in-Progress Limits](./wip-limits.md) is the complementary lever that
constrains how much is in flight at once.

## See also

- [Cost of Delay](cost-of-delay.md)
- [Work-in-Progress (WIP) Limits](wip-limits.md)
- [Little's Law](littles-law.md)
- [Continuous Integration & Continuous Delivery (CI/CD)](ci-cd.md)
- [DORA Metrics](dora-metrics.md)
- [Queueing & Utilization](queueing-and-utilization.md)
