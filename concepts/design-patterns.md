---
title: Design Patterns
tags: [design-patterns, architecture, oop, gang-of-four]
created: 2026-09-25
updated: 2026-09-25
sources: [sources/gang-of-four.md, sources/fowler-refactoring.md]
layout: default
parent: Concepts
---

# Design Patterns

A **design pattern** is a *named, reusable template* for solving a recurring
design problem — not a ready-made class to paste, but a *description* of a
problem, the elements of a solution, how they fit together, and the
**consequences** (the trade-offs) of using it. The idea was popularised by the
Gang of Four (Gamma, Helm, Johnson, Vlissides, 1994) in *Design Patterns*.

## The 23 GoF patterns, in three families

**Creational** — how objects are constructed, decoupled from their concrete type:
Factory Method, Abstract Factory, Builder, Prototype, Singleton.

**Structural** — how objects/classes are composed to form larger structures:
Adapter, Bridge, Composite, Decorator, Facade, Proxy.

**Behavioral** — how objects communicate and responsibilities are assigned:
Chain of Responsibility, Command, Iterator, Mediator, Memento, Observer, State,
Strategy, Visitor.

## The real point: patterns are a *communication* device

The *power* of a pattern is not the shape — it's that **saying the name shares
the whole design in a few words.** "Let's use an Observer here" lets two
engineers align on an entire subsystem with three words. That *naming* is what
makes a pattern a pattern; the GoF book's lasting gift is that it *gave names*
to solutions that existed anonymously before.

## The consequences matter most (and the modern caveats)

Every pattern is a **decision with trade-offs**, and the *consequences* — the
coupling it introduces, the flexibility it buys, the complexity it adds — are
the part that actually matters. The modern caveats:

- **Patterns are tools, not dogma.** Reaching for a pattern to *use a pattern*
  (a premature Observer, a gratuitous Singleton) is a [You Aren't Gonna Need It (YAGNI)](./yagni.md) violation.
  Pattern-for-pattern's-sake is the anti-pattern of pattern-theory.
- **They're mostly about *decoupling* and *flexibility*.** A pattern earns its
  keep when you *actually expect variation* (you'll add a new handler, a new
  payment provider, a new output format). If you don't, plain code is simpler.
- **Languages matter.** Some patterns are idioms of *one* language and not
  others; a pattern that's clean in C# may be ugly (or unnecessary) in a
  functional language. See [Functional Programming](./functional-programming.md).

## Related Pages

- [SOLID](./solid.md)
- [Refactoring](./refactoring.md)
- [Domain-Driven Design](./domain-driven-design.md)
- [YAGNI](./yagni.md)

## Sources

- **[Design Patterns (GoF)](../sources/gang-of-four.md)**
- [Refactoring](../sources/fowler-refactoring.md)

## Maps of Content

- [Architecture & Design](../pages/architecture.md)
