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

## Worked example

A `Batch` aggregate holds a reference, a sku, and a quantity of available stock,
along with the order lines allocated to it. Its `allocate` method refuses any
line that would exceed the available quantity, and it raises an error rather
than silently allocating too much. That rule can be enforced by the aggregate
alone, in one transaction, because everything it needs is inside it. The
aggregate is loaded, changed through its root, and saved as a whole.

## Choosing boundaries

Start with the invariant, not the data. Ask which rules must hold together
at the moment of a commit, and put the objects those rules touch inside one
aggregate. Keep the aggregate small enough to load and lock quickly. Reference
other aggregates by identity rather than by holding them, so that no single
transaction has to span the whole model.

## When not to use it

A simple entity with no invariants that span several objects does not need an
aggregate. Forcing every table into an aggregate adds structure without
protecting anything. The concept is most useful where a real business rule
has to be true at all times.

## Common mistakes

A common error is to make the aggregate the whole customer or the whole order
history, which makes every change contend for the same lock. Another is to
change several aggregates in one transaction because it is convenient, which
brings back the coupling the boundary was meant to prevent. A third is to let
code reach into an aggregate's children and change them directly, which skips
the root's rules.

## See also

- [Domain-Driven Design (DDD)](domain-driven-design.md)
- [Ubiquitous Language](ubiquitous-language.md)
- [Bounded Context](bounded-context.md)
- [Repository Pattern](repository-pattern.md)
- [Unit of Work](unit-of-work.md)
- [Domain Events](domain-events.md)
- [Service Layer](service-layer.md)
