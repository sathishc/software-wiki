---
title: Long-Running Agents
tags: [ai-agents, context-engineering, delivery]
created: 2026-11-06
updated: 2026-11-06
sources: [sources/anthropic-long-running-harnesses.md, sources/anthropic-context-engineering.md, sources/stripe-minions-and-payment-method-factory.md]
layout: default
parent: Concepts
---

# Long-Running Agents

A **long-running agent** is one that works on a task across many sessions or
context windows, where no single session can hold the whole job. Each new session
starts without memory of the last, so the problem is continuity: how the work
carries forward without drifting or stopping early. Anthropic's post on effective
harnesses for long-running agents describes the failure modes and one approach to them.

## The two failure modes reported

The first is over-reach: the agent tries to build the whole system in one pass and
runs out of room partway. The second is premature completion: a later session looks
at the partly built result and declares the job finished. Both come from the agent
having no reliable picture of what is done and what remains.

## The approach (as reported)

An **initializer** session sets up the environment: a setup script, a progress log,
and an initial version-control commit. It also writes a structured feature list, with
every item marked as not yet passing. Later **coding** sessions each pick one
unfinished feature, make progress, and leave the code in a clean, mergeable state,
with a commit and a progress update. The post notes that the agent may only change
the status of a feature, which limits how much a model can quietly rewrite.

Each session begins by orienting itself: check the working directory, read the
history and progress file, pick the highest-priority unfinished item, and run a basic
end-to-end check before adding anything new. The starting check is what stops an
agent from building on broken ground.

## Connection to software delivery

This is familiar ground for anyone who has used [Continuous Integration & Continuous Delivery (CI/CD)](./ci-cd.md).
The rule "leave the main line green and mergeable" is a delivery discipline, and it is
what makes work safe to hand over between people or sessions. A progress log plays
the role of a good commit message, and a feature list is a backlog. The approach also
mirrors [Context Engineering](./context-engineering.md): state is kept outside the
window and loaded when needed.

## Open questions

The post asks whether a single general-purpose agent beats a team of specialised
agents for testing, QA and cleanup, and whether the approach generalises beyond web
applications. Treat it as a reported experiment, not settled practice, and measure
with [Agent Evals](./agent-evals.md). See the [map](../pages/ai-agents-software-engineering.md).
