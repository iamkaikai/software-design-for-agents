---
name: Mistaking the Written Contract for the Real Interface
chapter: external
tags: [architecture, APIs, compatibility]
---

## Principle

Consumers depend on stable observable behavior, not only on what the formal contract says.

## Common Mistake

Assuming undocumented behavior is safe to change because it was never explicitly promised.

## Why It Is Tempting

- The written API contract feels like the complete definition of compatibility.
- Teams want freedom to change internals without treating every observable detail as a migration problem.
- It is uncomfortable to admit that consumers rely on behaviors you never intended to support.

## What Goes Wrong

- Ordering, timing, defaults, null-handling, pagination shape, or response quirks become hidden dependencies.
- Changes that look internal on paper break downstream systems in production.
- Teams dismiss the breakage with "that was never part of the contract," which does not help the dependents who were relying on it.

## Better Decision Pattern

- Distinguish between accidental behavior you should fix deliberately and stable observable behavior you should treat as compatibility surface.
- Assume widely used systems have a larger real interface than their docs alone suggest.
- Plan migrations with real consumer behavior in mind, not only the spec.

## Trade-offs and Boundaries

- You should not freeze every bug forever.
- The challenge is to decide which observable behaviors have become meaningful enough that changing them now carries compatibility cost.
- This rule widens your sense of interface reality; it does not require surrendering all architectural freedom.

## Boundary Questions

- Does this change touch long-stable ordering, defaults, timing profile, or result shape that consumers may have quietly depended on?
- Does the system have enough users that real usage patterns matter more than the written spec alone?
- Is "undocumented" being used as a substitute for compatibility analysis?

## Red Flags

- A rollout breaks consumers even though the schema did not change.
- The only interface analysis done is schema-level.
- Teams keep discovering hidden dependencies after deployment instead of before.

## Examples

**Failure pattern:** Changing response ordering because it was never specified, then breaking consumers that were depending on it for deterministic processing.

**Counterexample:** Intentionally removing a harmful quirk, but doing so as a real compatibility change with migration support.
