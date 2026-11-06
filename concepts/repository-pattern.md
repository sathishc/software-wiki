---
title: Repository Pattern
tags: [architecture, domain-driven-design, design-patterns, testing]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/architecture-patterns-with-python.md]
layout: default
parent: Concepts
---

# Repository Pattern

A **repository** is an abstraction over persistent storage that presents
domain objects as if they lived in an in-memory collection. Code asks the
repository to `add` an object or `get` one by identity, and does not write SQL
or touch the database driver directly. The pattern comes from
[Domain-Driven Design](./domain-driven-design.md) and is central to
[Percival and Gregory's](../people/percival-gregory.md) book.

## Why it matters

Keeping persistence behind an interface does two things. It keeps the
[domain model](./aggregate.md) free of infrastructure, so the model can
evolve without changing the database. It also allows an in-memory fake to
stand in during tests, so the bulk of the test suite runs in milliseconds and
does not need a database running.

## Shape

A repository exposes a small set of operations, typically `add`, `get`, and
sometimes a query by a business key. Its concrete implementation lives in the
infrastructure layer, for example one backed by an ORM. The domain and the
[service layer](./service-layer.md) depend only on the abstract interface.

## Trade-offs

A repository adds a layer, and it can hide performance characteristics such
as N+1 queries if it is not designed with them in mind. It is also tempting to
turn it into a generic CRUD wrapper, which loses the business meaning. A
repository should expose operations in the language of the domain, in line
with [Ubiquitous Language](./ubiquitous-language.md).

## Worked example

A use case needs a batch of stock, identified by a reference. The service asks
the repository for it with `get(reference)` and receives a domain object, not a
database row. Tests use an in-memory repository that stores objects in a
dictionary and implements the same two methods. The test checks the domain
behaviour, and the production run uses the SQL-backed repository, which maps
rows to domain objects behind the same interface. The use case cannot tell
which one it has, and does not need to.

## Design rules

Name methods in the domain's language: `get`, `add`, or a business key lookup,
not `save_any` or `select_where`. Expose one repository per aggregate root,
not one per database table, because the aggregate is the unit that must be
loaded consistently. Return domain objects, never ORM query objects, so the
rest of the code does not depend on the storage technology.

## When not to use it

For a small application that does simple create, read, update and delete with
no business rules, a repository adds a layer that does little. An ORM used
directly, with the model class doubling as the domain object, is often
adequate. The repository earns its place when the domain is rich enough that
keeping it free of storage concerns pays off.

## Common mistakes

A repository that exposes a generic query builder recreates the database
inside the domain, and tests then become slow and fragile. A repository that
leaks lazy loading makes performance problems appear far from their cause. A
repository per table, rather than per aggregate, tempts code to load and change
parts of an aggregate separately, which breaks its invariants.

## Related

The repository is one of the [ports](./ports-and-adapters.md) of the
architecture, and the [Unit of Work](./unit-of-work.md) usually manages the
transaction that the repository's changes belong to. See also
[Architecture & Design](../pages/architecture.md).
