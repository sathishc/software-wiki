---
title: "Effective Context Engineering for AI Agents — Anthropic (2025)"
tags: [sources, ai-agents, context-engineering]
source: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
ingested: 2026-11-06
---

# Effective Context Engineering for AI Agents — Source Notes

**Publisher:** Anthropic (applied AI team)
**Published:** 29 September 2025 (date from a third-party summary)

**Provenance note:** Checked against the full post, fetched in this session.
Compaction, structured note-taking, and the 1,000–2,000 token sub-agent summaries
were confirmed in the text. The publication date comes from a third-party summary
and has not been confirmed.

---

## Thesis

Context is a finite resource with diminishing returns. An LLM has an attention
budget, and every extra token dilutes it. The goal of **context engineering** is
therefore the smallest set of high-signal tokens that makes the desired outcome
likely. The post presents it as broader than prompt engineering, since an
agent's context includes system prompts, tools, examples, message history and
retrieved data, all of which compete for attention.

## Key points (as reported)

- **System prompts at the right altitude.** Specific enough to guide behaviour,
  but not brittle hard-coded logic or vague guidance. Start minimal and add
  instructions in response to observed failures.
- **Minimal, non-overlapping tools.** Bloated tool sets are a common failure
  mode, since they confuse the agent and consume context.
- **Just-in-time retrieval.** Keep lightweight references such as file paths,
  queries and links, and load data at runtime with tools (the post cites Claude
  Code using commands such as `head` and `tail`). This trades some speed for
  flexibility, and a hybrid of up-front and autonomous retrieval is often best.
- **Long-horizon techniques:** *compaction* (summarise a near-full window and
  continue from the summary; clearing old tool results is the lightest form),
  *structured note-taking* (persist notes outside the window, such as a to-do
  list or a notes file), and *sub-agents* (specialised agents work in clean
  contexts and return condensed summaries, reported as around 1,000–2,000 tokens).

## Cross-references

- Concept: [Context Engineering](../concepts/context-engineering.md).
- Related long-running work: [Effective Harnesses for Long-Running Agents](./anthropic-long-running-harnesses.md).
- Map: [Building Software with AI Agents](../pages/ai-agents-software-engineering.md).
