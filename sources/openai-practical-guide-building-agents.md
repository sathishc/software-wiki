---
title: "A Practical Guide to Building Agents — OpenAI"
tags: [sources, ai-agents, architecture, evals]
source: https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf
ingested: 2026-11-06
---

# A Practical Guide to Building Agents — Source Notes

**Publisher:** OpenAI
**Format:** Guide (PDF), with a related "Building agents" learning track on the OpenAI developer site

**Provenance note:** Still based on search-result excerpts. The PDF was retrieved
in this session, but its text could not be extracted for checking, so none of
the claims below have been verified against the guide.

---

## Thesis

An agent is a system that uses an LLM to manage workflow execution and
decisions, and has access to tools to gather context and take actions within
defined guardrails. Simple chatbots, single LLM calls and classifiers are not
agents. The guide's advice is to build agents only where the problem needs
judgement, has rules that are hard to maintain, or depends on unstructured
data, and otherwise to use a deterministic solution.

## Key points (as reported)

- **Three core components:** a model, tools (data, action and orchestration
  tools), and instructions.
- **Model selection.** Prototype with the most capable model, set up evals to get
  a baseline, then swap in smaller models to reduce cost and latency where the
  evals still pass.
- **Orchestration.** Start with a single agent running in a loop, and add tools
  before adding agents. For multi-agent systems, two patterns are described: a
  manager agent that calls specialist agents as tools, and decentralised agents
  that hand off to one another.
- **Guardrails.** Layered defences covering privacy and brand risk, backed by
  authentication, access control and standard software security.

## Cross-references

- Concepts: [AI Agents](../concepts/ai-agents.md), [Agentic Workflow Patterns](../concepts/agentic-workflow-patterns.md),
  [Agent Evals](../concepts/agent-evals.md).
- Compare with [Building Effective AI Agents (Anthropic)](./anthropic-building-effective-agents.md).
- Map: [Building Software with AI Agents](../pages/ai-agents-software-engineering.md).
