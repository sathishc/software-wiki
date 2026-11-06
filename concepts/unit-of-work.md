---
title: Unit of Work
tags: [architecture, domain-driven-design, design-patterns]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/architecture-patterns-with-python.md]
layout: default
parent: Concepts
---

# Unit of Work

A **unit of work** groups a set of changes into one atomic operation. It keeps
track of the objects loaded during a business transaction, and it commits them
all together or rolls them all back. In [Percival and Gregory's](../people/percival-gregory.md)
book, the unit of work is the piece that gives the [service layer](./service-layer.md)
control over the transaction boundary.

## Shape

A typical unit of work is a context manager. It provides access to the
[repositories](./repository-pattern.md) it manages, and it exposes `commit` and
`rollback`. A service function opens the unit of work, does its work through
the repositories, and then calls `commit`. If an exception is raised, the
unit of work rolls back, so no partial changes are persisted.

## Why it matters

Without a unit of work, each repository call might commit on its own, and a
use case that touches two aggregates could leave the system half-updated. The
unit of work makes the atomic boundary explicit and keeps it out of the domain
model.

## Relation to domain events

The unit of work is also a natural point to collect the [domain events](./domain-events.md)
raised by the aggregates it loaded, and to publish them after a successful
commit. This is one common way to avoid announcing changes that were never
saved.

## Trade-offs

A unit of work adds an abstraction that is easy to over-engineer. In some
stacks an ORM session already plays this role, and the book's approach is to
wrap it rather than replace it. The aim is an explicit boundary, not another
layer for its own sake. See [Aggregate](./aggregate.md) for how the consistency
boundary is drawn inside it.
