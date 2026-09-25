---
title: "Clean Code, Code Review & Craftsmanship — Robert C. Martin"
tags: [sources, clean-code, code-review, craftsmanship, robert-martin, solid]
source: https://en.wikipedia.org/wiki/Clean_Code
ingested: 2026-09-25
---

# Clean Code, Code Review & Craftsmanship — Source Notes

**Works:** *Clean Code* (Robert C. "Uncle Bob" Martin, 2008); the modern
**code review** practice; the software **craftsmanship** movement (e.g. *The
Pragmatic Programmer*, Hunt & Thomas, 1999).

**Reference URLs captured:**
- https://en.wikipedia.org/wiki/Clean_Code
- https://en.wikipedia.org/wiki/Code_review
- https://pragprog.com/titles/tpp2nd/the-pragmatic-programmer-20th-anniversary-edition/

---

## Clean Code

*Clean Code* is Robert C. Martin's handbook for making code that **reads well
and is easy to change.** "Clean" here means readable, well-structured, honest
about intent, and free of the [Code Smells](../concepts/code-smells.md) that accumulate passively. The
book is a *style and structure* guide; its most-used prescriptions:

- **Names** should be intention-revealing, unambiguous, and informative (the
  number-one rule; a bad name compounds, a good name is the cheapest
  documentation).
- **Functions** should be small, do one thing, and sit at one level of
  abstraction.
- **Comments** should explain *why*, not *what* (the code shows the what); a
  bad comment is a liability.
- **Formatting** is a shared, mechanical convention — automate it so people can
  argue about design instead of whitespace.
- **Error handling** should be in one place and never swallow silently.

The underlying claim: **readability is a feature.** Code is written once and
read many times, by many people, over years. Every line you write is a
[Technical Debt](../concepts/technical-debt.md) liability *or* an asset, depending on how well it reads.
Clean Code is the individual-contributor-level expression of the same economics
as [Refactoring](../concepts/refactoring.md).

## Code review

**Code review** is a peer examining a proposed change before (or shortly after)
it merges. It is the single highest-leverage *team-level* quality practice, for
three reasons:

1. **It catches bugs** — a second pair of eyes finds what the author's
   over-familiarity hides.
2. **It spreads knowledge** — the cheapest way to keep the team from becoming a
   set of silos; everyone learns everyone else's code.
3. **It enforces the standard** — where the team's "what does good look like"
   gets made consistent, culture-level.

The modern best-practice shape (from years of practice at high-performing
teams): **small reviews** (a few hundred lines max — a review past that is
dysfunctional), **fast turnaround** (hours, not days — review latency is its
own form of lead time), **kind and specific** feedback (comment on the code,
not the coder; request *changes* rather than *judging*), and **automated
first** (lint, format, and tests run before a human ever reads a line).
Review throughput is a deliverable: piling up review queues is a hidden
[Continuous Integration & Continuous Delivery (CI/CD)](../concepts/ci-cd.md) / [DORA Metrics](../concepts/dora-metrics.md) drag on **lead time for changes**.

## Craftsmanship

The **software craftsmanship** movement (Pragmatic Programmer, Agile, the
"craft") is the umbrella belief that software is a *craft* to be practised with
pride — worth doing well on its own merits, not just to satisfy a spec. Its
recurring mantras: **Don't Repeat Yourself** ([Don't Repeat Yourself (DRY)](../concepts/dry.md)), **Keep It Simple**
([Keep It Simple (KISS)](../concepts/kiss.md)), **You Aren't Gonna Need It** ([You Aren't Gonna Need It (YAGNI)](../concepts/yagni.md)), and **the boy-scout rule**
(leave the code a little cleaner than you found it). See [Code Quality](../pages/code-quality.md) for
how these fit together.

---
