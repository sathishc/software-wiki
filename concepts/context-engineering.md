---
title: Context Engineering
tags: [ai-agents, context-engineering, architecture]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/anthropic-context-engineering.md, sources/anthropic-long-running-harnesses.md]
layout: default
parent: Concepts
---

# Context Engineering

**Context engineering** is the practice of deciding what goes into a model's
context window at each step, and in what form. Anthropic's post on the subject
treats it as a broader discipline than prompt engineering. A prompt is one part of the
context; the rest includes tool definitions, examples, message history, and
whatever data the agent retrieves. All of it competes for the model's attention.

## The central idea

Context is a finite attention budget. More tokens do not reliably mean better
output, and irrelevant material dilutes the signal. The aim is the smallest set of
high-signal tokens that makes the desired outcome likely. This is the same
discipline as [Keep It Simple (KISS)](./kiss.md) applied to the model's input.

## Techniques reported

- **Right-altitude system prompts.** Specific enough to guide behaviour, but not
  brittle hard-coded logic. Start minimal and add instructions in response to
  observed failures.
- **Minimal, non-overlapping tools.** Overlapping tools confuse the agent and
  consume context. See [Agent Tool Design](./agent-tool-design.md).
- **Just-in-time retrieval.** Keep references such as file paths and queries, and
  load the data when it is needed, rather than front-loading everything.
- **Compaction.** When the window is nearly full, summarise and continue from the
  summary. Clearing old tool results is the lightest form.
- **Structured notes.** Persist state outside the window, such as a progress file
  or a to-do list, so a later session can resume.
- **Sub-agents.** Specialised agents work in clean contexts and return a condensed
  summary to the parent.

## How it connects to software design

Context engineering has a close analogue in software architecture: each component
should see only what it needs, through a narrow interface. This is the reasoning
behind [Bounded Context](./bounded-context.md) and [API Design](./api-design.md).
The difference is that the consumer here is a model, and its "interface" is the
prompt. The [Long-Running Agents](./long-running-agents.md) concept shows how the
same ideas extend across sessions.

## Caveats

The advice reflects the reported experience of specific teams and models, and
the best balance of up-front and autonomous retrieval depends on the task. Measure
with [Agent Evals](./agent-evals.md) rather than assuming a technique helps.

See the [map](../pages/ai-agents-software-engineering.md) for the wider picture.
