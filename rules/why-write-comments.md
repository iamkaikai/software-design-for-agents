---
name: Why Write Comments
chapter: 12
tags: [comments, documentation, abstractions]
---

## Principle

Write comments because code cannot carry all of the design knowledge that future readers need.

## Why It Matters

Good abstractions depend on more than signatures and control flow. Without comments, callers often have to inspect implementation details to reconstruct behavior, rationale, and safe usage.

## What It Simplifies

- It reduces unknown unknowns by stating what matters about a module or interface.
- It lowers cognitive load because readers do not need to infer everything from code alone.
- It completes abstractions by capturing the parts of a contract that code cannot express well.

## Trade-offs and Boundaries

- Comments cost time to write and maintain, so they must carry information that readers cannot cheaply recover elsewhere.
- Commenting everything creates noise; commenting nothing pushes design knowledge into guesswork and archaeology.
- The understanding moves from private author knowledge into shared documentation, which only helps if the comments stay near the code and stay current.
- Ask for clarification when the behavior, rationale, or boundary of an interface cannot be expressed clearly enough in code and the intended contract is still unresolved.

## When Context Changes the Answer

- Public APIs, non-obvious invariants, tricky concurrency, protocol boundaries, and unusual failure semantics deserve explicit documentation.
- Straightforward local code with precise names may need little or no commentary beyond nearby interface docs.

## Red Flags

- Developers claim the code is self-documenting while readers still must inspect implementation to use it safely.
- Important rationale exists only in chat, tickets, or oral history.
- Comments are postponed indefinitely because "there is no time."
- Comments are distrusted because most existing ones are stale or content-free.

## Examples

**Helpful:** A class comment that states the abstraction, invariants, and caller-visible guarantees.

**Backfires:** Mandating comments on every trivial statement until useful documentation is buried in noise.
