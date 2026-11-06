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

## Worked example

A support team closes about 12 tickets a week, which is its throughput. At any
moment about 36 tickets are open, which is its work in progress. Little's Law
gives the average time each ticket spends open: 36 ÷ 12 = 3 weeks. If the team
wants a two-week average, it does not need to work faster. It needs to hold
about 24 tickets open at a time. The same arithmetic lets a manager estimate
the effect of a process change before making it, using only the current
throughput and the proposed change in open work.

## Preconditions

The law applies to a system in a steady state, where the amount of work in the
system is roughly stable over the period being measured. If work is piling up
faster than it is completed, the averages drift and the relationship gives
misleading answers. It applies to averages, not to individual items, and it
holds regardless of the order in which items are processed or how they arrive,
which is what makes it so widely useful.

## Applying it to a part of the system

Because the law is about any stable system, it can be applied to a single stage.
A review stage with a steady throughput and a known number of items waiting
gives its own cycle time. This is often the most useful use of the law, since
it identifies which stage is holding work the longest.

## When not to use it

When work arrives in bursts, or the system is growing, the steady-state
assumption fails and the numbers should be read with caution. The law also
does not say which stage to change; it only describes the relationship. For
that, the [queueing](./queueing-and-utilization.md) and
[batch size](./batch-size.md) arguments are needed.

## Common mistakes

A frequent error is to measure throughput over a short window during a burst
and then apply it to a long-run plan. Another is to mix definitions, counting
"in progress" in one place and "in the system" in another, which makes the
arithmetic appear to disagree with itself.

## Related

[Cost of Delay](./cost-of-delay.md) shows what the extra cycle time costs, and the
[Lean Product Development](../pages/lean-product-development.md) map ties the
relation to the wider flow framework.

## See also

- [Queueing & Utilization](queueing-and-utilization.md)
- [Work-in-Progress (WIP) Limits](wip-limits.md)
- [Batch Size](batch-size.md)
- [Cost of Delay](cost-of-delay.md)
