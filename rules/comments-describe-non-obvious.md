---
name: Comments Should Describe Things Not Obvious from Code
chapter: 13
tags: [comments, documentation, readability]
---

## Principle

Comments should carry information that code alone does not communicate clearly enough.

## Why It Matters

Code can show mechanics, but it often cannot fully express intent, rationale, assumptions, invariants, or surprising consequences. Good comments close that gap without duplicating what the reader can already see.

## What It Simplifies

- It reduces cognitive load by letting readers understand intent without reverse-engineering the implementation.
- It eliminates unknown unknowns by making hidden assumptions, invariants, and non-obvious consequences explicit — things readers would not know to look for.
- It lets readers rely on higher-level guidance instead of inferring intent from implementation detail.

## Trade-offs and Boundaries

- Comments are not a substitute for clear code. If a comment only explains a confusing implementation, the code may still need redesign.
- Comments add maintenance cost and can become noise when they restate visible behavior.
- The simplification comes from shifting some understanding into prose; that only works when the prose is accurate and selective.
- Clarify the contract when a comment is being used to justify surprising semantics, cross-module constraints, or temporary design debt that should instead be made explicit in code or interface contracts.

## When Context Changes the Answer

- Interface docs and rationale comments usually carry higher value than line-by-line narration.
- Dense logic, concurrency, protocol boundaries, and unusual invariants justify more commentary than straightforward data plumbing.

## Red Flags

- Comments merely translate code into English.
- Public interfaces have no explanation of behavior or assumptions.
- Important design decisions live only in commit history or chat.
- Comments explain "how" in great detail but omit "why this exists."

## Examples

**Helpful:** Explaining that a retry limit exists because the upstream service duplicates side effects after the fourth attempt.

**Backfires:** `// increment i` above `i++`.
