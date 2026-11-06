---
title: Unit Testing
tags: [unit-testing, testing, quality, tdd]
created: 2026-09-25
updated: 2026-11-06
sources: [sources/beck-xp-tdd.md, sources/feathers-legacy-code.md]
layout: default
parent: Concepts
---

# Unit Testing

**Unit testing** is the practice of testing the *smallest testable piece* of
software — a single function, method, or class — in **isolation**, with its
dependencies stubbed or faked. It is the **base of the [Test Pyramid](./test-pyramid.md)** and
the safety net that makes [Refactoring](./refactoring.md) and [Test-Driven Development (TDD)](./tdd.md) possible.

## The shape of a unit test

A *unit test* answers one question about one unit: **"Given this input, does
the unit behave as specified?"** The properties that make it a *unit* test
(and not an integration test):

- **Isolated** — the unit under test is exercised on its own; its collaborators
  are replaced with **doubles** (stubs, fakes, mocks, spies) so the test is
  fast and deterministic.
- **Fast** — microseconds, not seconds. You can run the *whole* suite in
  seconds, which is what makes "run tests after every change" a habit.
- **Deterministic** — no timing, no network, no randomness, no order-
  dependence. A flaky unit test is worse than none, because it erodes trust in
  the green.
- **Independent** — tests don't depend on each other's order or on global
  state; any one can run alone.

## Why it's the linchpin

Unit testing is the *enabler* the rest of the wiki rests on:

- It makes **[Refactoring](./refactoring.md) safe** — "the tests pass" is the proof you didn't
  break behaviour.
- It is the **[Test-Driven Development (TDD)](./tdd.md) loop** — the red step *is* writing a unit test first.
- It is **[Technical Debt](./technical-debt.md)'s repayment** — untested code is legacy code
  (Feathers); adding unit tests is the single act that converts a liability
  into an asset.
- It is what a **[Code Review](./code-review.md)** relies on — the reviewer checks that the
  *behaviour* is covered, not just the happy path.

## The honest caveats

- **Coverage is not the goal.** 100% line coverage with a test that asserts
  nothing proves nothing. *Meaningful* assertions on *behaviour* are the goal;
  coverage is a weak *by-product* you can track, never the target.
- **Unit tests are necessary but not sufficient.** They can't catch
  integration bugs (two correct units wired together wrong). You still need the
  integration and end-to-end layers of the [Test Pyramid](./test-pyramid.md).

## Related Pages

- [TDD](./tdd.md)
- [Test Pyramid](./test-pyramid.md)
- [Refactoring](./refactoring.md)
- [Code Review](./code-review.md)

## Sources

- [XP & TDD](../sources/beck-xp-tdd.md)
- [Working Effectively with Legacy Code](../sources/feathers-legacy-code.md)

## Maps of Content

- [Testing & Quality](../pages/testing.md)

## See also

- [Test-Driven Development (TDD)](tdd.md)
- [Test Pyramid](test-pyramid.md)
- [Refactoring](refactoring.md)
- [Dependency Injection](dependency-injection.md)
- [Ports and Adapters (Hexagonal Architecture)](ports-and-adapters.md)
- [Building Software with AI Agents](../pages/ai-agents-software-engineering.md)
