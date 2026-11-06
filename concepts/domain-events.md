---
title: Domain Events
tags: [architecture, domain-driven-design, microservices, modeling]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/architecture-patterns-with-python.md]
layout: default
parent: Concepts
---

# Domain Events

A **domain event** is a record of something that happened in the domain, named
in the past tense, such as `BatchAllocated` or `OrderCancelled`. An
[aggregate](./aggregate.md) raises events when a business rule changes its state,
and other parts of the system react to them. In
[Percival and Gregory's](../people/percival-gregory.md) book, events are how a
single-service design grows into an event-driven one without tangling its
parts together.

## Why use them

Events decouple the part of the system that makes a change from the parts
that must respond to it. An aggregate does not need to know that sending an
email or updating a read model is necessary. It records the fact, and a
handler elsewhere acts on it. This keeps aggregates small and keeps
cross-aggregate rules out of single transactions.

## How they flow

The aggregate records events as it changes. The [unit of work](./unit-of-work.md)
collects them when the transaction commits, and only publishes them if the
commit succeeded. Handlers then run, often in the [service layer](./service-layer.md),
and may themselves change other aggregates in their own transactions. This
gives eventual consistency between aggregates rather than a single atomic change.

## Trade-offs

Events make the flow of a use case harder to follow, since the reaction happens
somewhere else. They need careful naming, versioning, and idempotent handlers,
because messages can be delivered more than once. Use them where the decoupling
pays for that cost, not for every internal call.

## Related

Event-driven designs are the basis of many [Microservices](./microservices.md),
and they are the tool for splitting work across [bounded contexts](./bounded-context.md).
See also [Architecture & Design](../pages/architecture.md).
