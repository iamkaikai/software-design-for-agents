---
name: Designing for Performance
chapter: 20
tags: [performance, complexity, measurement]
---

## Principle

Optimize for performance in ways that preserve simplicity when possible, and use measurement to justify complexity when it is not.

## Why It Matters

Ignoring performance entirely can produce death by a thousand cuts. Chasing speed everywhere can produce a brittle, overcomplicated system. Good performance design chooses the few places where complexity is worth paying.

## What It Simplifies

- It replaces intuition-driven tweaking with measurement-driven decisions.
- It encourages naturally efficient designs that are both simple and fast.
- It focuses optimization on critical paths instead of spreading low-value complexity everywhere.

## Trade-offs and Boundaries

- Performance work often moves complexity into representation, caching, batching, or specialized fast paths. Keep that cost local and justified.
- Faster is not automatically better if the gain is marginal and the new design becomes harder to maintain.
- Some systems have hard latency or throughput requirements that justify extra complexity up front; others should optimize later and only where data demands it.
- Ask for clarification when a proposed optimization changes semantics, observability, memory use, operational risk, or interface behavior without a measured performance target.

## When Context Changes the Answer

- Start with simple, naturally efficient structures when they already meet likely needs.
- Use stronger optimization tactics only after measuring or when the requirement is explicit and non-negotiable.

## Red Flags

- Optimizations are justified by gut feeling rather than benchmarks or traces.
- Complexity is added for performance, but no one checks whether the change moved a meaningful metric.
- Many small inefficiencies accumulate because performance was never considered at all.
- The critical path is cluttered with special-case logic that could be moved aside.

## Examples

**Helpful:** Measuring a hot path, then redesigning it so the common case avoids extra calls and checks.

**Backfires:** Adding a cache with invalidation complexity before confirming the data access path is even a bottleneck.
