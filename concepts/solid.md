---
title: SOLID
tags: [solid, oop, architecture, design-patterns, code-quality]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/clean-code-review.md, sources/gang-of-four.md]
layout: default
parent: Concepts
---

# SOLID

**SOLID** is a mnemonic for five single-letter design principles, coined by
**Robert C. Martin** [Robert-Martin](../people/robert-martin.md) to codify what "well-structured
object-oriented code" means. They are the most-taught design heuristics in the
OO world.

## The five principles

| Letter | Name | Core idea |
|---|---|---|
| **S** | **Single Responsibility** | A type should have one, and only one, *reason to change*. |
| **O** | **Open/Closed** | Open for extension, closed for modification. |
| **L** | **Liskov Substitution** | Subtypes must be substitutable for their base type without breaking behaviour. |
| **I** | **Interface Segregation** | Many client-specific interfaces beat one fat interface. |
| **D** | **Dependency Inversion** | Depend on abstractions, not on concretions. |

## The common thread

All five are facets of the same goal: **loose coupling and high cohesion**, so
that a change in one part of the system ripples through *few* other parts.
They are the *why* behind much of [Refactoring](./refactoring.md) — "extract this method",
"introduce this interface", "depend on this abstraction" are SOLID in action.

## The honest caveats

- SOLID is a **design** discipline for *object-oriented* systems. Applied
  blindly to scripts, functional code, or a 50-line utility, it produces
  ceremonial bloat (five files for one feature). It is a *heuristic for where
  flexibility is expected*, not a rule for every line.
- They describe *static* structure, not *behaviour*. A system can be SOLID and
  still brittle, slow, or wrong. They are necessary, not sufficient — see
  [Clean Code](./clean-code.md) and [Code Quality](../pages/code-quality.md) for the behavioural half.

## Related Pages

- [Clean Code](./clean-code.md)
- [Refactoring](./refactoring.md)
- [Design Patterns](./design-patterns.md)
- [YAGNI](./yagni.md)

## Sources

- [Clean Code, Code Review & Craftsmanship](../sources/clean-code-review.md)
- [Design Patterns (GoF)](../sources/gang-of-four.md)

## Maps of Content

- [Code Quality](../pages/code-quality.md)
- [Architecture & Design](../pages/architecture.md)

## See also

- [Dependency Injection](dependency-injection.md)
- [Refactoring](refactoring.md)
- [Design Patterns](design-patterns.md)
- [Clean Code](clean-code.md)
- [Don't Repeat Yourself (DRY)](dry.md)
- [Code Smells](code-smells.md)
