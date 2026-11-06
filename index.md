---
layout: home
title: Home
nav_order: 0
---

# software-wiki

A LLM-maintained [Karpathy LLM-wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
for **Software Engineering** — code quality, architecture, testing, and
delivery. Sibling of [`sat-wiki`](../sat-wiki/README.md). Compiled from
canonical sources; every page cross-references its neighbours, so knowledge
compounds on each ingest.

## Pages (Maps of Content)

Navigational synthesis pages — each one a curated map of a domain, not a
reference page.

- [Code Quality](pages/code-quality.md) — How code stays readable and changeable: KISS/YAGNI restraint, SOLID structure, clean code, refactoring, technical debt. Tags: `moc`, `code-quality`, `craftsmanship`
- [Testing & Quality](pages/testing.md) — The safety net that makes everything else possible: unit tests, TDD, the test pyramid, run automatically by CI. Tags: `moc`, `testing`, `tdd`, `quality`
- [Architecture & Design](pages/architecture.md) — How a system is structured: DDD's lens, bounded contexts, monolith vs microservices, API design, patterns. Tags: `moc`, `architecture`
- [Delivery](pages/delivery.md) — How software ships and tells you what's happening: CI/CD, DORA metrics, observability, code review. Tags: `moc`, `delivery`
- [Lean Product Development](pages/lean-product-development.md) — Manage the flow of value, not busyness: cost of delay, queues and utilisation, WIP limits, batch size. Includes an analysis of the wiki's coverage and gaps. Tags: `moc`, `lean`, `flow`, `economics`

---

## People

- [Eric Evans](people/eric-evans.md) — Author of Domain-Driven Design (2003, "the blue book") — the foundational text of the [Domain-Driven Design (DDD)](concepts/domain-driven-design.md) movement. His…
- [Kent Beck](people/kent-beck.md) — Author of Extreme Programming Explained (1999) and a principal originator of Agile software. With Martin Fowler he authored Refactoring; with Ward Cunningham he…
- [Martin Fowler](people/martin-fowler.md) — Author of Refactoring (2001/2018), Patterns of Enterprise Application Architecture (2002), and the ubiquitous martinfowler.com — the single most cited practical…
- [Michael Feathers](people/michael-feathers.md) — Author of Working Effectively with Legacy Code (2004) — the canonical book on the unglamorous, universally felt problem of code you cannot change safely. His work…
- [Donald G. Reinertsen](people/donald-reinertsen.md) — Author of *The Principles of Product Development Flow* (2009) and the economic case for flow in product development: cost of delay, queues, WIP limits, and small batches. Tags: `person`, `lean`, `flow`, `economics`
- [Harry Percival & Bob Gregory](people/percival-gregory.md) — Authors of *Architecture Patterns with Python* (2020): applying DDD and TDD in Python, with the repository, service layer, unit of work, and ports-and-adapters patterns. Tags: `person`, `architecture`, `domain-driven-design`, `testing`
- [Robert-Martin](people/robert-martin.md) — Robert C. Martin ("Uncle Bob") is the voice behind the SOLID principles, the [Clean Code](concepts/clean-code.md) movement, and a large part of the modern…

## Concepts

### Code Quality

- [Clean Code](concepts/clean-code.md) — Clean Code is the name Robert C. Martin [Robert-Martin](people/robert-martin.md) gave to readable, well-structured, honest-about-intent code — and to the handbook…
- [Code Smells](concepts/code-smells.md) — A code smell is a heuristic signal in code that something may be wrong — a fast, pattern-based indicator that a deeper problem is likely nearby. The name comes from…
- [Don't Repeat Yourself (DRY)](concepts/dry.md) — DRY is a software-design principle: every piece of knowledge in a system should have a single, unambiguous, authoritative representation within that system. It is…
- [Keep It Simple (KISS)](concepts/kiss.md) — KISS — "Keep It Simple, Stupid" — is the principle that a simpler design is almost always preferable to a complex one, where they achieve the same result. It is a…
- [Refactoring](concepts/refactoring.md) — Refactoring is a controlled change to existing code that alters its internal structure while preserving its observable behaviour. Both halves are essential: it…
- [SOLID](concepts/solid.md) — SOLID is a mnemonic for five single-letter design principles, coined by Robert C. Martin [Robert-Martin](people/robert-martin.md) to codify what "well-structured…
- [Technical Debt](concepts/technical-debt.md) — Technical debt is a metaphor (coined by Ward Cunningham, ~1992) for the long-term cost of choosing a faster, easier, or less correct way of doing something now in…
- [You Aren't Gonna Need It (YAGNI)](concepts/yagni.md) — YAGNI — a mantra from [Kent Beck](people/kent-beck.md)'s [Test-Driven Development (TDD)](concepts/tdd.md)/XP world — says: don't add functionality until it is actually…

### Testing

- [Test-Driven Development (TDD)](concepts/tdd.md) — TDD is the discipline of writing a failing test before you write the code that satisfies it — then writing the simplest code that passes, then cleaning up.…
- [Test Pyramid](concepts/test-pyramid.md) — The test pyramid (attributed to Ham Vervloet; popularised as the "test pyramid" by Robert C. "Uncle Bob" Martin, 2011) is a proportional model of a test suite. The…
- [Unit Testing](concepts/unit-testing.md) — Unit testing is the practice of testing the smallest testable piece of software — a single function, method, or class — in isolation, with its dependencies stubbed…
- [Extreme Programming](concepts/xp.md) — Extreme Programming (XP) — named by [Kent Beck](people/kent-beck.md) and the initial community (Beck, Ward Cunningham, Ron Jeffries, Chuck Cohn, Martin Fowler, Ken…

### Architecture & Design

- [Aggregate](concepts/aggregate.md) — A cluster of domain objects with one root and its own invariants; the unit that is loaded and saved in one transaction. Tags: `domain-driven-design`, `architecture`, `modeling`
- [API Design](concepts/api-design.md) — API design is the craft of defining the interface through which a software component is used — the contracts, methods, and data shapes a consumer sees. It is "the…
- [Bounded Context](concepts/bounded-context.md) — A bounded context is a context in which a domain model, and the terms of its [Ubiquitous Language](concepts/ubiquitous-language.md), have a single, unambiguous meaning. It is…
- [CQRS](concepts/cqrs.md) — Separating commands that change state from queries that read it, so each side can use its own model. Tags: `architecture`, `microservices`, `api-design`
- [Dependency Injection](concepts/dependency-injection.md) — Passing dependencies in from outside, wired at the application's edge, so the core is testable with fakes. Tags: `design-patterns`, `architecture`, `testing`
- [Design Patterns](concepts/design-patterns.md) — A design pattern is a named, reusable template for solving a recurring design problem — not a ready-made class to paste, but a description of a problem, the…
- [Domain Events](concepts/domain-events.md) — Past-tense records of domain facts that other parts of the system react to, decoupling aggregates and enabling eventual consistency. Tags: `architecture`, `domain-driven-design`, `microservices`
- [Domain-Driven Design (DDD)](concepts/domain-driven-design.md) — Domain-Driven Design is an approach to software design that starts from the business domain — the real-world problem the software solves — and works inward, making…
- [Functional Programming](concepts/functional-programming.md) — Functional programming (FP) is a style built on two core moves:.
- [Microservices](concepts/microservices.md) — Microservices is a software-architecture style in which a system is built as a collection of small, independently deployable services, each owning a bounded slice…
- [Monolith](concepts/monolith.md) — A monolith (in software architecture) is a system built and deployed as a single, unified unit of code — one deployable artefact, often one codebase, one (or a few)…
- [Ports and Adapters](concepts/ports-and-adapters.md) — Hexagonal architecture: the core depends on abstract ports, and infrastructure implements them as adapters. Tags: `architecture`, `design-patterns`, `testing`
- [Repository Pattern](concepts/repository-pattern.md) — An abstraction over storage that presents domain objects as an in-memory collection, so the model stays free of infrastructure. Tags: `architecture`, `domain-driven-design`, `design-patterns`
- [Service Layer](concepts/service-layer.md) — A thin layer of use-case coordination between adapters and the domain; owns the transaction boundary but holds no business rules. Tags: `architecture`, `domain-driven-design`
- [Ubiquitous Language](concepts/ubiquitous-language.md) — The ubiquitous language is a single, shared vocabulary — drawn from the domain experts' own words — used consistently in conversation, documentation, and code…
- [Unit of Work](concepts/unit-of-work.md) — Groups changes into one atomic commit or rollback, giving the service layer control of the transaction. Tags: `architecture`, `domain-driven-design`, `design-patterns`

### Delivery & Culture

- [Continuous Integration & Continuous Delivery (CI/CD)](concepts/ci-cd.md) — CI/CD is the delivery practice of merging small changes frequently and automating the work that turns a change into production — the build, test, package, and…
- [Code Review](concepts/code-review.md) — Code review is the practice of a peer examining a proposed change before (or shortly after) it merges. It is the single highest-leverage team-level quality practice…
- [DORA Metrics](concepts/dora-metrics.md) — The DORA metrics (DevOps Research and Assessment) are a small, canonical set of four software-delivery throughput and stability metrics, first published in…
- [Observability](concepts/observability.md) — Observability is the property of a running system: the ability to infer its internal state from its external outputs — without having to be inside it, and…

### Lean & Flow

- [Batch Size](concepts/batch-size.md) — Smaller batches cut cycle time, variability, and risk; the trade-off is transaction cost, which automation reduces. Tags: `lean`, `flow`, `economics`, `ci-cd`
- [Cost of Delay](concepts/cost-of-delay.md) — The economic loss per unit of time a piece of value stays undelivered; the basis for sequencing work by WSJF. Tags: `lean`, `flow`, `economics`
- [Little's Law](concepts/littles-law.md) — For a stable system, average work in progress equals throughput times average cycle time (L = λW). Tags: `lean`, `flow`, `queueing`
- [Queueing & Utilization](concepts/queueing-and-utilization.md) — Queues, not workers, drive delay; high utilisation makes queues grow non-linearly. Tags: `lean`, `flow`, `queueing`, `economics`
- [Work-in-Progress (WIP) Limits](concepts/wip-limits.md) — Capping work in progress controls cycle time and forces rate-matching between stages. Tags: `lean`, `flow`, `queueing`

---

## Sources

- [Extreme Programming & Test-Driven Development — Kent Beck, Ward Cunningham](sources/beck-xp-tdd.md) — Works: Extreme Programming Explained (Kent Beck, 1999); the TDD red/green/refactor loop popularised through Ward Cunningham (1999) and Kent Beck. Ingested 2026-09-25.
- [Clean Code, Code Review & Craftsmanship — Robert C. Martin](sources/clean-code-review.md) — Works: Clean Code (Robert C. "Uncle Bob" Martin, 2008); the modern code review practice; the software craftsmanship movement (e.g. The Pragmatic Programmer, Hunt &… Ingested 2026-09-25.
- [The Principles of Product Development Flow — Donald G. Reinertsen (2009)](sources/reinertsen-product-development-flow.md) — Book: second-generation lean product development; roughly 175 principles on economics, queues, variability, batch size, WIP, and feedback. Compiled from secondary summaries, so principle codes need checking against the book. Ingested 2026-11-06.
- [Architecture Patterns with Python — Percival & Gregory (2020)](sources/architecture-patterns-with-python.md) — Book: DDD, TDD and event-driven design in Python; repository, service layer, unit of work, aggregates, domain events, ports and adapters. Written from knowledge and secondary summaries, so verify before quoting. Ingested 2026-11-06.
- [Domain-Driven Design — Eric Evans (2003)](sources/evans-ddd.md) — Book: Domain-Driven Design: Tackling Complexity in the Heart of Software (2003) Author: Eric Evans (the "blue book"). Ingested 2026-09-25.
- [Working Effectively with Legacy Code — Michael Feathers (2004)](sources/feathers-legacy-code.md) — Book: Working Effectively with Legacy Code (Michael Feathers, 2004) Author: Michael Feathers. Ingested 2026-09-25.
- [CI/CD, DORA & The DevOps Practice — Fowler, Forsgren et al.](sources/fowler-ci-cd.md) — Works: Continuous integration (Fowler, 2002); Continuous delivery (Fowler); Accelerate: The Science of DevOps (Forsgren, Humble, Kim, 2018) — origin of the DORA… Ingested 2026-09-25.
- [Refactoring — Martin Fowler (2001)](sources/fowler-refactoring.md) — Book: Refactoring: Improving the Design of Existing Code (1st ed. 2001, 2nd ed. 2018) Author: Martin Fowler (with Kent Beck). Ingested 2026-09-25.
- [Design Patterns: Elements of Reusable Object-Oriented Software — Gamma, Helm, Johnson, Vlissides (1994)](sources/gang-of-four.md) — Book: Design Patterns: Elements of Reusable Object-Oriented Software (1994) — "the Gang of Four" (GoF): Erich Gamma, Richard Helm, Ralph Johnson, John Vlissides. Ingested 2026-09-25.
