---
name: Code Should Be Obvious
chapter: 18
tags: [readability, complexity]
---

## Principle

Code is obvious if a reader can understand it quickly without much thought. If code requires careful study or external knowledge to understand, it is not obvious — and it will be a source of bugs and slow development.

## Why It Matters

Developers spend far more time reading code than writing it. Obvious code is faster to understand, faster to review, and less likely to harbor hidden bugs. Non-obvious code forces every future reader to spend time deciphering what the original author intended.

## How to Apply

- Use clear, descriptive names that eliminate the need for mental mapping.
- Structure code so the flow of execution is easy to follow.
- Avoid clever tricks, unusual language features, or subtle side effects.
- When a piece of code is not obvious, consider rewriting it before adding a comment.
- Use whitespace and grouping to visually reflect the logical structure.
- Limit the number of things a reader needs to hold in their head at any one time.

## Red Flags

- Code that requires reading the implementation of called functions to understand the caller.
- Clever one-liners that pack multiple operations together.
- Variables whose type or purpose is unclear from context.
- Event-driven or callback-based code where the execution order is hard to follow.
- Generic container types (e.g., `Pair<String, List<Integer>>`) where the meaning of each element is unclear.

## Examples

**Bad:** `return x ? a || (b && !c) : d ?? e;` — technically correct but requires careful parsing.

**Good:** Extracting the condition into a well-named boolean variable, then using a simple if/else.
