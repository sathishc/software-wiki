---
title: Eric Evans
tags: [person, domain-driven-design, architecture, modeling]
created: 2026-09-25
updated: 2026-09-25
sources: [sources/evans-ddd.md]
layout: default
parent: People
---

# Eric Evans

Author of *Domain-Driven Design* (2003, "the blue book") — the foundational
text of the [Domain-Driven Design (DDD)](../concepts/domain-driven-design.md) movement. His work reframed software
design as a *modeling* discipline: the hardest part of a project is not the
technology, it is representing the business domain correctly.

## Core contribution

1. **The domain model as the heart of the system** — the conceptual
   representation of the business (concepts, relationships, rules) *is* the
   design.
2. **Ubiquitous Language** — a single shared vocabulary, used in code, docs,
   *and* conversation, drawn from the domain experts' words.
3. **Bounded Context** — a model only means what it means within a defined
   context; map how contexts relate and you know where the system's seams are.
   This is the strategic insight behind [Microservices](../concepts/microservices.md).

## His key insight

> "If the model is wrong, the software is wrong — no amount of clever code
> saves a wrong model."

Evans' whole book is an answer to one question: *how do you keep a complex
domain from boiling over into spaghetti?* His answer is **discipline at the
boundaries** (bounded contexts) and **clarity at the centre** (ubiquitous
language).

## Where he fits

Evans is the **architecture-strategy** anchor. His [Bounded Context](../concepts/bounded-context.md) is the
bridge from [Domain-Driven Design (DDD)](../concepts/domain-driven-design.md) to [Microservices](../concepts/microservices.md) — the most-cited
reason to draw a service boundary. He is the counterweight to purely
technical/infrastructure-driven architecture.

## Related Pages

- [Domain-Driven Design](../concepts/domain-driven-design.md)
- [Bounded Context](../concepts/bounded-context.md)
- [Ubiquitous Language](../concepts/ubiquitous-language.md)
- [Microservices](../concepts/microservices.md)
- [Martin Fowler](./martin-fowler.md)

## Sources

- **[Domain-Driven Design](../sources/evans-ddd.md)**

## Maps of Content

- [Architecture & Design](../pages/architecture.md)
