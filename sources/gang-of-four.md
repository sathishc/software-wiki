---
title: "Design Patterns: Elements of Reusable Object-Oriented Software — Gamma, Helm, Johnson, Vlissides (1994)"
tags: [sources, design-patterns, architecture, oop, gang-of-four]
source: https://en.wikipedia.org/wiki/Design_Patterns
ingested: 2026-09-25
---

# Design Patterns (Gang of Four) — Source Notes

**Book:** Design Patterns: Elements of Reusable Object-Oriented Software
(1994) — "the Gang of Four" (GoF): Erich Gamma, Richard Helm, Ralph Johnson,
John Vlissides.

**Reference URLs captured:**
- https://en.wikipedia.org/wiki/Design_Patterns
- https://refactoring.com/catalog/ (Fowler's catalogue — pattern-adjacent)

---

## What a design pattern is

The GoF book popularised the idea that **recurring design solutions** to
recurring problems can be *named*. A **design pattern** is a *template* for
solving a problem that can be over and over again without being copied the
same way each time. It is a *description of a problem, the elements that make
up the solution, how they fit together, and the consequences* — not a ready-
made class to paste.

## The 23 GoF patterns, in three families

**Creational** (how you construct objects, loosely coupled):
- **Factory Method** — let a class delegate instantiation to a subclass/factory.
- **Abstract Factory** — create families of related objects without specifying
  concrete classes.
- **Builder** — separate the construction of a complex object from its
  representation; stepwise construction.
- **Prototype** — clone an existing object rather than building from scratch.
- **Singleton** — ensure a class has exactly one instance, with a global point
  of access. (The most infamous and most misused of the 23.)

**Structural** (how objects/classes are composed):
- **Adapter** — convert one interface into another the client expects.
- **Bridge** — separate an abstraction from its implementation so the two can
  vary independently.
- **Composite** — treat a tree of objects uniformly (part-whole).
- **Decorator** — attach behaviour to an object dynamically, compositionally,
  instead of subclass explosion.
- **Facade** — a simple interface to a complex subsystem.
- **Proxy** — stand-in that controls access to the real object.

**Behavioral** (how objects communicate / responsibilities are assigned):
- **Chain of Responsibility** — pass a request down a chain of handlers.
- **Command** — encapsulate a request as an object.
- **Iterator** — traverse a collection without exposing its representation.
- **Mediator** — centralise communication between a set of objects.
- **Memento** — capture/restore internal state without violating encapsulation.
- **Observer** — define one-to-many dependencies (the pub/sub backbone).
- **State** — alter behaviour when internal state changes.
- **Strategy** — define a family of interchangeable algorithms; swap at runtime.
- **Visitor** — add operations over a structure without changing its classes.

## The deeper lesson

The GoF book is less a *catalogue to memorise* than an argument that **naming a
pattern is a communication device**: saying "let's use an Observer here" lets
two engineers share an entire design in three words. The *consequences* of a
pattern (its trade-offs, coupling it introduces, flexibility it buys) are the
part that matters most — every pattern is a *decision*, not a free lunch. See
[Design Patterns](../concepts/design-patterns.md) for when each earns its keep and the modern caveats
(especially: patterns are tools, not dogma; a premature pattern is a
[You Aren't Gonna Need It (YAGNI)](../concepts/yagni.md) violation).

---
