---
title: Dependency Injection
tags: [design-patterns, architecture, testing, tdd, solid]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/architecture-patterns-with-python.md]
layout: default
parent: Concepts
---

# Dependency Injection

**Dependency injection** means that a component receives the things it depends
on from outside, rather than creating them or reaching for globals itself. It
is the mechanism that makes the [ports-and-adapters](./ports-and-adapters.md)
structure work. In [Percival and Gregory's](../people/percival-gregory.md)
book, handlers and services declare their dependencies explicitly, and a
bootstrap step at the edge of the application decides which real adapters to pass in.

## The bootstrap

The book uses a small bootstrap function as the single place where the
application is assembled. It creates the real database session, repositories,
and message publisher, then injects them into the [service layer](./service-layer.md).
Tests run the same services with fake adapters injected instead. Nothing inside
the core needs to know which one it has.

## Why it helps

Injection removes hidden coupling. A function that takes a repository as an
argument is easy to test with a fake; one that constructs its own database
connection is not. This connects to the dependency-inversion principle of
[SOLID](./solid.md), where high-level policy depends on abstractions rather
than concrete details.

## Trade-offs

Explicit injection can add boilerplate, and a large container framework can hide
what is actually wired together. Keep the wiring visible and in one place, and
avoid injecting things that never need to vary.

## Worked example

A `create_order` function accepts its repository and its notifier as arguments.
In production, a bootstrap function constructs the SQL repository and the email
notifier and passes them in. In a test, the same function receives an in-memory
repository and a fake notifier, and the test calls it directly. The function
itself never decides which implementation it uses, so the test exercises the
same logic as production with only the outside world replaced.

## Where the wiring lives

Keep the construction of real objects in one place at the edge of the
application, typically a bootstrap or composition root. Everything else asks
for what it needs through its parameters. When the wiring is scattered, it is
hard to tell what the application actually uses, and tests have to patch
global state to swap implementations.

## When not to use it

Injecting something that will never vary, such as a pure function or a
constant, adds parameters without benefit. Very small scripts may not justify
a bootstrap step at all. A large container framework can also be overkill, and
it can hide the dependency graph behind annotations that are hard to read.

## Common mistakes

Reaching for a global singleton inside a function defeats the purpose and
makes tests order-dependent. A service locator, where code asks a registry for
its dependencies at runtime, looks like injection but hides the dependencies
from the function signature. Passing the entire application container into
every function is the same problem in a different shape.

## Related

Injection is the way [Unit Testing](./unit-testing.md) gets its fakes, and the
[repository](./repository-pattern.md) and [unit of work](./unit-of-work.md) are
typically the first dependencies passed in. See [Design Patterns](./design-patterns.md)
for the wider family of decoupling patterns.

## See also

- [Ports and Adapters (Hexagonal Architecture)](ports-and-adapters.md)
- [Service Layer](service-layer.md)
- [Unit Testing](unit-testing.md)
- [Repository Pattern](repository-pattern.md)
- [SOLID](solid.md)
- [Design Patterns](design-patterns.md)
