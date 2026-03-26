---
name: Modifying Existing Code
chapter: 16
tags: [maintenance, complexity, design]
---

## Principle

When changing existing code, make the change fit the design cleanly or improve the design enough that it can.

## Why It Matters

Most software work happens in existing systems. If each change only patches the immediate need, design quality steadily erodes and later work becomes slower and riskier.

## What It Simplifies

- It reduces long-term fragility by preventing local hacks from becoming permanent structure.
- It turns maintenance into gradual repair instead of gradual decay.
- It lowers future change cost by keeping abstractions aligned with current reality.

## Trade-offs and Boundaries

- Not every modification warrants a large refactor. The right move is the smallest design improvement that keeps the new change honest.
- Cleaning up one area can expose more debt than fits the current change budget; choose leverage, not perfectionism.
- This rule moves some effort from feature delivery into structural maintenance, which is worthwhile only when it genuinely lowers future cost.
- Ask for clarification when a requested patch clearly conflicts with the existing design and the expected scope of cleanup is materially larger than the stated change.

## When Context Changes the Answer

- Shared or frequently modified code deserves more cleanup investment than isolated dead-end code.
- Bug fixes should usually leave the surrounding code simpler, but emergency operational fixes may need a follow-up cleanup instead of immediate refactoring.

## Red Flags

- The change is technically correct but adds new branches in several unrelated files.
- The same module keeps accumulating one-off cases for new requests.
- Developers are afraid to touch a file and instead add wrappers around it.
- Comment updates are skipped because the design no longer matches the code.

## Examples

**Helpful:** Refactoring a branching serializer into a strategy-based boundary before adding a new format.

**Backfires:** Turning a one-line urgent fix into a multi-day redesign of unrelated parts of the system.
