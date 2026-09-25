---
title: Monolith
tags: [monolith, architecture, microservices, deployment]
created: 2026-09-25
updated: 2026-09-25
sources: [sources/evans-ddd.md]
layout: default
parent: Concepts
---

# Monolith

A **monolith** (in software architecture) is a system built and deployed as a
**single, unified unit of code** — one deployable artefact, often one
codebase, one (or a few) databases, in-process calls between its modules. It is
the *default* and the *starting point* for most systems, and the baseline that
**[Microservices](./microservices.md)** are usually a *departure* from.

## Why "monolith" is not an insult (it often gets written that way)

A *well-structured* monolith — **"modular monolith"** — is a perfectly good,
often *the right* architecture: one deployable, but with **clear internal
module boundaries** (so the modules can be *extracted into services later, if
and when needed*). The anti-pattern is not "it's a monolith"; the anti-pattern
is a **"big ball of mud"** — a monolith with *no* internal structure, where
every module knows every other and every change ripples everywhere.

That distinction is the whole point of the [Monolith](./monolith.md) vs [Microservices](./microservices.md)
debate: **structure (clear boundaries) and deployment (one unit vs many) are
two *independent* axes.** You can have:

- A **structured monolith** (good boundaries, one deploy) — *simple, fast to
  develop, easy to reason about*, and *can be decomposed later*.
- A **big ball of mud monolith** (no boundaries) — the real problem.
- A **set of well-bounded microservices** (good boundaries, many deploys) —
  independent scale/deploy, at the cost of distributed-systems complexity.
- A **set of poorly-bounded microservices** (no boundaries, many deploys) —
  *the worst of both*: a big ball of mud *distributed over the network*, with
  all the distributed pain and none of the independence benefit.

## When a monolith wins

A monolith is the *right* choice when: the team is small, the domain is not
yet complex enough to need independent scaling, and the *cost* of distributed
systems (network failures, eventual consistency, N things to operate) exceeds
the *benefit* of independent deployment. **Most systems should *start* here**
and only *extract* a service when a *specific* scaling or ownership need
appears — with the extraction guided by the [Bounded Context](./bounded-context.md) so the new
boundary is *meaningful*.

## Related Pages

- [Microservices](./microservices.md)
- [Bounded Context](./bounded-context.md)
- [Domain-Driven Design](./domain-driven-design.md)

## Sources

- **[Domain-Driven Design](../sources/evans-ddd.md)**

## Maps of Content

- [Architecture & Design](../pages/architecture.md)
