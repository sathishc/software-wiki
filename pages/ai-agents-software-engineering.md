---
title: Building Software with AI Agents
tags: [moc, ai-agents, evals, delivery, architecture]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/anthropic-building-effective-agents.md, sources/anthropic-context-engineering.md, sources/anthropic-writing-tools-for-agents.md, sources/anthropic-demystifying-evals.md, sources/anthropic-long-running-harnesses.md, sources/openai-practical-guide-building-agents.md, sources/stripe-minions-and-payment-method-factory.md]
layout: default
parent: Pages
---

# Building Software with AI Agents

> A curated map of how software gets built when an AI agent does part of the work.
> The subject is new, and the sources are recent company write-ups, not settled
> research, so this map records what practitioners report and how it connects to
> the older craft of testing, delivery and design.

## The one-line idea

**An agent is a loop around a model, and most of the engineering effort goes into
everything around the model**: its context, its tools, its harness, its evaluations,
and the review that stops its mistakes reaching production. The model is the part
that changes fastest; the surrounding discipline is what carries over.

## How the pieces fit

The chain runs from definition to measurement. [AI Agents](../concepts/ai-agents.md)
define what the system is, and [Agentic Workflow Patterns](../concepts/agentic-workflow-patterns.md)
set out how much autonomy to grant. The [Agent Harness](../concepts/agent-harness.md)
runs the loop, while [Context Engineering](../concepts/context-engineering.md) decides
what the model sees and [Agent Tool Design](../concepts/agent-tool-design.md) shapes
what it can do. [Long-Running Agents](../concepts/long-running-agents.md) extend the
loop across sessions. [Agent Evals](../concepts/agent-evals.md) measure whether any of
this works, and [Human Review of Agent Work](../concepts/human-review-of-agent-work.md)
is the final check before code is accepted.

## Reading order

1. [AI Agents](../concepts/ai-agents.md): what counts as an agent, and when not to build one.
2. [Agentic Workflow Patterns](../concepts/agentic-workflow-patterns.md): the simplest structures that work.
3. [Agent Harness](../concepts/agent-harness.md): the code that runs the loop.
4. [Context Engineering](../concepts/context-engineering.md): what goes into each step.
5. [Agent Tool Design](../concepts/agent-tool-design.md): the interface the model uses.
6. [Agent Evals](../concepts/agent-evals.md): how to tell whether it works.
7. [Long-Running Agents](../concepts/long-running-agents.md) and [Human Review of Agent Work](../concepts/human-review-of-agent-work.md): sustaining the work and checking it.

## What the sources agree on

Across Anthropic, OpenAI and Stripe, the same advice recurs. Start with the simplest
structure that works, and add autonomy only when it measurably helps. Invest in
evaluations early, because they are how a team knows whether a change helped. Keep
tools few, clear and token-efficient. Treat context as a scarce budget. Keep a human
review in the path. Stripe's numbers, as reported, show the payoff: unattended agents
produce over a thousand reviewed PRs a week, and a reusable prompt library cut an
integration from a bake-off of about twenty engineering days to four.

## Connections to the existing wiki

The agent material is an extension of the craft already in the wiki, not a separate
field. Evals are the agent form of the [Testing & Quality](./testing.md) map: isolation,
determinism and fast feedback from [Unit Testing](../concepts/unit-testing.md) and the
[Test Pyramid](../concepts/test-pyramid.md). Review and delivery reuse
[Code Review](../concepts/code-review.md) and [Continuous Integration & Continuous Delivery (CI/CD)](../concepts/ci-cd.md),
and the [Delivery](./delivery.md) map's measures, such as [DORA Metrics](../concepts/dora-metrics.md),
still say whether the whole system is getting healthier. Tool design leans on
[API Design](../concepts/api-design.md), and the harness structure follows the boundary
thinking of [Ports and Adapters](../concepts/ports-and-adapters.md) and
[Architecture & Design](./architecture.md). Small agent changes follow the same logic
as [Batch Size](../concepts/batch-size.md) in [Lean Product Development](./lean-product-development.md).

## Open questions and caveats

Most of these sources are company write-ups and recent posts, not peer-reviewed
studies, and several figures come from excerpts that have not been checked against
the full text. The best practices are still moving. Treat each claim as a hypothesis
to test with your own [Agent Evals](../concepts/agent-evals.md). The source notes record
which sources were read in full and which were not.
