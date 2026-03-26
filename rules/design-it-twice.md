---
name: Design It Twice
chapter: 11
tags: [design, process]
---

## Principle

Before committing to an important design choice, compare at least two plausible approaches.

## Why It Matters

The first idea is often shaped by habit, local context, or the current call site. Looking at alternatives makes trade-offs visible and forces you to articulate why one design is better.

## What It Simplifies

- It reduces accidental commitment to the first acceptable option.
- It reveals which complexity is inherent and which is introduced by the chosen design.
- It helps surface better abstractions, not just better implementations.

## Trade-offs and Boundaries

- You do not need a formal design exercise for every tiny helper. Apply this where the interface, decomposition, or long-term shape matters.
- The cost is more up-front thinking and occasional discarded sketches.
- The benefit comes from comparison, not from generating many options for its own sake.
- Clarify the priorities when a design choice has multiple plausible meanings or boundaries and the caller's actual priorities are not yet explicit.

## When Context Changes the Answer

- Shared modules, public interfaces, and structural refactors benefit most from explicit comparison.
- Tiny internal changes may only need a quick mental alternative rather than written design work.

## Red Flags

- "This is the obvious design" ends the discussion before trade-offs are stated.
- A design feels awkward but no one compared it to a different abstraction.
- Performance, simplicity, and extensibility pull in different directions and no one states the chosen priority.
- The team debates implementation details before agreeing on the interface.

## Examples

**Helpful:** Comparing range-based and line-based text APIs before implementing an editor core.

**Backfires:** Spending days comparing exotic alternatives for a simple private helper whose contract is already clear.
