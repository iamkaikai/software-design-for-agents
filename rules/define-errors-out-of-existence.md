---
name: Define Errors Out of Existence
chapter: 10
tags: [complexity, error-handling, interfaces]
---

## Principle

The best way to deal with exception handling complexity is to define your APIs so that errors can't happen in the first place. Redefine semantics so that the "error" case is handled as part of normal operation.

## Why It Matters

Exception handling is one of the worst sources of complexity. Every exception introduces a code path that is hard to test and easy to get wrong. By redefining operations to absorb would-be error conditions, you eliminate entire categories of complexity.

## How to Apply

- Instead of throwing an error when a caller tries to delete something that doesn't exist, make the operation a no-op (idempotent).
- Instead of requiring callers to check a precondition before calling, handle the edge case inside the function.
- Use "define away" semantics: if a `substring(start, end)` receives out-of-range indices, clip them to the valid range rather than throwing.
- Reserve exceptions for truly exceptional conditions that the caller must know about and can't be handled internally.

## Red Flags

- APIs that throw exceptions for common, foreseeable situations.
- Callers that must call a `canDoX()` check before calling `doX()`.
- Try/catch blocks appearing around almost every call to a module.
- Error-handling code that is longer than the normal-path code.

## Examples

**Bad:** `array.get(index)` throws `IndexOutOfBoundsException` — every caller needs a bounds check or try/catch.

**Good:** `map.getOrDefault(key, fallback)` — the missing-key case is handled by returning the default, no exception needed.
