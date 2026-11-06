---
title: Architecture & Design
tags: [moc, architecture, microservices]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/evans-ddd.md, sources/gang-of-four.md, sources/fowler-refactoring.md]
layout: default
parent: Pages
---

# Architecture & Design

> A curated map of *how a *system* is *structured* — from *single classes* to
> *bounded contexts* to *deployed services.* This is the *system-scale* version
> of the same *economics* that drive [Code Quality](./code-quality.md): **make it *easy to
> change*, because *change is the only constant*.**

## The one-line idea

**Architecture is the set of *decisions* that are *expensive to change later*.**
Everything else is *implementation*. A *good* architecture is one where the
*expensive* decisions are *right* and the *cheap* ones are *free to evolve* —
which means the *boundaries* (module, context, service) are drawn *along the
lines where the *domain* actually *changes independently.*

## How the pieces fit

```
   ┌──────────────────────────────────────────────────────────────────┐
   │                 Domain-Driven Design  (the *lens*)               │
   │   model the *business*; name things the *domain* names them       │
   └──────────────┬───────────────────────────────┬───────────────────┘
                  │  ubiquitous language          │  bounded contexts
                  ▼                               ▼
   ┌──────────────────────────────┐   ┌───────────────────────────────┐
   │   Ubiquitous Language        │   │   Bounded Context             │
   │   (one shared vocabulary,    │   │   (a model that only means     │
   │    code = the domain's words)│   │    what it means *here*)       │
   └──────────────────────────────┘   └───────────────┬───────────────┘
                                                      │  contexts are the *right*
                                                      │  seams to *deploy*
                                                      ▼
   ┌──────────────────────────────────────────────────────────────────┐
   │                     Module / Service Boundaries                  │
   │   a *monolith* (one deploy, structured)  or  *microservices*     │
   │   (many deploys)  — *structure* and *deployment* are *separate*  │
   └──────────────────────────────┬───────────────────────────────────┘
                                  │  the *contract* between units is
                                  ▼
   ┌──────────────────────────────────────────────────────────────────┐
   │                       API Design  (the *interface*)              │
   │   minimal · predictable · *designed for the *consumer*           │
   └──────────────────────────────────────────────────────────────────┘
```

And, *orthogonal* to all of the above, the *tactics* that *shape* the code
*inside* those boundaries: **[Design Patterns](../concepts/design-patterns.md)** (the *named* decoupling
moves) and **[SOLID](../concepts/solid.md)** (the *single-responsibility* family of them).

## The synthesis (where these fit together)

- **[Domain-Driven Design (DDD)](../concepts/domain-driven-design.md)** is the *lens* — *start from the *business,*
  not the *technology.* It is the *most radical* claim in this map: *the
  *model* is the *heart* of the *system.*
- **[Ubiquitous Language](../concepts/ubiquitous-language.md)** is DDD's *most-repeated* idea — *one shared
  vocabulary, in code, docs, *and* *conversation.* It is [Clean Code](../concepts/clean-code.md)'s
  *naming* rule, *elevated* to a *team* discipline.
- **[Bounded Context](../concepts/bounded-context.md)** is the *strategic* heart — *the *model* is only
  *valid* *within* a *boundary*; *map* the *contexts* and you *know* the
  *seams.* **This is the *design basis* for a *service boundary.***
- **[Monolith](../concepts/monolith.md) vs [Microservices](../concepts/microservices.md)** is the *deployment* decision — and
  the *crucial* *insight* is that **structure** and **deployment** are *two
  *independent* *axes.* A *structured monolith* is *good*; a *big ball of
  mud* (structured *or not*) is *the real problem.*
- **[API Design](../concepts/api-design.md)** is the *contract* — the *80/20* of *design:* a *small*
  surface that *all* *consumers* depend on, *forever.* *Good* API design is
  *buying* *future flexibility* with *present restraint.*
- **[Design Patterns](../concepts/design-patterns.md) + [SOLID](../concepts/solid.md)** are the *tactics* — the *named* and
  *principle-based* *decoupling* moves that *shape* the code *inside* the
  boundaries above.
- **[Ports and Adapters](../concepts/ports-and-adapters.md)** and the **[Repository Pattern](../concepts/repository-pattern.md)** put the
  *domain* at the centre, with *infrastructure* at the edges. The
  **[Service Layer](../concepts/service-layer.md)** and **[Unit of Work](../concepts/unit-of-work.md)** coordinate
  each use case and its transaction, and **[Dependency Injection](../concepts/dependency-injection.md)** wires the
  real pieces in at the edge, so the core can be tested without them.
- **[Aggregate](../concepts/aggregate.md)** and **[Domain Events](../concepts/domain-events.md)** draw the *consistency*
  boundary inside the model and carry changes across it, and **[CQRS](../concepts/cqrs.md)** splits the write side
  from the read side when their shapes diverge. These are the patterns from
  [Percival and Gregory](../people/percival-gregory.md)'s *Architecture Patterns with Python*.

The **unifying thread** is *boundaries, and the *reason* for them*: **a
boundary is *earned* when what's on the *two sides* *changes *independently.***
*DDD* tells you *where* the *independence* *lives* (the *domain*); *bounded
context* *marks* it; *monolith/microservices* *deploys* it; *API* *contracts*
it; *patterns* and *SOLID* *decouple* it *inside.*

## The key people

- **[Eric Evans](../people/eric-evans.md)** — DDD, [Ubiquitous Language](../concepts/ubiquitous-language.md), [Bounded Context](../concepts/bounded-context.md);
  the *model-first* anchor.
- **[Martin Fowler](../people/martin-fowler.md)** — the *bliki* essays that made DDD *practical* and
  *named* its *key ideas* in *plain* English.

## Recommended reading order

1. **[Architecture & Design](./architecture.md)** (you are here — the map).
2. **[Domain-Driven Design (DDD)](../concepts/domain-driven-design.md)** — the *lens* (and *when* it's *worth* it).
3. **[Bounded Context](../concepts/bounded-context.md)** — the *strategic* heart (and the *bridge* to
   *services).
4. **[Monolith](../concepts/monolith.md)** / **[Microservices](../concepts/microservices.md)** — the *deployment* decision
   (and *why* *most* systems should *start* *monolithic*).
5. **[API Design](../concepts/api-design.md)** — the *contract* (and the *forever* *cost* of a bad one).

## Related Maps of Content

- [Code Quality](./code-quality.md) — the *same* *economics* at the *class*
  scale.
- [Testing & Quality](./testing.md) — the *net* that *protects* the
  boundaries.
- [Delivery](./delivery.md) — how you *ship* and *observe* the boundaries.

## See also

- [Building Software with AI Agents](./ai-agents-software-engineering.md) — how agent-built code is tested, reviewed and delivered.
