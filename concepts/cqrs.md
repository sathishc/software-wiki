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

## Related

CQRS is often used with [Microservices](./microservices.md), where read models
can be owned by a different service. See also [API Design](./api-design.md)
and [Architecture & Design](../pages/architecture.md).
