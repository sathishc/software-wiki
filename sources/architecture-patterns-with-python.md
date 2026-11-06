---
title: "Architecture Patterns with Python — Harry Percival & Bob Gregory (2020)"
tags: [sources, architecture, domain-driven-design, testing, tdd, design-patterns]
source: "Book (O'Reilly, 2020); written from general knowledge of the book and checked against secondary summaries, 2026-11-06"
ingested: 2026-11-06
---

# Architecture Patterns with Python — Source Notes

**Book:** Architecture Patterns with Python: Enabling Test-Driven Development, Domain-Driven Design and Event-Driven Microservices (O'Reilly, 2020)
**Authors:** Harry Percival and Bob Gregory

**Provenance note:** These notes were written from general knowledge of the
book and checked against secondary summaries; the book's text was not
available for a close reading. Chapter-level claims should be verified before
being quoted externally.

---

## Thesis

The book shows how to apply [Domain-Driven Design (DDD)](../concepts/domain-driven-design.md)
and [Test-Driven Development (TDD)](../concepts/tdd.md) to a real Python
application, and argues that the two reinforce each other. The domain model is
kept free of infrastructure concerns, so it can be tested quickly and in
isolation, and the infrastructure is pushed to the edges behind interfaces.
The running example is a small order-allocation system, built up in layers.

## Patterns covered

- **Repository pattern** — an abstraction over persistent storage that makes
  the domain model look like an in-memory collection. See
  [Repository Pattern](../concepts/repository-pattern.md).
- **Service layer** — a thin layer that coordinates use cases, owns the
  transaction boundary, and keeps business logic out of the web or CLI
  adapter. See [Service Layer](../concepts/service-layer.md).
- **Unit of work** — manages a set of changes to be committed as a single
  atomic operation, and gives the service layer one place to control
  transactions. See [Unit of Work](../concepts/unit-of-work.md).
- **Aggregates and invariants** — the consistency boundary for a cluster of
  domain objects, which is the unit that changes are loaded and saved
  through. See [Aggregate](../concepts/aggregate.md).
- **Domain events** — facts recorded by the domain that other parts of the
  system can react to, used to keep aggregates decoupled and to move work
  across boundaries. See [Domain Events](../concepts/domain-events.md).
- **Ports and adapters (hexagonal architecture)** — the domain depends on
  abstract ports, and infrastructure implements them as adapters. See
  [Ports and Adapters](../concepts/ports-and-adapters.md).
- **Dependency injection** — dependencies are passed into handlers and
  services explicitly, with a bootstrap step wiring the real implementations
  at the application's edge. See [Dependency Injection](../concepts/dependency-injection.md).
- **CQRS** — separating commands that change state from queries that read it,
  so each side can be shaped for its job. See [CQRS](../concepts/cqrs.md).

## Ideas the book stresses

The layering is driven by testability. The authors favour a test pyramid
where most tests exercise the domain and service layer directly, and fewer
tests run end to end through the web and the database. This links to
[Test Pyramid](../concepts/test-pyramid.md) and [Unit Testing](../concepts/unit-testing.md).

The book also treats events as a way to split a system into services that
communicate asynchronously, which connects to [Microservices](../concepts/microservices.md)
and the [Monolith](../concepts/monolith.md) trade-off.

## Cross-references

- Author page: [Harry Percival & Bob Gregory](../people/percival-gregory.md).
- Map: [Architecture & Design](../pages/architecture.md).
- Builds on [Domain-Driven Design](./evans-ddd.md) (the source note for Evans's book).
