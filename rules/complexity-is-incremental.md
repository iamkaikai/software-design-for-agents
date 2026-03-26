---
name: Complexity Is Incremental
chapter: 2
tags: [complexity, fundamentals]
---

## Principle

Complexity isn't caused by a single catastrophic decision. It accumulates in small increments — a special case here, an extra parameter there, a workaround somewhere else. Each one seems harmless on its own, but together they make a system hard to understand and modify.

## Why It Matters

Because complexity creeps in gradually, developers stop noticing it. "It's just one more flag" becomes the rationale for hundreds of flags. The cost of each increment is tiny, but the aggregate cost is enormous. Fighting complexity requires treating every small increase as a big deal.

## How to Apply

- Before adding a special case, parameter, or conditional, ask: "Is this making the system harder to understand?"
- Resist "just this once" thinking. If a change adds complexity, find a way to absorb it or push back on the requirement.
- When reviewing code, flag incremental complexity even if each individual instance seems small.
- Prefer solutions that reduce or hold the line on complexity over solutions that are expedient but add to it.

## Red Flags

- Methods or classes that have grown many parameters over time.
- Boolean flags that toggle behavior in subtle ways.
- Comments like "this is a special case for X" appearing frequently.
- Code where you need to understand many conditions to trace a single path.

## Examples

**Bad:** Adding a `isLegacy` flag to a function that changes behavior in three different places inside the function body.

**Good:** Creating a separate implementation for the legacy path, keeping both paths simple and independent.
