---
name: Write Comments First
chapter: 15
tags: [comments, documentation, process]
---

## Principle

Write interface-level comments early enough that they help shape the design rather than merely describe it after the fact.

## Why It Matters

Trying to explain an interface in plain language exposes fuzzy boundaries, overloaded responsibilities, and missing invariants before implementation hardens them.

## What It Simplifies

- It turns documentation into a design probe instead of a cleanup task.
- It helps separate the intended abstraction from low-level implementation mechanics.
- It reveals when a function or module is trying to do too much.

## Trade-offs and Boundaries

- Early comments are sketches; they must be kept aligned with the implementation as the design evolves.
- Not every private helper needs full interface documentation before coding.
- The value comes from clarifying important boundaries, not from ritualistically writing comments for every trivial line of code.
- Clarify the semantics when you cannot write a short honest description of behavior without making unresolved choices.

## When Context Changes the Answer

- New modules, public APIs, and major refactors benefit most from early comment-driven design.
- Very small, local helpers may only need a quick mental contract or a brief inline note if their role is obvious.

## Red Flags

- Comments appear only after implementation and merely summarize what already exists.
- The interface description keeps changing because the abstraction is not stable.
- A function needs a paragraph to explain what should have been split into clearer concepts.
- Developers skip documentation because they do not yet understand the behavior themselves.

## Examples

**Helpful:** Drafting a class comment that states the abstraction and invariants before choosing the internal data structure.

**Backfires:** Writing elaborate early docs for a speculative subsystem whose purpose is still unknown.
