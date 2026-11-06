---
title: Ports and Adapters (Hexagonal Architecture)
tags: [architecture, design-patterns, testing, tdd]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/architecture-patterns-with-python.md]
layout: default
parent: Concepts
---

# Ports and Adapters (Hexagonal Architecture)

**Ports and adapters**, also called **hexagonal architecture** (Alistair Cockburn,
2005), places the application's core at the centre and makes every dependency on
the outside world go through an explicit boundary. A **port** is an interface
the core defines for something it needs or offers. An **adapter** is the
concrete code that implements a port against a real technology, such as a
database, a message queue, or an HTTP client. In
[Percival and Gregory's](../people/percival-gregory.md) book this is the
structure the whole application is built around.

## The shape

The domain and the [service layer](./service-layer.md) sit inside the boundary
and depend on nothing outside it. A [repository](./repository-pattern.md) is a
port for storage, and an email sender or message publisher is a port for
outbound communication. On the outside, a web API or CLI drives the core
through its own adapter, and a database adapter implements the storage port.
The arrows point inwards, so the core never imports infrastructure.

## Why it matters for testing

Because the core depends only on ports, a test can plug in an in-memory fake
adapter and exercise the whole use case without any infrastructure. This is the
practical reason the book pairs the pattern with [Test-Driven Development](../concepts/tdd.md)
and why most of its tests run fast. See the [Test Pyramid](./test-pyramid.md).

## Trade-offs

The pattern adds interfaces and indirection that are not worth it for a small
script. Its benefit grows with the number of external systems and the amount
of domain logic. The risk is a port that mirrors a particular technology rather
than the domain's needs, which leaks the technology back into the core.

## Worked example

An order service needs to send a confirmation. The core defines a port, a
`Notifier` interface with a single `send` operation taking a recipient and a
message. The production adapter wraps an email provider's client, and a
different adapter could use SMS. In tests, a fake adapter records what it was
asked to send, and the test checks the record. The core's code never imports
the email library, so changing providers touches one adapter and no domain
code.

## Designing ports

Define a port in terms of what the core needs, not in terms of a vendor's
API. A port called `PaymentGateway` with `charge(amount, customer)` is better
than one that mirrors a particular provider's endpoints and fields, because
the vendor's shape then leaks into the domain. Keep ports small and focused.
A port with forty methods is usually two or three ports that have been merged.

## When not to use it

For a script that talks to one database and has no domain rules, the pattern
is more structure than the problem needs. Its value grows with the number of
external systems and the amount of domain logic that must stay independent of
them.

## Common mistakes

A port that is a thin wrapper around a vendor SDK offers no protection, since
every caller still needs to know the vendor's semantics. Passing ORM objects or
HTTP request objects through a port leaks infrastructure back into the core.
Mocking every collaborator in a test, rather than using a simple fake, hides
the real behaviour the port is supposed to isolate.

## Related

Ports are wired together by [dependency injection](./dependency-injection.md).
See also [Architecture & Design](../pages/architecture.md) and [Monolith](./monolith.md),
which the pattern lets you keep well-structured as a single deployable.

## See also

- [Dependency Injection](dependency-injection.md)
- [Repository Pattern](repository-pattern.md)
- [Service Layer](service-layer.md)
- [Unit Testing](unit-testing.md)
- [Test-Driven Development (TDD)](tdd.md)
- [Domain-Driven Design (DDD)](domain-driven-design.md)
