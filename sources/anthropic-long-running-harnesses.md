---
title: "Effective Harnesses for Long-Running Agents — Anthropic Engineering"
tags: [sources, ai-agents, context-engineering, delivery]
source: https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents
ingested: 2026-11-06
---

# Effective Harnesses for Long-Running Agents — Source Notes

**Publisher:** Anthropic, Engineering blog

**Provenance note:** Checked against the full post, fetched in this session. The
initializer and coding agent roles and the progress-file approach were confirmed
in the text. The related post "Harness design for long-running apps" was
mentioned but not read.

---

## Problem

Each new agent session starts with no memory of the previous one. When a task
spans many context windows, the agent drifts. Two failure modes were reported:
the agent tries to build the whole application in one pass, and a later session
declares the job finished too early.

## Approach (as reported)

- **Initializer agent.** The first session sets up the environment. It writes an
  `init.sh` script, a progress log file, and an initial git commit.
- **Coding agent.** Each later session makes incremental progress on one feature,
  then leaves the code in a clean, mergeable state with descriptive commits and a
  progress update.
- **Feature list.** The initializer writes a structured list of features, all
  marked as failing (over 200 in the web-app example). Coding agents may only flip
  the `passes` field. The post reports that models edit JSON more carefully than
  Markdown.
- **Getting up to speed.** Each session checks its working directory, reads the
  git log and progress file, picks the highest-priority unfinished feature, and
  runs a basic end-to-end check before starting new work.
- **End-to-end testing** with browser automation made a large difference. Limits
  remain; for example, the agent could not see native browser alert dialogs.

## Open questions (as reported)

Whether one general-purpose agent outperforms a multi-agent setup with testing,
QA or cleanup agents, and whether the approach generalises beyond web-app
development.

## Cross-references

- Concepts: [Long-Running Agents](../concepts/long-running-agents.md) and
  [Context Engineering](../concepts/context-engineering.md).
- Related: [Context Engineering post](./anthropic-context-engineering.md),
  [Continuous Integration & Continuous Delivery (CI/CD)](../concepts/ci-cd.md),
  since the "always leave a clean, mergeable state" rule is a delivery discipline.
