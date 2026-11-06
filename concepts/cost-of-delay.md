---
title: Cost of Delay
tags: [lean, flow, economics]
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

## Worked example

Suppose two features compete for the same team. Feature A is worth about
£20,000 for every week it is not live, because it captures a seasonal sales
window, and it will take four weeks to build. Feature B is worth about £8,000
a week, because it reduces support load steadily, and it will take one week.
Ordered by priority, the team might pick A first. Ordered by WSJF, the
calculation is A at £20,000 ÷ 4 = £5,000 per week of effort, and B at
£8,000 ÷ 1 = £8,000 per week of effort. B goes first. Doing B first delays A
by one week, which costs £20,000, but it brings forward £8,000 of value per
week for the whole duration of A's build. The arithmetic depends on the
estimates, but the shape of the decision is the point: a short job that
stops a steady loss can beat a larger job with a bigger headline value.

## Shapes of delay cost

Not every item loses value at the same rate. A **fixed-date** item, such as a
trade show or a regulatory deadline, loses nothing until the date and then
loses almost everything, so its cost of delay is a step, not a slope. A
**steady** item loses value linearly, such as a cost saving. A **decaying**
item loses value faster as time passes, such as a feature that competitors
are about to make obsolete. Estimating the shape matters as much as the size,
because the same average cost can hide very different sequencing decisions.

## Estimating in practice

Teams usually split the cost of delay into three parts: time-criticality (how
much value falls as time passes), risk reduction or opportunity enablement
(what the item unlocks or protects later), and direct value. Estimates should
be rough and compared, not precise. A useful habit is to ask "what does one
more week of waiting cost us?" for each candidate, and to write the answer
down so it can be challenged.

## When not to use it

Cost of delay is not worth the effort for work with no economic consequence
of timing, such as internal refactors with no deadline, or for a team where
every item is equally urgent by external commitment. It is also a poor fit for
exploratory research whose value is unknown, where the first task is to
learn enough to estimate anything at all.

## Common mistakes

Teams often confuse cost of delay with priority or with deadline. A deadline
is one input, not the whole measure. Others estimate the value of the feature
and forget to model its delay cost, which is the rate at which that value
falls away. A third common error is to use WSJF with duration estimates that
are much less reliable than the value estimates, which lets a guess about
size dominate the decision.
