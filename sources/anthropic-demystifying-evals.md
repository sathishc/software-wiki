---
title: "Demystifying Evals for AI Agents — Anthropic Engineering"
tags: [sources, ai-agents, evals, testing]
source: https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents
ingested: 2026-11-06
---

# Demystifying Evals for AI Agents — Source Notes

**Publisher:** Anthropic, Engineering blog

**Provenance note:** Checked against the full post, fetched in this session.
The 20–50 starting tasks, the near-100% regression target, the 0% pass rate as a
broken-task signal, and the git-history example were confirmed in the text.

---

## Thesis

An **eval** gives an AI an input and grades its output. For agents, evals are
the equivalent of a test suite, and they are harder to write, because agents
take many steps, use tools and change their environment. The post offers a
vocabulary and practical guidance for building evals that are trustworthy
enough to guide decisions.

## Vocabulary (as reported)

A **task** is one test case with an input and a success definition. A **trial**
is one attempt at a task, repeated because agents are non-deterministic. A
**grader** scores the outcome. The **transcript** is the full record of the
trial. The **outcome** is the final state of the environment. The **evaluation
harness** runs the tasks, and the **agent harness** runs the agent. An
**evaluation suite** groups tasks for one capability.

## Key points (as reported)

- **Two kinds of eval.** Capability evals start at a low pass rate to give the
  team a hill to climb. Regression evals should sit near 100% and catch
  backsliding. A capability eval that reaches a high pass rate can graduate into
  the regression suite.
- **Start small.** Around 20–50 simple tasks drawn from real failures is a
  reasonable start.
- **Tasks must be unambiguous,** with reference solutions. A 0% pass rate across
  many trials usually indicates a broken task rather than an incapable agent.
- **Isolate every trial.** Each run should start from a clean environment. The
  post cites a case where an agent gained an unfair advantage by reading git
  history left by earlier trials.
- **Graders.** Prefer deterministic graders. Where an LLM grader is needed,
  calibrate it against human experts and give it an "unknown" option. Grade
  outcomes rather than the exact path of tool calls, and allow partial credit.
- **Read the transcripts.** Do not trust a score until someone has checked what
  the agent actually did.

## Cross-references

- Concept: [Agent Evals](../concepts/agent-evals.md), built on
  [Test Pyramid](../concepts/test-pyramid.md) and [Unit Testing](../concepts/unit-testing.md)
  ideas about isolation and determinism.
- Related: [Agent Harness](../concepts/agent-harness.md).
