---
name: Different Layer, Different Abstraction
chapter: 7
tags: [abstraction, modules, layers]
---

## Principle

Adjacent layers should not expose the same idea in slightly different packaging. Each layer should change the abstraction, not merely relay it.

## Why It Matters

When layers have the same abstraction, you pay for extra boundaries without getting extra leverage. This creates pass-through methods, duplicated protocols, and more surface area to maintain.

## What It Simplifies

- It reduces shallow wrapper layers that add no new meaning.
- It makes system structure easier to reason about because each layer has a distinct role.
- It keeps callers from managing lower-level details that should have been transformed away.

## Trade-offs and Boundaries

- Some duplication across layers is acceptable when adapting an external interface, preserving stability, or enforcing policy.
- A wrapper can be worthwhile if it narrows an unstable dependency or creates a safer contract, even when much of the data still looks similar.
- The complexity can move into the adapting layer, which is fine if it genuinely protects callers.
- Clarify the boundary when a new layer mostly mirrors an existing API and the value of the extra boundary is not explicit.

## When Context Changes the Answer

- Anti-corruption layers around vendor APIs often keep a similar shape on purpose to isolate churn.
- Internal service or helper layers should usually justify themselves with a clearer abstraction, not just ownership boundaries.

## Red Flags

- Methods only rename or forward arguments.
- Several layers expose nearly identical request and response objects.
- The main reason a layer exists is "future flexibility" without a concrete interface benefit.
- Readers must inspect both layers together to understand one behavior.

## Examples

**Helpful:** A domain service that turns low-level storage records into business concepts.

**Backfires:** A service class that simply forwards repository methods under slightly different names.
