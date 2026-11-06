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

## Related

Service functions receive their dependencies through [dependency injection](./dependency-injection.md).
Their side effects, such as published [domain events](./domain-events.md), are
where event-driven behaviour starts. See also [Architecture & Design](../pages/architecture.md).
