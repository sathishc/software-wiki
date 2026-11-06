---
title: "Building Effective AI Agents — Anthropic Engineering (2024)"
tags: [sources, ai-agents, architecture, design-patterns]
source: https://www.anthropic.com/engineering/building-effective-agents
ingested: 2026-11-06
---

# Building Effective AI Agents — Source Notes

**Publisher:** Anthropic, Engineering blog
**Authors:** Erik Schluntz and Barry Zhang
**Published:** 19 December 2024

**Provenance note:** Checked against the full post, fetched in this session.
The section names and the five workflow patterns were confirmed in the text; the
notes were not verified line by line.

---

## Thesis

The post argues that the most successful agent implementations use simple,
composable patterns rather than complex frameworks. It separates two kinds of
system. A **workflow** orchestrates LLM calls and tools through predefined code
paths. An **agent** lets the LLM decide its own process and tool use in a loop,
guided by feedback from the environment. The post recommends starting with the
simplest thing that works, and adding agentic complexity only when it measurably
improves outcomes.

## Key points (as reported)

- **Augmented LLM** is the basic building block: a model with retrieval, tools
  and memory. The Model Context Protocol is mentioned as one way to implement it.
- **Workflow patterns** named in the post: prompt chaining, routing,
  parallelisation (sectioning and voting), orchestrator-workers, and
  evaluator-optimiser. See [Agentic Workflow Patterns](../concepts/agentic-workflow-patterns.md).
- **Frameworks can hide prompts and make debugging harder**, so calling model
  APIs directly is often enough to start with.
- **Three principles:** keep the design simple, make the agent's planning steps
  visible, and design the agent-computer interface carefully, including thorough
  tool documentation and testing. See [Agent Tool Design](../concepts/agent-tool-design.md).
- Agents should be tested extensively in sandboxed environments.

## Cross-references

- Builds on the shared vocabulary in [AI Agents](../concepts/ai-agents.md) and
  [Agent Harness](../concepts/agent-harness.md).
- Compare with OpenAI's [practical guide](./openai-practical-guide-building-agents.md)
  and the [context engineering](./anthropic-context-engineering.md) post.
- Map: [Building Software with AI Agents](../pages/ai-agents-software-engineering.md).
