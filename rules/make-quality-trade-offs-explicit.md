---
name: Mistaking "Better Architecture" for a Shared Priority
chapter: external
tags: [architecture, quality-attributes, tradeoffs]
---

## Principle

Architectural decisions are usually choices among competing quality attributes, not universal improvements.

## Common Mistake

Saying a design is "better" without stating better for what.

## Why It Is Tempting

- Broad words like "scalable," "robust," and "enterprise-ready" sound persuasive.
- Teams often assume everyone values the same quality attributes in the same order.
- It is easier to argue from taste than to state which trade-off is being chosen.

## What Goes Wrong

- One group optimizes for throughput while another assumed modifiability mattered most.
- A design improves one attribute and quietly harms another.
- Architecture debates become circular because participants are solving different problems.

## Better Decision Pattern

- Name the quality attributes in play: modifiability, performance, reliability, security, operability, cost, latency, and so on.
- State which ones this decision is optimizing and which ones it is willing to make worse.
- Review the result against those declared priorities instead of against vague elegance.

## Trade-offs and Boundaries

- Not every local coding choice needs a formal quality-attribute exercise.
- The point is to make consequential trade-offs explicit, not to produce ritual documents.
- Naming the trade-off does not remove disagreement, but it makes disagreement honest.

## Ask for Clarification When

- A decision is sold as "good architecture" without naming the quality attribute it serves.
- Different reviewers appear to be arguing from different success criteria.
- A large structural choice is being made while its operational or business priorities remain unstated.

## Red Flags

- Performance wins are announced without discussing operability or change cost.
- Modularity wins are announced without discussing latency or consistency.
- Teams discover after rollout that they were optimizing for different outcomes.

## Examples

**Failure pattern:** Adopting an eventually consistent design because it feels scalable, then discovering the workflow required immediate correctness guarantees.

**Counterexample:** Explicitly choosing slower writes because auditability and correctness outrank throughput for that subsystem.
