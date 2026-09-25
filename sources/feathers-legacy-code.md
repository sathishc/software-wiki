---
title: "Working Effectively with Legacy Code — Michael Feathers (2004)"
tags: [sources, technical-debt, refactoring, legacy-code]
source: https://en.wikipedia.org/wiki/Working_Effectively_with_Legacy_Code
ingested: 2026-09-25
---

# Working Effectively with Legacy Code — Source Notes

**Book:** Working Effectively with Legacy Code (Michael Feathers, 2004)
**Author:** Michael Feathers

**Reference URLs captured:**
- https://en.wikipedia.org/wiki/Working_Effectively_with_Legacy_Code
- https://martinfowler.com/bliki/TechnicalDebt.html (origin of the term)

---

## What "legacy code" means (a deliberate redefinition)

Feathers redefines the term to remove the "old" connotation: **legacy code is
code without tests.** Code becomes "modern" the moment it is tested; a shiny
new feature with no tests is, by this definition, legacy. The age of the code
is irrelevant — *the absence of a safety net is the problem.*

## The core problem

You have a codebase that works but you cannot change it safely, because you do
not know what it does and you would be flying blind. The goal is to move code
from *untested* to *tested* so it can be refactored — to convert a
[Technical Debt](../concepts/technical-debt.md) liability into an asset.

## The two modes

- **Escape hatch** — when you must change legacy code to add a feature. You
  create a **seam** (a place you can inject a test), **characterize** the
  existing behaviour (record what the code does without changing it), and only
  then change it.
- **Exploring** — when you are not under a feature deadline and want to get a
  codebase into shape. You read the code to understand its intent, then build
  tests around what it does.

## Characterization tests

A **characterization test** (Feathers' key tool) records *the behaviour the
code currently has*, whatever that is, without assuming it is *correct*. It
distinguishes "the system does X" from "the system should do X." You use them
to freeze current behaviour, then decide which of it is intended and should be
preserved.

## Seams

A **seam** is a place in the program where you can alter behaviour without
editing that location — an abstraction boundary you can control in a test.
The whole art of testing untestable code is *creating seams* (extracting
interfaces, injecting dependencies) so you can stub the untestable parts and
drive the tested ones.

## The bigger lesson

This is [Technical Debt](../concepts/technical-debt.md) made operational. Debt is not a one-time "we'll fix
it later" item; it accrues **interest** — every change to untested code is
harder and riskier. Feathers shows the repayment loop: *test → create seam →
refactor →* the next change is easier. It is the same compound economics as
[Refactoring](../concepts/refactoring.md).

---
