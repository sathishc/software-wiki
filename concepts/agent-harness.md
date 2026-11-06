---
title: Agent Harness
tags: [ai-agents, architecture, evals, testing]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/anthropic-demystifying-evals.md, sources/stripe-minions-and-payment-method-factory.md, sources/anthropic-long-running-harnesses.md]
layout: default
parent: Concepts
---

# Agent Harness

The **agent harness** is the code around the model that runs the agent: it sends
the context to the model, parses the model's tool calls, executes them, feeds the
results back, and decides when to stop. The model supplies judgement; the harness
supplies everything else. Anthropic's evals post uses the term to separate the
agent under test from the **evaluation harness**, which runs tasks and records
results.

## What a harness does

A harness typically manages the message history, enforces limits such as step or
cost budgets, sandboxes tool execution, and handles errors and retries. For
long-running work it also manages state between sessions, as described in
[Long-Running Agents](./long-running-agents.md). Much of the reliability of an
agent comes from its harness, not from the model alone. Stripe's reusable prompts
and observer agent are a form of harness engineering: structure placed around the
model so its output is more consistent.

## Why it matters for testing

Because the harness controls the environment, it determines whether an evaluation
is fair. The Anthropic post reports that each trial should start from a clean,
isolated state, since an agent that can read history from earlier trials can gain
an unfair advantage. The same principle of isolation that makes
[Unit Testing](./unit-testing.md) reliable applies here. See [Agent Evals](./agent-evals.md).

## Design choices

Keep the harness simple enough to debug. A thin loop that exposes the model's
steps is easier to diagnose than a deep framework that hides prompts, which is the
point Anthropic makes about frameworks. Put limits in the harness rather than
trusting the model to stop: a maximum number of steps, a token budget, and a
timeout are cheap insurance.

## Related

The harness is where [Ports and Adapters](./ports-and-adapters.md)-style boundaries
help most, since the model, tools and environment can each be swapped for a fake
in tests. See also [Context Engineering](./context-engineering.md) and the
[map](../pages/ai-agents-software-engineering.md).
