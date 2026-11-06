---
title: API Design
tags: [api-design, architecture, design-patterns, microservices]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/gang-of-four.md, sources/fowler-ci-cd.md]
layout: default
parent: Concepts
---

# API Design

**API design** is the craft of defining the *interface* through which a
software component is *used* — the contracts, methods, and data shapes a
consumer sees. It is "the 80/20 of software design": a small surface that *all*
consumers depend on, so the *consequences* of a bad decision are *enormous and
long-lived*. In a [Microservices](./microservices.md) system, the API is *the* boundary — the
one artefact other teams code against.

## The core principle: design for the *consumer*

The central test of an API is **how easy it is to use *correctly*, and how
hard it is to use *wrong*.** The best APIs feel *inevitable* — the consumer
seldom has to look at the docs to do the common things, and the docs are mostly
there for the edge cases. Concretely:

- **Consistency** — one thing, one way. A `get()` that behaves differently
  across two resources teaches the consumer *two* rules; that is a defect.
- **Predictable error model** — a *single, documented* way to report failure
  (one error shape, one status convention), so the consumer handles errors in
  one place. "Sometimes it throws, sometimes it returns `null`, sometimes it
  returns an error object" is the classic *unpredictable* API — the worst kind.
- **Minimal surface** — expose the *least* that meets the need. Every method
  you expose is a *commitment* you must maintain in *forever* (see below).
  Prefer composable, *general* primitives over a menu of special cases.
- **Discoverable and self-describing** — names that read like the domain
  ([Ubiquitous Language](./ubiquitous-language.md)); documentation that a new consumer can rely on.

## The 80/20 and the cost of a bad decision

This is the **[Technical Debt](./technical-debt.md)** of interfaces, and it is *steeper* than
internal code debt:

- An internal function is refactored *within your team*. An API is a **public
  contract** that *other* people — sometimes *other teams and other companies* —
  build on. Changing a public API has a *real, external* cost (migration,
  versioning, coordination).
- **APIs are "forever."** Once consumed, a method rarely goes away; you add
  *versions* or *deprecate* and *maintain the old one in parallel.* This is why
  *good* API design (a stable, predictable, minimal surface) is worth so much:
  you are *buying future flexibility* with present restraint.

This is why [You Aren't Gonna Need It (YAGNI)](./yagni.md) applies *especially* hard to APIs: expose what you know
you need, keep it *simple and predictable*, and you can *extend* it compatibly
later. The [Bounded Context](./bounded-context.md) is the unit: *each context exposes one API.*

## Related Pages

- [Bounded Context](./bounded-context.md)
- [Microservices](./microservices.md)
- [Clean Code](./clean-code.md)

## Sources

- **[Design Patterns (GoF)](../sources/gang-of-four.md)**
- **[CI/CD, DORA & DevOps](../sources/fowler-ci-cd.md)**

## Maps of Content

- [Architecture & Design](../pages/architecture.md)

## See also

- [Microservices](microservices.md)
- [CQRS (Command Query Responsibility Segregation)](cqrs.md)
- [Bounded Context](bounded-context.md)
- [Design Patterns](design-patterns.md)
- [Ports and Adapters (Hexagonal Architecture)](ports-and-adapters.md)
- [Monolith](monolith.md)
- [Building Software with AI Agents](../pages/ai-agents-software-engineering.md)
