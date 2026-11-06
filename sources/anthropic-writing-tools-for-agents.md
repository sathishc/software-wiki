---
title: "Writing Effective Tools for AI Agents — Anthropic Engineering"
tags: [sources, ai-agents, api-design, testing]
source: https://www.anthropic.com/engineering/writing-tools-for-agents
ingested: 2026-11-06
---

# Writing Effective Tools for AI Agents — Source Notes

**Publisher:** Anthropic, Engineering blog

**Provenance note:** Checked against the full post, fetched in this session.
The namespacing guidance, the `response_format` option, and the 25,000 token cap
for Claude Code were confirmed in the text.

---

## Thesis

Tools are a contract between a deterministic system and a non-deterministic
reader, so they should be designed for the agent's way of working, not simply
wrapped around existing API endpoints. The post treats the tool interface as an
**agent-computer interface** that needs the same care as a human interface, and
it recommends measuring tool quality with evaluations rather than intuition.

## Key points (as reported)

- **Choose tools deliberately.** Build a few tools for high-impact workflows, and
  consolidate multi-step operations. Examples given: a `search_contacts` tool in
  place of a list call, or `schedule_event` in place of separate list and create
  calls. Overlapping tools distract the agent.
- **Namespace tools** by service and resource (e.g. `asana_search`, `jira_search`).
  Prefix versus suffix naming changes results, so test it.
- **Return meaningful context.** Prefer human-readable names over opaque
  identifiers, and offer a `response_format` option (concise or detailed) so the
  agent controls how much it receives.
- **Optimise for token efficiency.** Use pagination, filtering and truncation
  with sensible defaults. Claude Code is reported to cap tool responses at 25,000
  tokens. Error messages should say what to do next, not return opaque codes.
- **Prompt-engineer the descriptions.** Write them as if onboarding a new hire,
  name inputs unambiguously (`user_id`, not `user`), and enforce strict schemas.
  Small description changes were reported to have a large effect on SWE-bench
  Verified results.
- **Evaluate programmatically.** Run each evaluation task as an agent loop,
  record accuracy, runtime, tool-call counts, token use and errors, and read the
  transcripts to see where the agent gets confused.

## Cross-references

- Concept: [Agent Tool Design](../concepts/agent-tool-design.md).
- Related: [Agent Evals](../concepts/agent-evals.md), and the existing
  [API Design](../concepts/api-design.md) concept, which this post extends to an
  agent consumer.
