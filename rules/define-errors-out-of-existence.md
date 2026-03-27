---
name: Define Errors Out of Existence
chapter: 10
tags: [complexity, error-handling, interfaces, structural-prevention]
---

## Principle

Where it is honest to do so, redefine operations so common "error" cases become part of normal semantics instead of spawning scattered exception-handling branches. Better still, make the error structurally impossible — through types, schemas, constraints, or state representations — so no caller can produce it in the first place.

This is the software equivalent of 防呆 (poka-yoke): instead of relying on every caller to handle errors correctly, redesign the interface or data model so the mistake cannot be expressed.

## Why It Matters

Exception-heavy APIs force every caller to understand and defend against many alternate flows. In many cases that complexity is more dangerous than the condition itself. Every guard clause is a place where someone can forget, get the order wrong, or silently swallow a real problem.

Structural prevention is stronger than semantic redefinition: a `CHECK` constraint or a type that cannot represent the invalid state needs zero discipline from callers — the system enforces correctness by construction.

## Three Levels of Prevention

1. **Structural (strongest):** Make the invalid state unrepresentable. Types, enums, `NOT NULL`, `CHECK` constraints, `UNIQUE` constraints. The error literally cannot exist.
2. **Semantic:** Redefine the operation so the "error" case is normal. `delete(id)` means "ensure absent." Callers stop caring whether the item existed.
3. **Procedural (weakest):** Document that callers must check preconditions. Every caller must remember. Someone will forget.

Prefer level 1 over 2, and level 2 over 3.

## What It Simplifies

- Replaces branch-heavy control-flow knowledge with simpler semantic knowledge (level 2) or no knowledge at all (level 1).
- Reduces duplicated caller-side checks such as "exists before delete" or "clip range before slice."
- Centers on postconditions instead of failure choreography.
- Eliminates special-case code paths. Represent "no selection" as an empty selection (start == end) rather than a nullable flag — copy and delete work naturally on empty selections without branches.

## Trade-offs and Boundaries

- The goal is not to remove understanding. The goal is to replace scattered exceptional-branch knowledge with simpler, more local, more predictable semantic knowledge.
- This only helps when the new semantics are natural, predictable, and easy for callers to carry in their heads.
- Important distinctions must stay visible. Do not hide failures, absences, or costs that callers need in order to behave correctly.
- Make common cases non-exceptional, but do not make important distinctions invisible.
- Ask for clarification when redefining behavior would collapse meanings such as missing vs empty, absent vs failed, retriable vs permanent, or idempotent vs duplicate-sensitive.

## When Context Changes the Answer

- Defining an error away works well when callers mostly care about the postcondition, such as "after this call, the item does not exist."
- Exposing the distinction is better when callers must react differently to the underlying causes, such as "not found" versus "backend unavailable."
- Structural prevention is almost always right for data integrity (schemas, types), but can be too rigid for evolving business rules where the "valid" set changes frequently.

## Red Flags

- Errors are silently swallowed with no way to distinguish real failure from benign absence.
- Callers now need tribal knowledge to predict what "success" means.
- The new semantics make observability or debugging materially worse.
- The interface returns empty values where the distinction between empty and missing is part of the business meaning.
- A nullable field or status string is used where an enum or constraint would prevent invalid states entirely.
- Guard clauses are scattered across multiple callers for a condition the data model could prevent once.

## Examples

### Structural Prevention (Level 1)

**Helpful:** A status column with `CHECK (status IN ('pending', 'processing', 'completed', 'failed'))` — invalid statuses cannot exist in the database. No caller needs to validate.

**Helpful:** `turn_index INTEGER NOT NULL DEFAULT 0 CHECK (turn_index >= 0)` — there is no "thread with unknown turn count" state to handle. The zero value is the initial state, not a special case.

**Helpful:** `UNIQUE(thread_id, turn_index)` — duplicate turns for the same index are impossible. No application-level dedup logic needed.

**Backfires:** An overly strict constraint on a field whose valid values change with business rules, forcing migrations for every policy change.

### Semantic Redefinition (Level 2)

**Helpful:** `delete(id)` means "ensure this item no longer exists," even if it was already absent.

**Helpful:** `ensureThread(workbenchId)` means "after this call, a thread exists for this workbench" — whether it was just created or already existed. Callers never handle "already exists."

**Helpful:** Cancelling a finished turn is a no-op. The postcondition "this turn will not produce more output" is already satisfied.

**Helpful:** Confirming an already-confirmed plan succeeds. The postcondition "this plan is confirmed" is already true.

**Backfires:** `readConfig()` treating an unreadable file the same as an intentionally empty configuration.

### Design Special Cases Out of Existence

**Helpful:** Represent "no selection" as an empty selection (start position == end position). Copy and delete operations work naturally on empty selections without conditional checks.

**Helpful:** A pagination cursor that decodes to `turnIndex: 0` when absent, so the query is always `WHERE turn_index > $cursor` — no "first page" special case.

**Backfires:** Treating "user has no preferences" the same as "user explicitly chose defaults" when the distinction affects downstream behavior.
