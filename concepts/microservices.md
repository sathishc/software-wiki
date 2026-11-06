---
title: Microservices
tags: [microservices, architecture, monolith, deployment]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/evans-ddd.md, sources/fowler-ci-cd.md]
layout: default
parent: Concepts
---

# Microservices

**Microservices** is a software-architecture style in which a system is built
as a collection of **small, independently deployable services**, each owning a
*bounded slice* of functionality, communicating over **network APIs** (usually
HTTP/REST or messaging), and each deployable *independently* of the others. It
is most often contrasted with the **[Monolith](./monolith.md)**.

## The core properties (what makes it "micro")

A *microservice* is a microservice only if it has most of these:

- **Decomposed by business capability** — each service owns a *coherent domain
  concern* (billing, order, inventory), **not** a technical layer (there is not
  a "database service" and a "business-logic service"). The seams follow the
  [Bounded Context](./bounded-context.md) of the domain.
- **Independent deployment** — you can ship a change to one service without
  rebuilding or redeploying the others. *This* is the property that buys the
  scaling benefit.
- **Owns its own data** — each service has its own store and **no shared
  database** (a shared DB reintroduces the monolith's coupling under a new
  name).
- **Lightweight communication** — services talk over *explicit* network calls,
  so the boundaries are *real* (you feel them, and must manage them).

## The real trade-off (the honest one)

Microservices *trade* a monolith's **simplicity and speed-of-development** for
**independent scaling and independent deployment.** The cost is that you now
have a **distributed system**, which means you must *earn* back:

- **Distributed-systems pain** — network calls can fail, be slow, be
  duplicated; you must handle partial failure, timeouts, and eventual
  consistency. A monolith has in-memory calls; a microservice has *the network*.
- **Operational complexity** — N services = N things to deploy, monitor,
  secure, and version. You *need* [Continuous Integration & Continuous Delivery (CI/CD)](./ci-cd.md) and [Observability](./observability.md) at scale, or
  you are running N fragile systems instead of one.
- **Boundary quality is everything** — cut a service boundary *wrong* (not along
  a [Bounded Context](./bounded-context.md)) and you get services that change lockstep and call
  into each other's guts: the *worst* of both architectures.

**The honest rule of thumb:** *start as a [Monolith](./monolith.md) and extract a service
when you have a *reason* — an independent scaling/ownership/deployment need —
not when "microservices" is the default.* The boundary should be *domain-driven*
([DDD](domain-driven-design.md)), because a domain boundary is the only one that's *stable and meaningful*.

## Related Pages

- [Monolith](./monolith.md)
- [Bounded Context](./bounded-context.md)
- [Continuous Integration/CD](./ci-cd.md)
- [Observability](./observability.md)

## Sources

- **[Domain-Driven Design](../sources/evans-ddd.md)** (contexts as boundaries)
- **[CI/CD, DORA & DevOps](../sources/fowler-ci-cd.md)** (operating them)

## Maps of Content

- [Architecture & Design](../pages/architecture.md)
- [Delivery](../pages/delivery.md)

## See also

- [Monolith](monolith.md)
- [Bounded Context](bounded-context.md)
- [Domain Events](domain-events.md)
- [API Design](api-design.md)
- [Continuous Integration & Continuous Delivery (CI/CD)](ci-cd.md)
- [DORA Metrics](dora-metrics.md)
- [CQRS (Command Query Responsibility Segregation)](cqrs.md)
