---
name: Consistency
chapter: 17
tags: [readability, conventions, maintenance]
---

## Principle

Consistency reduces cognitive load. When similar things are done in similar ways throughout a system, developers can understand new code faster by recognizing familiar patterns. Inconsistency forces readers to re-learn patterns for each new piece of code.

## Why It Matters

Consistency creates leverage: once you learn a convention, it applies everywhere. Inconsistency means every new file, function, or module is a learning experience. Over time, inconsistency compounds into significant confusion and wasted effort.

## How to Apply

- Follow existing patterns and conventions in the codebase, even if you'd personally prefer a different approach.
- Use the same name for the same concept everywhere. Don't call it `user` in one place and `account` in another if they mean the same thing.
- Structure similar modules similarly — if all controllers follow a pattern, new controllers should follow it too.
- When you establish a new pattern, document it so others follow it.
- If a convention is truly wrong, change it everywhere — don't create a second competing convention.

## Red Flags

- Two modules that solve similar problems in completely different ways.
- Variable names that change meaning across files (e.g., `id` means user ID in one file and order ID in another).
- Mixed formatting styles, error-handling approaches, or API patterns in the same codebase.
- "New style" code living alongside "old style" code indefinitely.

## Examples

**Bad:** Half the API endpoints return `{ data: ... }` and the other half return `{ result: ... }` — callers must check which format each endpoint uses.

**Good:** All API endpoints return `{ data: ... }` uniformly. A migration updates the old ones.
