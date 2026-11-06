---
title: Agentic Workflow Patterns
tags: [ai-agents, design-patterns, architecture]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/anthropic-building-effective-agents.md, sources/openai-practical-guide-building-agents.md]
layout: default
parent: Concepts
---

# Agentic Workflow Patterns

Between a single model call and a fully autonomous [AI agent](./ai-agents.md) lies a
set of composable patterns. Anthropic's post on building effective agents names
several, and each one is a [design pattern](./design-patterns.md) in the classic sense:
a named solution to a recurring problem, with trade-offs that make it suit some
situations and not others.

## The patterns (as named in the Anthropic post)

- **Prompt chaining.** Break a task into steps, where each LLM call processes the
  output of the last. Useful when the task splits cleanly and a check can sit between steps.
- **Routing.** Classify an input and send it to a specialised prompt or model.
  Useful when different kinds of input need different handling.
- **Parallelisation.** Run independent calls at the same time. Sectioning splits a
  task into parts; voting runs the same task several times for a more reliable answer.
- **Orchestrator-workers.** A central model breaks the task down and delegates the
  parts to worker calls, then combines the results. Useful when the subtasks are not
  known in advance.
- **Evaluator-optimiser.** One model produces output and another critiques it in a
  loop until the output meets a standard. Useful when a clear quality bar exists.

OpenAI's guide makes a related distinction for multi-agent systems: a **manager**
pattern, where one agent calls specialist agents as tools, and a **decentralised**
pattern, where agents hand off control to one another.

## Choosing one

Both sources advise starting with the simplest pattern that works, and adding
structure only when measurement shows it helps. Each extra step adds latency,
cost and a new point of failure. The choice is an architectural trade-off, which is
why these patterns sit alongside [Microservices](./microservices.md) and
[Monolith](./monolith.md) thinking: more moving parts buy flexibility at the price
of coordination. Evaluate each choice with [Agent Evals](./agent-evals.md).

## Relation to the wider wiki

The orchestrator-workers and evaluator-optimiser patterns are close to
[Observability](./observability.md)-driven feedback loops, and the handoff pattern
has the same coupling concerns as [Bounded Context](./bounded-context.md) boundaries.
See the [map](../pages/ai-agents-software-engineering.md).
