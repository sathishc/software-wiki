---
title: "Stripe: Minions and the Payment Method Factory (stripe.dev)"
tags: [sources, ai-agents, delivery, code-review, ci-cd]
source: https://stripe.dev/blog/topic/developer-productivity
ingested: 2026-11-06
---

# Stripe: Minions and the Payment Method Factory — Source Notes

**Publisher:** Stripe, engineering blog (stripe.dev)
**Posts:** "Minions: Stripe's one-shot, end-to-end coding agents" (Parts 1 and 2),
and the Payment Method Factory write-up.

**Provenance note:** The Minions Part 1 post was fetched in full in this session,
and the Slack invocation, the Ruby and Sorbet codebase, and the human review of
every PR were confirmed. The Payment Method Factory post and Minions Part 2 were
not fetched, so the figures from them still rest on search excerpts. Part 2's
1,300+ PR figure is unverified.

---

## Minions: unattended coding agents

Stripe describes **minions**: one-shot, end-to-end coding agents that run without
a human at the keyboard. A run usually starts from a Slack message and ends in a
pull request that passes CI. The post reports that over 1,000 PRs a week are now
produced this way (Part 2 gives 1,300+), that every one is reviewed by a human,
and that the code is written by the agents rather than by hand. Engineers run
several minions in parallel, which was particularly useful during on-call. The
codebase is large, mostly Ruby with Sorbet, and uses many internal libraries, so
the agents reuse Stripe's existing developer tooling rather than a separate stack.

## Payment Method Factory: reusable prompts

Stripe reports a system of over 100 reusable, hardened prompts for building
payment-method integrations. Reported results: integration timelines fell from up
to six months to two to six weeks. In a bake-off, a plain Claude Code setup took
about 20 engineering days, against 4 days with the reusable prompts. The factory
uses an **observer agent** to critique implementation runs, and agents test their
own work against provider sandboxes.

## Relevance to this wiki

Stripe's examples are about **throughput with review**, not replacing review. The
human reviews every PR, which ties the work to [Code Review](../concepts/code-review.md).
The reusable prompts and observer agent are a form of
[Agent Harness](../concepts/agent-harness.md) engineering. Running agents on the
existing tooling and CI is the [Continuous Integration & Continuous Delivery (CI/CD)](../concepts/ci-cd.md)
discipline applied to agent output, and the observer and sandbox tests are a form
of [Agent Evals](../concepts/agent-evals.md).

## Cross-references

- Map: [Building Software with AI Agents](../pages/ai-agents-software-engineering.md).
- Concept: [Human Review of Agent Work](../concepts/human-review-of-agent-work.md).
