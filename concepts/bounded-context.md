---
title: Bounded Context
tags: [bounded-context, domain-driven-design, architecture]
created: 2026-09-25
updated: 2026-09-25
sources: [sources/evans-ddd.md]
layout: default
parent: Concepts
---

# Bounded Context

A **bounded context** is a *context* in which a domain model, and the terms of
its [Ubiquitous Language](./ubiquitous-language.md), have a **single, unambiguous meaning.** It is the
strategic unit of [Domain-Driven Design (DDD)](./domain-driven-design.md) and — this is the high-leverage
point — the **design basis for a service boundary** in [Microservices](./microservices.md).

## Why it exists

In any non-trivial domain, **the same word means different things in different
places.** `User` to billing is a *paying account*; `User` to support is a
*human with a ticket*; `Order` to the warehouse is a *fulfilment job*. A single
global model cannot honestly hold all of these — it forces you to pick one
meaning and *lie* about the others, or to build a Franken-model with
never-ending special cases.

A bounded context says: **"in *this* area, `User` means *this*. In *that* area,
`User` means *that*. Both are right."** The model is only consistent *within*
its boundary; you simply must **define the boundary and map how the contexts
talk to each other** (shared kernel, conformist, anti-corruption layer).

## From context to service

This is the bridge to deployment. A well-drawn bounded context is *almost
always* a reasonable **[Microservices](./microservices.md) boundary**, because:

- It has a **coherent, self-contained model** (deployable as a unit).
- It has a **defined vocabulary** (a clean API for other contexts).
- It changes **independently** of other contexts (an independent deploy/ownership
  unit).

The converse is the key *warning*: **a service boundary that is *not* a bounded
context is a recipe for pain.** You end up with services that *need* each
other's internals and change lockstep — the worst of both worlds. DDD gives
you a *domain-derived* reason to cut a service boundary, instead of an
*infrastructure-derived* one.

## Related Pages

- [Domain-Driven Design](./domain-driven-design.md)
- [Ubiquitous Language](./ubiquitous-language.md)
- [Microservices](./microservices.md)
- [Eric Evans](../people/eric-evans.md)

## Sources

- **[Domain-Driven Design](../sources/evans-ddd.md)**

## Maps of Content

- [Architecture & Design](../pages/architecture.md)
