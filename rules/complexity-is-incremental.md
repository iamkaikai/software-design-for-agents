---
name: Complexity Is Incremental
chapter: 2
tags: [complexity, fundamentals]
---

## Principle

Complexity rarely arrives as one dramatic mistake. It accumulates through small decisions that each seem affordable in isolation.

## Why It Matters

If you only react to obvious disasters, you will miss the steady drift that makes systems expensive to change. Complexity compounds through added branches, flags, exceptions, and one-off accommodations.

## What It Simplifies

- It trains you to evaluate each local decision by its effect on the whole system.
- It replaces "this one extra case is harmless" with "what pattern does this create if repeated?"
- It makes design debt visible earlier, when it is still cheap to correct.

## Trade-offs and Boundaries

- This rule does not mean every increase in complexity is avoidable. Some complexity is required by the problem itself.
- The goal is to reject unnecessary complexity, not to freeze the design or refuse hard requirements.
- Applying the rule well requires judgment about whether a change is a one-time cost with clear leverage or the start of a new burden.
- Clarify the trade-off when a "small" requested change introduces a new concept, mode, state, or semantic exception that may spread.

## When Context Changes the Answer

- A small local complication can be worth it when it buys strong simplification elsewhere, such as isolating an ugly integration detail in one place.
- A one-off special case is less dangerous when it is fully contained, named clearly, and prevented from leaking into other interfaces.

## Red Flags

- "Just this once" appears often in reviews or commit messages.
- New boolean flags or optional parameters accumulate in stable APIs.
- Similar edge-case checks appear in multiple callers.
- A simple change now requires remembering several historical exceptions.

## Examples

**Helpful:** Rejecting a new mode flag on a shared function and creating a clearer abstraction instead.

**Backfires:** Refusing any added complexity even when the domain genuinely has another required state that must be modeled explicitly.
