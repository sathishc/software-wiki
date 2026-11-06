---
title: Harry Percival & Bob Gregory
tags: [person, architecture, domain-driven-design, tdd, testing]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/architecture-patterns-with-python.md]
layout: default
parent: People
---

# Harry Percival & Bob Gregory

Harry Percival and Bob Gregory are the authors of *Architecture Patterns with
Python* (O'Reilly, 2020). Percival also wrote *Test-Driven Development with
Python*, which the new book builds on. Their work takes the ideas of
[Eric Evans](./eric-evans.md) and [Kent Beck](./kent-beck.md) and applies them
to a concrete Python codebase, which makes it one of the more practical
treatments of DDD in a dynamic language.

## Core contribution

Their main claim is that [Domain-Driven Design](../concepts/domain-driven-design.md)
and [Test-Driven Development](../concepts/tdd.md) work best together. The domain
model is kept free of infrastructure so that it can be tested quickly, and the
infrastructure is pushed to the edges. They show this step by step, building up
a small system and introducing each pattern only when the code needs it.

## Key patterns in the book

Their structure gives the wiki several of its architecture concepts: the
[repository](../concepts/repository-pattern.md), the [service layer](../concepts/service-layer.md),
the [unit of work](../concepts/unit-of-work.md), [aggregates](../concepts/aggregate.md),
[domain events](../concepts/domain-events.md), and [ports and adapters](../concepts/ports-and-adapters.md).
Their use of [dependency injection](../concepts/dependency-injection.md) at the
application's edge is a practical form of [SOLID](../concepts/solid.md)'s dependency inversion.

## Where they sit in the wiki

Their book connects the testing material in [Testing & Quality](../pages/testing.md)
with the design material in [Architecture & Design](../pages/architecture.md).
It sits downstream of [Eric Evans](./eric-evans.md)'s model-driven design, and
it provides concrete code for the [bounded context](../concepts/bounded-context.md)
and [microservices](../concepts/microservices.md) ideas.
