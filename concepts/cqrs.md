---
title: CQRS (Command Query Responsibility Segregation)
tags: [architecture, microservices, api-design, modeling]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/architecture-patterns-with-python.md]
layout: default
parent: Concepts
---

# CQRS (Command Query Responsibility Segregation)

**CQRS** separates the operations that change state (**commands**) from the
operations that read it (**queries**), and lets each side use its own model.
Commands go through the domain, with its invariants and [aggregates](./aggregate.md).
Queries can read from a data shape designed for display, without loading
aggregates at all. [Percival and Gregory](../people/percival-gregory.md) discuss
it as a way to keep the write model clean while still serving efficient reads.

## The core idea

The domain model is built for enforcing rules, which means it is often
awkward for reporting. A list page that shows thousands of items should not
need to load every aggregate that backs them. CQRS lets reads come from a
projection, a table or view built for that page, while writes continue through
the [service layer](./service-layer.md) and the domain.

## How the two sides connect

The write side publishes [domain events](./domain-events.md) when state changes.
Handlers update the read-side projections from those events. This makes the
read model eventually consistent with the write model, which is the main
price of the pattern.

## When it is worth it

CQRS suits systems where reads and writes have very different shapes or load,
and where the domain's rules are complex enough to justify keeping them apart.
It is overkill for a simple create-read-update-delete application. Applying it
everywhere is a common mistake.

## Worked example

An order system has a write side that enforces rules through aggregates and
the service layer. A customer's order-history page, however, needs to show
hundreds of orders with totals and statuses, filtered and sorted. Loading
aggregates to build that page would be slow and awkward. Instead, each order
event updates a read table shaped exactly for the page. The page queries that
table directly. Writes still go through the domain and its rules, and reads
never change state.

## Why the split helps

The domain model is designed to protect invariants, which makes it a poor
shape for reporting. Separating the two lets each side be optimised and
evolved independently. The read model can be rebuilt from events if its
design changes, which makes experimentation cheaper.

## Consistency

The read side is usually eventually consistent with the write side, so a user
may briefly not see their own change. Teams handle this with UI choices, such
as showing a pending state, or by reading from the write side for the item the
user has just changed. The lag should be measured and monitored, not assumed to
be negligible.

## When not to use it

For a create, read, update and delete application where reads and writes look
alike, CQRS adds two models and a synchronisation mechanism for no benefit.
Applying it everywhere is a common and costly mistake. It is best applied to a
specific part of a system where the read and write needs diverge sharply.

## Common mistakes

Letting a query change state turns the read side into a second write path with
no rules. Building read models without monitoring their lag hides stale data
until a user reports it. Splitting into separate services before understanding
the domain tends to produce distributed complexity with no clear gain.

## Related

CQRS is often used with [Microservices](./microservices.md), where read models
can be owned by a different service. See also [API Design](./api-design.md)
and [Architecture & Design](../pages/architecture.md).
