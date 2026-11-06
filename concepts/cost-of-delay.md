---
title: Cost of Delay
tags: [lean, flow, economics, sequencing]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/reinertsen-product-development-flow.md]
layout: default
parent: Concepts
---

# Cost of Delay

The **cost of delay** is the economic loss incurred for each unit of time that
a piece of value stays undelivered. It is the central economic quantity in
[Donald G. Reinertsen](../people/donald-reinertsen.md)'s second-generation lean
view of product development: a feature is not "cheap" or "expensive" in
isolation, its worth depends on how long it waits.

Reinertsen's most-quoted advice is that if you only quantify one thing in
product development, quantify the cost of delay. The reason is that it turns
a vague sense of urgency into a number you can compare across items.

## Why it matters

Most teams order work by priority, deadline, or the loudest stakeholder. Cost
of delay asks a different question: *what does each week of waiting cost us?*
Two items with the same value can have very different urgency. A feature that
captures a time-limited market window loses value steeply; a feature for a
stable, slow-moving need loses almost nothing per week. Ignoring this makes
the team deliver the second kind first.

## Sequencing with WSJF

When items differ in both cost of delay and duration, the book's scheduling
rule is **weighted shortest job first (WSJF)**: divide the cost of delay by the
job's duration, and do the highest ratio first. Short, high-urgency work goes
first; long, low-urgency work waits. When durations are roughly equal, the
rule collapses to "do the highest cost-of-delay item first."

## How this connects to the rest of the map

Cost of delay explains why [queues](./queueing-and-utilization.md) are
expensive: every item sitting in a queue is accruing delay cost. It is the
reason to keep [batch sizes](./batch-size.md) small and [WIP limits](./wip-limits.md)
tight, since both shorten the time items spend waiting. The
[Lean Product Development](../pages/lean-product-development.md) map treats it as
the starting point for its economic argument.

The same idea appears in software delivery as the value of shipping sooner,
which the [DORA Metrics](./dora-metrics.md) capture indirectly through lead time.

## Caveats

Cost of delay is hard to estimate precisely. The value of the discipline lies
in making the estimate explicit and arguing about it, not in the decimal
places. Treat it as a comparative tool, not an accounting figure.
