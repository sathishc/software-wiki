---
title: Domain-Driven Design (DDD)
tags: [domain-driven-design, architecture, modeling]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/evans-ddd.md]
layout: default
parent: Concepts
---

# Domain-Driven Design (DDD)

**Domain-Driven Design** is an approach to software design that starts from the
*business domain* — the real-world problem the software solves — and works
*inward*, making the **model** (the representation of that domain in code) the
**centre of the system.** Coined by **Eric Evans** [Eric Evans](../people/eric-evans.md) in his 2003
"blue book," DDD is a direct answer to the observation that in complex
systems, *the hard part is not the technology, it is the model.*

## The three pillars

1. **The domain model is the heart.** The conceptual representation of the
   business — its concepts, relationships, and rules — *is* the design. Get it
   right and the rest follows; get it wrong and no amount of clever plumbing
   saves you.

2. **Ubiquitous Language** [Ubiquitous Language](./ubiquitous-language.md) — one shared vocabulary,
   drawn from the domain experts' own words, used *consistently* in
   conversation, documentation, *and* code identifiers. This is DDD's most
   radical claim: a naming disagreement between the team and the code is a
   *defect*, not a style choice.

3. **Bounded Context** [Bounded Context](./bounded-context.md) — a model is only meaningful within
   a defined boundary. The same word can legitimately mean different things in
   different contexts; *map the contexts and their relationships* and you know
   where the system's seams are.

## Strategic vs tactical

- **Strategic DDD** — how to *partition* a large domain into bounded contexts
  and how those contexts relate (shared kernel, conformist, anti-corruption
  layer). This is the *big* part: it is where DDD earns its keep at scale and
  is the *design basis* for [Microservices](./microservices.md) boundaries.
- **Tactical DDD** — how to model *within* a context: **Entities** (have
  identity), **Value Objects** (immutable, defined by attributes), **Aggregates**
  (a unit of consistency with a single root), plus Repositories, Factories,
  Domain Services, and [Domain Events](domain-events.md).

## When DDD is worth it

DDD is *deliberately* heavyweight — it demands close collaboration with domain
experts and disciplined modelling. It is **worth it when the domain is the hard
part**: complex business rules, many interacting concepts, a domain that
*changes* and that you must keep modelling accurately (trading, logistics,
healthcare, finance). For a CRUD app with a flat domain, DDD is overkill — the
simple [Keep It Simple (KISS)](./kiss.md)/[You Aren't Gonna Need It (YAGNI)](./yagni.md) route wins. See [Architecture & Design](../pages/architecture.md) for the boundary-
drawing it enables.

## Related Pages

- [Bounded Context](./bounded-context.md)
- [Ubiquitous Language](./ubiquitous-language.md)
- [Microservices](./microservices.md)
- [Eric Evans](../people/eric-evans.md)

## Sources

- **[Domain-Driven Design](../sources/evans-ddd.md)**

## Maps of Content

- [Architecture & Design](../pages/architecture.md)

## See also

- [Bounded Context](bounded-context.md)
- [Ubiquitous Language](ubiquitous-language.md)
- [Aggregate](aggregate.md)
- [Repository Pattern](repository-pattern.md)
- [Service Layer](service-layer.md)
- [Microservices](microservices.md)
