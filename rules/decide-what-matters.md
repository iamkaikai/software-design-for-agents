---
name: Decide What Matters
chapter: 21
tags: [prioritization, abstraction, design]
---

## Principle

Structure the design around the distinctions, guarantees, and constraints that matter most, and minimize the impact of everything else.

## Why It Matters

Many design mistakes come from treating too many things as important or hiding something that actually matters. Good design depends on knowing what deserves prominence, centrality, and repetition.

## What It Simplifies

- It reduces clutter by shrinking the set of things that shape the interface and structure.
- It helps decide what to hide, what to expose, and what to optimize.
- It turns the other rules into context-sensitive heuristics rather than slogans.

## Trade-offs and Boundaries

- Deciding what matters is itself a design judgment, and it can be wrong. The answer often becomes clearer only after comparing options or seeing real usage.
- Over-emphasizing too many concerns bloats the design; under-emphasizing a truly important concern creates dangerous blind spots.
- This rule does not eliminate trade-offs. It helps choose which trade-offs should dominate the design.
- Ask for clarification when you cannot tell whether a distinction should be hidden or exposed because its importance to callers, operators, or the business is still ambiguous.

## When Context Changes the Answer

- In one system, throughput may be central; in another, auditability or semantic clarity may dominate.
- A detail that does not matter to most callers may still matter deeply to operators, integrators, or downstream systems.

## Red Flags

- Rare edge cases or implementation details dominate the public API.
- Important guarantees are buried while irrelevant options are prominent.
- The system exposes many knobs because no one decided which concerns deserve defaults.
- Teams argue about style while core semantic distinctions remain vague.

## Examples

**Helpful:** Centering a queue API around delivery guarantees because that is what callers truly need to reason about.

**Backfires:** Hiding consistency level, latency class, or failure visibility when those differences are actually central to correct use.
