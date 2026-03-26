---
name: Consistency
chapter: 17
tags: [readability, conventions, maintenance]
---

## Principle

Use the same patterns, names, and expectations for the same concepts so readers can reuse what they already know.

## Why It Matters

Consistency reduces the amount of new information a reader must learn. Once one instance is understood, similar cases become cheaper to understand and change.

## What It Simplifies

- It lowers cognitive load by letting readers rely on precedent.
- It makes review faster because deviations stand out.
- It reduces accidental variation in semantics, naming, and operational behavior.

## Trade-offs and Boundaries

- Consistency is a tool, not a reason to preserve a bad design forever.
- Blindly copying an existing pattern spreads defects just as efficiently as it spreads clarity.
- The simplification comes from reusing expectations; if the old expectation is wrong for the new problem, consistency may hide a needed distinction.
- Ask for clarification when matching an existing convention would preserve misleading semantics, the wrong abstraction, or an already harmful API shape.

## When Context Changes the Answer

- Prefer existing conventions when they are already clear and adequate.
- Break convention deliberately when the current pattern is materially wrong, but do it consistently and broadly enough that the system ends up clearer, not split between rival styles.

## Red Flags

- The same concept is represented with different names or return shapes.
- Similar operations have subtly different error or lifecycle semantics.
- "New style" and "old style" coexist indefinitely without a migration plan.
- Review feedback appeals to consistency even when the underlying design is flawed.

## Examples

**Helpful:** Making similar domain operations return the same status model and naming scheme.

**Backfires:** Preserving a bad getter/setter-heavy API just because "that is how the codebase does it."
