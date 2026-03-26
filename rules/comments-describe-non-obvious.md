---
name: Comments Should Describe Things Not Obvious from Code
chapter: 13
tags: [comments, documentation, readability]
---

## Principle

Comments should provide information that is not obvious from reading the code. They should describe *why*, not *what*. If a comment repeats what the code already says, it adds clutter, not value.

## Why It Matters

Good comments capture information that exists in the developer's mind but cannot be expressed in the code itself: the reasoning behind a decision, the higher-level intent, non-obvious constraints, or subtle edge cases. Without these comments, future readers must reverse-engineer the intent.

## How to Apply

- Write comments that describe **why** something is done, not **what** the code does.
- Document non-obvious side effects, constraints, or assumptions.
- Use interface comments (on functions, classes, modules) to describe the abstraction — what the caller needs to know, not how it's implemented.
- Avoid comments that repeat the code: `i += 1  // increment i` adds nothing.
- If you find yourself writing a comment to explain confusing code, consider rewriting the code to be clearer instead.

## Red Flags

- Comments that restate the code in English.
- No comments at all on public interfaces.
- Comments that describe implementation details in an interface-level docstring.
- Stale comments that no longer match the code.

## Examples

**Bad:** `// Set the retry count to 3` above `retryCount = 3`.

**Good:** `// Retry up to 3 times because the payment gateway occasionally returns transient 503s during settlement windows` above `retryCount = 3`.
