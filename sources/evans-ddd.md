---
title: "Domain-Driven Design — Eric Evans (2003)"
tags: [sources, domain-driven-design, architecture, modeling]
source: https://en.wikipedia.org/wiki/Domain-driven_design
ingested: 2026-09-25
---

# Domain-Driven Design — Source Notes

**Book:** Domain-Driven Design: Tackling Complexity in the Heart of Software (2003)
**Author:** Eric Evans (the "blue book")

**Reference URLs captured:**
- https://en.wikipedia.org/wiki/Domain-driven_design
- https://martinfowler.com/bliki/UbiquitousLanguage.html
- https://martinfowler.com/bliki/BoundedContext.html

---

## The core problem

Complex domains are where software gets genuinely hard. Evans' claim: the
hardest part of a software project is the **model** — getting the
representation of the business domain right, not the surrounding plumbing.
"Get the model right" is the thesis.

## The three core building blocks

1. **Domain** — the subject matter (billing, logistics, trading) the software
   helps with. The *domain model* is a conceptual representation of business
   concepts, relationships, and rules relevant to the user goals.

2. **Ubiquitous Language** — a shared vocabulary, drawn from the domain
   experts' own words, used *consistently* in conversation, documentation,
   *and* code identifiers. If the word `Customer` means one thing to the
   accountant and another to the UI, you have a defect, not a naming
   preference. [Martin Fowler](../people/martin-fowler.md) and [Eric Evans](../people/eric-evans.md) treat this as the anchor of
   the whole approach.

3. **Bounded Context** — a model is only valid within a *bounded context*, a
   context in which the terms have a single, unambiguous meaning. The same word
   can legitimately mean different things in different contexts (a `User` in the
   billing context is not the same as a `User` in the customer-support context).
   Mapping how bounded contexts relate (shared kernel, conformist, anti-
   corruption layer) is how large systems stay coherent.

## The strategic / tactical split

- **Strategic design** — how to divide a large domain into bounded contexts and
  how the contexts relate. This is the source of [Microservices](../concepts/microservices.md) as a
  deployment topology: contexts are the *right* seams to deploy.
- **Tactical patterns** — how to model *within* a context: **Entities** (have
  identity), **Value Objects** (defined by attributes, immutable), **Aggregates**
  (a cluster treated as a unit of consistency with a single root), Repositories,
  Factories, Domain Services, Domain Events.

## Why it matters

DDD reframes architecture from "how do the technical boxes fit together" to
"how does the *business* fit together." It is the bridge between
[Domain-Driven Design (DDD)](../concepts/domain-driven-design.md)-driven boundaries and deployment: a well-drawn bounded
context is almost always a reasonable service boundary, and a bad one is not.

---
