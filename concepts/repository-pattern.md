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

## Related

The repository is one of the [ports](./ports-and-adapters.md) of the
architecture, and the [Unit of Work](./unit-of-work.md) usually manages the
transaction that the repository's changes belong to. See also
[Architecture & Design](../pages/architecture.md).
