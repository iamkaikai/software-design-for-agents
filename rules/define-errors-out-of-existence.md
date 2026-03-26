---
name: Define Errors Out of Existence
chapter: 10
tags: [complexity, error-handling, interfaces]
---

## Principle

Where it is honest to do so, redefine operations so common "error" cases become part of normal semantics instead of spawning scattered exception-handling branches.

## Why It Matters

Exception-heavy APIs force every caller to understand and defend against many alternate flows. In many cases that complexity is more dangerous than the condition itself.

## What It Simplifies

- It replaces branch-heavy control-flow knowledge with simpler semantic knowledge.
- It reduces duplicated caller-side checks such as "exists before delete" or "clip range before slice."
- It makes common operations easier to reason about by centering on postconditions instead of failure choreography.

## Trade-offs and Boundaries

- The goal is not to remove understanding. The goal is to replace scattered exceptional-branch knowledge with simpler, more local, more predictable semantic knowledge.
- This only helps when the new semantics are natural, predictable, and easy for callers to carry in their heads.
- Important distinctions must stay visible. Do not hide failures, absences, or costs that callers need in order to behave correctly.
- Make common cases non-exceptional, but do not make important distinctions invisible.
- Ask for clarification when redefining behavior would collapse meanings such as missing vs empty, absent vs failed, retriable vs permanent, or idempotent vs duplicate-sensitive.

## When Context Changes the Answer

- Defining an error away works well when callers mostly care about the postcondition, such as "after this call, the item does not exist."
- Exposing the distinction is better when callers must react differently to the underlying causes, such as "not found" versus "backend unavailable."

## Red Flags

- Errors are silently swallowed with no way to distinguish real failure from benign absence.
- Callers now need tribal knowledge to predict what "success" means.
- The new semantics make observability or debugging materially worse.
- The interface returns empty values where the distinction between empty and missing is part of the business meaning.

## Examples

**Helpful:** `delete(id)` means "ensure this item no longer exists," even if it was already absent.

**Backfires:** `readConfig()` treating an unreadable file the same as an intentionally empty configuration.
