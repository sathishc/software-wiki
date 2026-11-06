---
title: Human Review of Agent Work
tags: [ai-agents, code-review, quality]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/stripe-minions-and-payment-method-factory.md, sources/openai-practical-guide-building-agents.md, sources/anthropic-long-running-harnesses.md]
layout: default
parent: Concepts
---

# Human Review of Agent Work

Human review of agent output is the practice of having a person check what an
[AI agent](./ai-agents.md) produced before it is accepted into the codebase. It
applies the existing [Code Review](./code-review.md) discipline to a new source of
change. The sources in this wiki describe it as a checkpoint rather than an
obstacle: Stripe reports that every agent-produced pull request is human-reviewed,
and OpenAI's guide recommends layered guardrails for agents that take actions.

## What changes when the author is an agent

The reviewer's job shifts. An agent does not get tired or forget, but it can make
plausible mistakes, and its code can look polished while being wrong in subtle
ways. Reviewers therefore need to check behaviour and intent, not only style. The
review question moves from "is this well written?" to "does this do what was asked,
and is it safe?". A clear task definition and a passing test suite matter more,
because they give the reviewer a stable reference.

## Practices that reduce review load

Keep each agent change small, which is the same logic as [Batch Size](./batch-size.md):
a small diff is easier to check and cheaper to revert. Require the agent to leave the
work in a clean, mergeable state with a description of what it changed, as the
Anthropic long-running-agent post suggests. Let CI run the mechanical checks, so the
human looks at what the tests cannot decide. Automated checks are covered by
[Continuous Integration & Continuous Delivery (CI/CD)](./ci-cd.md).

## Risks of too little review

Review is the main safeguard when evals are incomplete. Without it, agent errors
reach production under the appearance of tested code. The cost of a missed defect
is the same as in any change, which is why the [DORA Metrics](./dora-metrics.md)
change-failure rate remains the right measure of whether agent work is healthy.

## Related

Human review is one of several controls alongside [Agent Evals](./agent-evals.md)
and the [Agent Harness](./agent-harness.md) limits. See the
[map](../pages/ai-agents-software-engineering.md).
