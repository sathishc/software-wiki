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

## Worked example

A transfer between two accounts loads both accounts through the unit of work,
changes their balances, and calls commit. Inside the unit of work, both changes
are written together. If the second account is missing, the code raises an
exception before commit, and the unit of work rolls back, so the first account
is not debited either. Without the unit of work, each repository call could
commit independently, and a crash between them would leave money missing.

## How the pieces cooperate

The unit of work exposes the repositories it manages, so a use case obtains its
repositories through it rather than constructing them. The collection of
aggregates it loaded can also collect domain events, which it publishes only
after a successful commit. That ordering matters: events announce changes that
actually happened, not changes that were rolled back.

## When not to use it

If each use case changes exactly one aggregate in one write, the underlying
ORM session or database transaction may already provide the boundary. Adding a
unit of work on top then duplicates what is already there. Check what the
framework provides before building one.

## Common mistakes

Opening a new unit of work for every repository call defeats its purpose.
Committing inside the domain model moves the transaction boundary out of the
service layer, where it is hard to see. A third mistake is to ignore failure
paths, so that rollback is never exercised and nobody knows whether it works.
