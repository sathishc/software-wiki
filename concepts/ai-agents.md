---
title: AI Agents
tags: [ai-agents, architecture, design-patterns]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/anthropic-building-effective-agents.md, sources/openai-practical-guide-building-agents.md]
layout: default
parent: Concepts
---

# AI Agents

An **AI agent** is a system in which a large language model decides, in a loop,
what to do next: it chooses tools, takes actions, observes the results, and
continues until a goal is met or it stops. The loop is what separates an agent
from a single model call. Both [Anthropic](../sources/anthropic-building-effective-agents.md)
and [OpenAI](../sources/openai-practical-guide-building-agents.md) describe an agent
in these terms, and OpenAI's guide notes that a single-turn model call or a classifier does not count as one.

## Workflows versus agents

Anthropic draws a useful line between **workflows**, where code decides the
sequence of LLM calls and tool uses, and **agents**, where the model decides its
own process. A workflow is more predictable and easier to test. An agent is more
flexible and harder to bound. The advice in both sources is to prefer the simplest
option that works, and move to an agent only when the task needs judgement that a
fixed path cannot capture. The patterns that sit between the two are covered in
[Agentic Workflow Patterns](./agentic-workflow-patterns.md).

## The core components

OpenAI's guide names three parts: a model, the tools it can call (data tools,
action tools and orchestration tools), and instructions that define its role and
limits. The rest of the design is about making those parts reliable. The
[Agent Harness](./agent-harness.md) runs the loop, [Agent Tool Design](./agent-tool-design.md)
shapes the tools, and [Context Engineering](./context-engineering.md) decides what
the model sees at each step.

## Where agents fit in software work

Agents are most useful for work with clear inputs, a checkable outcome, and a
cost of trying that is low, such as fixing a bug with a failing test or writing
a migration. They are less suited to work where success is a matter of taste or
where a mistake is hard to reverse. Whatever the task, the agent's output enters
the same path as any other change, and so it needs the same [Code Review](./code-review.md)
and [Continuous Integration & Continuous Delivery (CI/CD)](./ci-cd.md) gates.

## Risks

Agents act, so they can act wrongly. Guardrails, least-privilege tools and
human checkpoints are the usual controls. The [Human Review of Agent Work](./human-review-of-agent-work.md)
concept covers the review side. For the wider picture, see the
[map](../pages/ai-agents-software-engineering.md).
