---
name: Design It Twice
chapter: 11
tags: [design, process]
---

## Principle

Before committing to a design, consider at least two different approaches. Compare them against each other. The first idea is rarely the best, and comparing alternatives surfaces trade-offs you wouldn't otherwise see.

## Why It Matters

Developers tend to latch onto the first design that comes to mind and implement it immediately. But the first design is often shaped by mental inertia rather than careful analysis. Considering a second design forces you to articulate why one approach is better, leading to stronger decisions.

## How to Apply

- When starting a new module, class, or significant function, sketch at least two different interface designs before writing code.
- Compare alternatives on: simplicity of interface, flexibility, performance, and how well they hide information.
- Even if you end up choosing the first design, the exercise of comparison strengthens your confidence.
- This applies at all scales: function signatures, class hierarchies, system architecture.

## Red Flags

- Jumping straight to implementation without considering alternatives.
- "This is the obvious way to do it" — the obvious way is not always the best.
- A design that feels forced or awkward, but is pursued because it was the first one considered.
- Difficulty explaining why the chosen approach is better than alternatives.

## Examples

**Bad:** Immediately implementing a tree structure because the data is hierarchical, without considering whether a flat list with parent references might be simpler for the actual use cases.

**Good:** Sketching both a tree and a flat-list approach, comparing how each handles the three most common operations, then choosing based on actual trade-offs.
