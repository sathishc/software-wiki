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

## Worked example

When an allocation fails because stock is short, the aggregate records an
`OutOfStock` event naming the sku. After the transaction commits, a handler
reacts to it by sending a notification to the purchasing team and creating a
restock request. The allocation code does not know that emails or purchasing
exist. Adding a new reaction later, such as updating a dashboard, means adding
a handler, not editing the allocation logic.

## Designing good events

Name events in the past tense, since they record facts that happened, such as
`BatchAllocated` or `OrderCancelled`. Include the data a reader needs to act on
the fact without calling back into the source. Keep events about the domain,
not about the implementation: `PaymentReceived` is a domain fact, whereas
`RowInserted` is a storage detail that should not leak out.

## Reliability

Events are usually delivered after the commit, so a failure after commit can
lose them unless there is a durable outbox. Handlers may run more than once,
so each one should be idempotent, or detect duplicates. Ordering across
handlers is not guaranteed in general, so no handler should assume it has
seen everything else first.

## When not to use it

Events add indirection. For a step that must succeed in the same transaction,
or a call whose result is needed immediately, a direct call is clearer. Using
events for every internal method call makes the flow of a request very hard to
follow.

## Common mistakes

Publishing events before the commit announces changes that may never happen.
Treating events as remote procedure calls, and waiting for specific replies,
reintroduces tight coupling under a different name. Handlers that are not
idempotent produce duplicate emails and double charges when a message is
redelivered.

## Related

Event-driven designs are the basis of many [Microservices](./microservices.md),
and they are the tool for splitting work across [bounded contexts](./bounded-context.md).
See also [Architecture & Design](../pages/architecture.md).

## See also

- [Aggregate](aggregate.md)
- [CQRS (Command Query Responsibility Segregation)](cqrs.md)
- [Microservices](microservices.md)
- [Unit of Work](unit-of-work.md)
- [Service Layer](service-layer.md)
- [Bounded Context](bounded-context.md)
