---
name: Write Comments First
chapter: 15
tags: [comments, documentation, process]
---

## Principle

Write the comments for a module or function before writing the code. Describe the interface, the abstraction, and the key design decisions in comments first, then implement.

## Why It Matters

Writing comments first forces you to think about the design before you write the implementation. It reveals vague thinking and poor abstractions early, when they're cheap to fix. If you can't write a clear comment describing what a function does, the design probably needs work.

## How to Apply

- Before implementing a function, write the docstring/header comment describing what it does, its parameters, return value, and side effects.
- Before implementing a class, write the class-level comment describing the abstraction it provides.
- Use the comments as a design tool: if the comment is awkward, the interface is probably awkward.
- Update comments during implementation if the design changes — but don't skip writing them first.

## Red Flags

- Functions with no documentation where the author says "I'll add comments later."
- Comments that were clearly written after the fact and just describe the implementation.
- Difficulty articulating what a function does in one or two sentences — a sign the function does too much.

## Examples

**Bad:** Writing a 200-line function first, then struggling to write a comment that explains it.

**Good:** Writing `/// Merges two sorted arrays into a single sorted array. Assumes both inputs are sorted in ascending order. Returns a new array without modifying the inputs.` — then implementing the merge.
