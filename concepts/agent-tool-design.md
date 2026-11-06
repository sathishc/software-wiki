---
title: Agent Tool Design
tags: [ai-agents, api-design, architecture]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/anthropic-writing-tools-for-agents.md, sources/anthropic-building-effective-agents.md]
layout: default
parent: Concepts
---

# Agent Tool Design

**Agent tool design** is the craft of building the tools an AI agent can call so
that the agent uses them correctly. Anthropic's post calls this the
**agent-computer interface**, and argues it deserves the same care as a human
interface. A tool is a contract between a deterministic system and a model that
reads descriptions, picks options, and fills in arguments, and the model can
misuse a poorly designed contract in ways a developer would not.

## Design principles (as reported)

- **Design for the workflow, not the endpoint.** Wrapping every API endpoint as a
  tool creates a large, overlapping set. Consolidate multi-step operations into
  one tool that matches a task the agent needs to do.
- **Namespace clearly.** Group tools by service and resource so the agent can tell
  them apart. Test naming conventions, since prefix versus suffix changes results.
- **Return context the agent can use.** Human-readable names beat opaque IDs. A
  response-format option lets the agent ask for concise or detailed output.
- **Keep responses small.** Use pagination, filters and truncation with sensible
  defaults. Error messages should say what to try next.
- **Write descriptions carefully.** Treat each description as onboarding material,
  name inputs unambiguously, and enforce strict schemas.
- **Measure.** Evaluate tools with real tasks and read the transcripts.

## The software-design parallel

Most of these principles are familiar from [API Design](./api-design.md): a small
stable surface, clear naming, predictable errors, and designing for the consumer.
The difference is that the consumer is a model that reads the documentation at
run time, so description quality matters as much as the implementation. Tool sets
also suffer from the same problem as large interfaces, which is why
[Single Responsibility (SOLID)](./solid.md) thinking helps: each tool should do
one job well.

## Testing tools

Tools can be unit tested like any other code, but the question that matters is
whether an agent picks and uses them correctly. That is measured with
[Agent Evals](./agent-evals.md), which is why the Anthropic post recommends running
tool changes through evaluation tasks rather than judging them by reading.

See also [Context Engineering](./context-engineering.md), since every tool
definition consumes part of the model's context, and the [map](../pages/ai-agents-software-engineering.md).
