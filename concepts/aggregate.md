---
title: Aggregate
tags: [domain-driven-design, architecture, modeling, bounded-context]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/architecture-patterns-with-python.md, sources/evans-ddd.md]
layout: default
parent: Concepts
---

# Aggregate

An **aggregate** is a cluster of domain objects treated as a single unit for
the purpose of changes. It has one **root entity** through which all access
goes, and it guarantees its own [invariants](#invariants) (business rules that
must always hold) when a change is committed. The concept comes from
[Domain-Driven Design](./domain-driven-design.md), and
[Percival and Gregory](../people/percival-gregory.md) use it as the unit that
the [repository](./repository-pattern.md) loads and saves.

## Invariants

The aggregate is the consistency boundary. Rules that must hold together, such
as "an order cannot allocate more stock than is available in a batch", are
enforced inside one aggregate in a single transaction. Rules that span
aggregates cannot be enforced atomically, and they are handled by eventual
consistency, usually through [domain events](./domain-events.md).

## Rules of thumb

Keep aggregates small. A large aggregate loads and locks more than it needs
to, and it creates contention. Reference other aggregates by identity rather
than by holding the object. Change one aggregate per transaction where
possible.

## Relation to the rest of the architecture

Aggregates are the objects the [service layer](./service-layer.md) coordinates
and the [unit of work](./unit-of-work.md) tracks. Their boundaries should line
up with the boundaries of the [bounded context](./bounded-context.md) that
owns them, and they should use the terms of the
[ubiquitous language](./ubiquitous-language.md).

See also [Architecture & Design](../pages/architecture.md).
