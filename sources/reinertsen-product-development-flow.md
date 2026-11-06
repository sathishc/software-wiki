---
title: "The Principles of Product Development Flow — Donald G. Reinertsen (2009)"
tags: [sources, lean, flow, economics, queueing, cost-of-delay, batch-size, wip, donald-reinertsen]
source: "Book (Celeritas Publishing, 2009); secondary summaries consulted 2026-11-06"
ingested: 2026-11-06
---

# The Principles of Product Development Flow — Source Notes

**Book:** The Principles of Product Development Flow: Second Generation Lean Product Development (Celeritas Publishing, 2009)
**Author:** Donald G. Reinertsen

**Provenance note:** These notes were compiled from secondary summaries and
a web search on 2026-11-06, not from a close reading of the book. Principle
codes (E3, F16, B1, W1, and so on) are as reported by those summaries and
should be checked against the book (the principle list is on pp. 271–276)
before anyone quotes them in external material.

---

## Thesis

Reinertsen argues that most product development organisations manage the
wrong thing. They optimise **utilisation, cost per unit of effort, and
schedule adherence**, when the economically relevant variable is **the
flow of value** through the development process. The book is a catalogue of
roughly 175 principles, grouped into eight areas, that explain how flow
behaves and how to manage it. Reinertsen calls this the "second generation"
of lean product development: first-generation lean (Toyota Production
System) was about manufacturing; this is about the uncertainty and
information-heavy nature of design work.

## Principle areas (as reported)

- **Economics** — decisions should be driven by economic value, and the
  central quantity is the [Cost of Delay](../concepts/cost-of-delay.md).
- **Queues** — work waits in queues, and the queue, not the worker, is where
  most of the economic damage happens. See [Queueing & Utilization](../concepts/queueing-and-utilization.md).
- **Variability** — variability is not always bad; it can be exploited, but
  it must be managed where it accumulates in queues.
- **Batch size** — smaller batches reduce cycle time, variability, and risk.
  See [Batch Size](../concepts/batch-size.md).
- **WIP constraints** — limiting work in progress controls cycle time and
  forces rate-matching. See [Work-in-Progress Limits](../concepts/wip-limits.md).
- **Cadence, synchronisation, and flow control** — regular rhythms make
  coordination cheaper than ad-hoc handoffs.
- **Fast feedback** — the cost of getting feedback falls as its latency falls.
- **Decentralised control** — local, information-rich decisions beat central
  control when information is the bottleneck.

## Notable principles cited in summaries

- **Quantify the cost of delay** — "If you only quantify one thing, quantify
  the cost of delay" (reported as E3).
- **Sequence by weighted shortest job first (WSJF)** — when durations and
  delay costs differ, order work by cost of delay divided by duration
  (reported as F16–F17).
- **Reducing batch size reduces cycle time and variability** (reported as B1–B2).
- **Constrain WIP to control cycle time** (reported as W1), and use WIP
  ranges to decouple adjacent processes' batch sizes (reported as W5).
- **Little's Law** is used as the basic relation between WIP, throughput, and
  cycle time. See [Little's Law](../concepts/littles-law.md).

## Cross-references

- Synthesised into the [Lean Product Development](../pages/lean-product-development.md) map.
- Author page: [Donald G. Reinertsen](../people/donald-reinertsen.md).
- Related existing material: [DORA Metrics](../concepts/dora-metrics.md) and
  [Continuous Integration & Continuous Delivery (CI/CD)](../concepts/ci-cd.md)
  (the software-delivery version of small batches and fast feedback), and
  [Delivery](../pages/delivery.md).
