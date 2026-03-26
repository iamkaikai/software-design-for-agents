---
name: Mistaking Distribution for Clean Separation
chapter: external
tags: [architecture, distributed-systems, tradeoffs]
---

## Principle

Cross-process and cross-service boundaries are not a cleanliness upgrade by themselves. They are a costly trade that only helps when they solve a problem large enough to justify the premium.

## Common Mistake

Treating distribution as a natural way to make a system cleaner, more scalable, or more "real" before the benefits are explicit.

## Why It Is Tempting

- Separate processes and services look like sharp boundaries.
- Distribution promises team autonomy, independent deploys, and scaling flexibility.
- Architecture literature and platform tooling often make splitting look like maturity.

## What Goes Wrong

- Network calls add latency, partial failure, timeouts, retries, and observability burden.
- Data consistency and debugging get harder just as domain understanding is still immature.
- Teams discover that the "independent" services still need shared deploys, shared schema changes, or constant coordination.

## Better Decision Pattern

- Start by naming the pressure that distribution is supposed to relieve: scaling, isolation, ownership, regulatory boundaries, fault containment, or technology divergence.
- Compare that benefit to the distributed-systems cost you are about to buy.
- Prefer simpler in-process boundaries first unless the external boundary clearly pays for itself.

## Trade-offs and Boundaries

- This rule does not mean "always build a monolith."
- Some systems genuinely need hard isolation, independent failure domains, or very different scaling characteristics early.
- The point is to make distribution earn its cost rather than smuggling in that cost under the banner of cleanliness.

## Ask for Clarification When

- A proposed split is justified with vague language like "more scalable" or "more modern" without a concrete pressure.
- The teams still need shared schema changes, lockstep deploys, or frequent synchronous coordination.
- The service boundary is being chosen before the domain boundary is clear.

## Red Flags

- A new service mostly forwards calls to another service.
- Independent deployment is claimed, but routine changes still require coordinated releases.
- One business workflow now spans many hops without an equally strong business reason.

## Examples

**Failure pattern:** Splitting a new product into many services before its workflows stabilize, then paying retry, schema, and deployment complexity on day one.

**Counterexample:** Introducing a hard service boundary when a security or compliance requirement genuinely demands isolated ownership and deployment.
