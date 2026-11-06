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

## Related

Injection is the way [Unit Testing](./unit-testing.md) gets its fakes, and the
[repository](./repository-pattern.md) and [unit of work](./unit-of-work.md) are
typically the first dependencies passed in. See [Design Patterns](./design-patterns.md)
for the wider family of decoupling patterns.
