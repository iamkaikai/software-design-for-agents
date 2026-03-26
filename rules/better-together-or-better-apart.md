---
name: Better Together Or Better Apart
chapter: 9
tags: [modules, methods, decomposition]
---

## Principle

Split or join code based on overall complexity, not on a blanket preference for smaller pieces.

## Why It Matters

Every split creates new interfaces, more places to look, and more chances for duplicated knowledge. Every join risks mixing unrelated concerns. Good decomposition is about placing strongly related behavior together and separating what is truly independent.

## What It Simplifies

- It reduces conjoined modules and methods that only make sense when read side by side.
- It helps eliminate duplication by moving shared knowledge into one place.
- It keeps general-purpose mechanisms separate from special-purpose policy when that separation reduces leakage.

## Trade-offs and Boundaries

- Smaller is not automatically simpler. Short methods and extra classes can make a system harder to understand if they fragment one coherent operation.
- Larger is not automatically deeper. Joining unrelated concerns can create one big module with no clear abstraction.
- This rule shifts judgment from line count to relationship analysis: what knowledge is shared, what must change together, and what callers need to know.
- Ask for clarification when a proposed split or join is justified mostly by style preference, file size, or team convention rather than by information hiding and interface simplicity.

## When Context Changes the Answer

- Join code when it shares knowledge, must evolve together, or creates a simpler interface when combined.
- Split code when a general-purpose mechanism is being polluted by use-case-specific policy, or when a method is trying to serve unrelated caller needs.

## Red Flags

- Two methods can only be understood by flipping back and forth between them.
- A helper exists only for one caller and exposes the caller's local variables through a complex signature.
- A general mechanism carries specialized behavior for one workflow.
- Functions are split because they are "too long" even though the resulting pieces are tightly coupled.

## Examples

**Helpful:** Extracting a reusable undo history mechanism from text-editor-specific undo actions.

**Backfires:** Splitting one coherent parsing routine into many tiny helpers that all share the same transient state.
