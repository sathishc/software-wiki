---
title: "Extreme Programming & Test-Driven Development — Kent Beck, Ward Cunningham"
tags: [sources, tdd, xp, testing, kent-beck, ward-cunningham]
source: https://en.wikipedia.org/wiki/Extreme_programming
ingested: 2026-09-25
---

# XP & TDD — Source Notes

**Works:** *Extreme Programming Explained* (Kent Beck, 1999); the TDD
red/green/refactor loop popularised through **Ward Cunningham** (1999) and
**Kent Beck**.

**Reference URLs captured:**
- https://en.wikipedia.org/wiki/Extreme_programming
- https://en.wikipedia.org/wiki/Test-driven_development
- https://c2.com/cgi/wiki?TestDrivenDevelopment

---

## Extreme Programming (XP)

XP is a *lightweight* methodology that pushes classic software practices to
the extreme: pair programming, continuous integration, on-site customer,
week-long releases, and above all — **test-first development** and
**refactoring**. It is the origin point for [Test-Driven Development (TDD)](../concepts/tdd.md).

## Test-Driven Development (TDD)

The **red–green–refactor** loop:

1. **Red** — write a *failing* test that specifies a small piece of desired
   behaviour.
2. **Green** — write the *simplest* code that makes the test pass.
3. **Refactor** — clean the code (remove duplication, clarify names) while
   keeping the test green; then repeat.

The discipline's key properties:

- **Tests are the specification.** Writing the test *first* forces you to
  articulate what "done" means before you build it.
- **Tests are a live safety net.** A green suite at any point means the code
  works *now* — which is what makes [Refactoring](../concepts/refactoring.md) safe.
- **Tests are executable documentation.** They encode intent far more precisely
  than prose.
- **Small increments.** Each loop is minutes, not days — tiny, verifiable steps.

## What TDD is *not*

It is **not** 100% test coverage (coverage is a by-product, not the goal), and
it is **not** writing many end-to-end tests first — that is the opposite of the
[Test Pyramid](../concepts/test-pyramid.md) (fast unit tests at the base, expensive integration tests at
the top). TDD is a *design* discipline as much as a *testing* one: thinking
about the interface before the implementation reshapes the code into something
simpler and more loosely coupled.

## Ward Cunningham's role

Cunningham is widely credited as one of the first to use test-first development
(around 1999, with his Selenoid browser-automation framework) and to name the
practice. Beck formalised and popularised it with *XP Explained* and the JUnit
test harness.

---
