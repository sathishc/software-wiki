---
title: Agent Evals
tags: [ai-agents, evals, testing, quality]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/anthropic-demystifying-evals.md, sources/openai-practical-guide-building-agents.md, sources/anthropic-writing-tools-for-agents.md]
layout: default
parent: Concepts
---

# Agent Evals

An **eval** gives an AI system an input and grades its output. For AI agents, evals
play the role a test suite plays for ordinary software, with a crucial difference:
the agent is non-deterministic and takes many steps, so a single run proves little.
Anthropic's post on the topic treats evals as the main way a team learns whether a change helped, and OpenAI's guide recommends setting up evals to get a baseline before changing models.

## Vocabulary

A **task** is a test case, with an input and a definition of success. A **trial** is
one attempt at a task, repeated because outcomes vary. A **grader** scores the result.
The **transcript** is the full record of a trial, and the **outcome** is the final
state. The **evaluation harness** runs the tasks, which is separate from the
[agent harness](./agent-harness.md) under test.

## Two kinds of eval

Capability evals start with a low pass rate, which gives the team a target to
improve. Regression evals should sit close to 100%, and they guard against
backsliding. When a capability eval reaches a high pass rate it can be promoted
into the regression suite. This split maps onto the familiar idea of
[Test-Driven Development (TDD)](./tdd.md): capability work is a red test being made
green, and regression is the suite that stays green.

## Building trustworthy evals

Start with 20–50 tasks drawn from real failures. Tasks must be unambiguous and have
reference solutions. A 0% pass rate across many trials usually means the task is
broken, not that the agent is incapable. Isolate every trial so that no state leaks
between runs. Prefer deterministic graders; where an LLM grades, calibrate it against
human judgement and allow an "unknown" answer. Grade outcomes rather than exact tool-call
paths, and read the transcripts before trusting a score. These points echo
[Unit Testing](./unit-testing.md) and [Test Pyramid](./test-pyramid.md) advice about
isolation, determinism and the value of fast, reliable feedback.

## Connection to delivery

Evals are the agent equivalent of the automated checks in [Continuous Integration & Continuous Delivery (CI/CD)](./ci-cd.md).
Stripe's observer agent and sandbox tests (see [the Stripe source](../sources/stripe-minions-and-payment-method-factory.md))
are a form of this. The discipline matches the wiki's theme of making feedback fast and reliable, as in [Observability](./observability.md).

See the [map](../pages/ai-agents-software-engineering.md) for how evals fit the wider approach.
