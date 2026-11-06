---
title: Service Layer
tags: [architecture, domain-driven-design, design-patterns]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/architecture-patterns-with-python.md]
layout: default
parent: Concepts
---

# Service Layer

The **service layer** is a thin layer of application code that sits between
the outside world (a web API, a CLI, a message consumer) and the
[domain model](./aggregate.md). It defines the system's use cases, such as
"allocate an order line" or "create a batch", and coordinates the steps needed
to carry each one out. It is described in
[Percival and Gregory's](../people/percival-gregory.md) *Architecture Patterns
with Python* as the orchestration layer of a [ports-and-adapters](./ports-and-adapters.md) design.

## What it does

A service function typically loads the aggregates it needs through a
[repository](./repository-pattern.md), calls methods on them to apply the
business rules, saves the results, and commits the transaction through a
[unit of work](./unit-of-work.md). It does not contain business rules itself.
Those belong in the domain model. The service layer's job is sequencing and
boundaries.

## What it does not do

It should not know about HTTP status codes, SQL, or the shape of a web request.
Keeping those out means the same use case can be called from an API, a
command-line tool, or a test, with no changes to the domain.

## Why it helps testing

Because use cases are plain functions with explicit dependencies, the service
layer is the main target for fast tests. The
[Test Pyramid](./test-pyramid.md) relies on most behavioural tests being at
this level, with a thin layer of end-to-end tests above it.

## Worked example

An "allocate order line" use case takes a command with an order id and a
product sku. The service opens a unit of work, asks the batch repository for
the batches holding that sku, calls the domain method that picks a batch and
records the allocation, then commits. If no batch has enough stock, the domain
records an out-of-stock event and the service returns a result the web layer
can translate into a response. The service contains the sequence of steps and
the transaction boundary, and nothing about HTTP, SQL or email.

## What belongs in the service and what does not

Business rules belong on the domain objects, so that they are enforced whichever
entry point is used. The service decides what happens and in what order, which
transactions to open, and which events to publish. A service function that
contains a long chain of `if` statements describing pricing or eligibility has
absorbed domain logic, and the domain model is probably too thin.

## When not to use it

For a single-endpoint application with no domain rules, a service layer adds
ceremony without benefit. Once there are several entry points, such as a web
API, a message consumer, and a scheduled job, the layer pays for itself because
each entry point becomes a thin adapter over the same use case.

## Common mistakes

The most common error is an "anaemic" domain, where the service layer holds
all the logic and the domain objects are plain data holders. Another is a
service that calls other services in deep chains, which hides the transaction
boundary. A third is returning web-specific responses from the service, which
ties the use case to one adapter.

## Related

Service functions receive their dependencies through [dependency injection](./dependency-injection.md).
Their side effects, such as published [domain events](./domain-events.md), are
where event-driven behaviour starts. See also [Architecture & Design](../pages/architecture.md).

## See also

- [Unit of Work](unit-of-work.md)
- [Repository Pattern](repository-pattern.md)
- [Domain Events](domain-events.md)
- [CQRS (Command Query Responsibility Segregation)](cqrs.md)
- [Dependency Injection](dependency-injection.md)
- [Ports and Adapters (Hexagonal Architecture)](ports-and-adapters.md)
