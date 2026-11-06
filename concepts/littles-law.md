---
title: Little's Law
tags: [lean, flow, queueing, economics]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/reinertsen-product-development-flow.md]
layout: default
parent: Concepts
---

# Little's Law

**Little's Law** is a theorem from queueing theory, stated by John Little (1961):
for a stable system, the average amount of work in the system equals the
average arrival (throughput) rate multiplied by the average time each item
spends in the system.

    L = λ × W

where L is average work in progress, λ is throughput, and W is average cycle
time. It holds regardless of arrival pattern or processing order,
which is what makes it so useful.

## Why product development uses it

[Donald G. Reinertsen](../people/donald-reinertsen.md) relies on this relation
as the bookkeeping behind his flow arguments. If throughput is fixed, then
reducing [work in progress](./wip-limits.md) reduces cycle time proportionally.
If you want faster delivery without working harder, you reduce WIP; you do not
need to demand higher throughput from people who are already busy.

## Worked intuition

Suppose a team completes 5 items a week on average. If 20 items are in progress,
each item takes about 4 weeks to finish, since $W = L / \lambda = 20 / 5$. If
WIP is cut to 10, the average cycle time falls to about 2 weeks, with the same
throughput. The team is not faster; it is waiting less.

## Caveats

The law assumes a stable system whose averages are taken over a long enough
window. It describes averages, not individual items, and it does not tell you
which bottleneck to fix. For that, the [queueing](./queueing-and-utilization.md)
and [batch size](./batch-size.md) arguments are needed.

## Related

[Cost of Delay](./cost-of-delay.md) shows what the extra cycle time costs, and the
[Lean Product Development](../pages/lean-product-development.md) map ties the
relation to the wider flow framework.
