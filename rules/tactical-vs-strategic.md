---
name: Working Code Isn't Enough (Tactical vs Strategic)
chapter: 3
tags: [mindset, complexity, design]
---

## Principle

A tactical programmer focuses on getting features working as quickly as possible. A strategic programmer invests time in good design, knowing that a clean structure pays off over time. Working code is not enough — the code must also have a clean design.

## Why It Matters

Tactical programming accumulates complexity rapidly. Each shortcut makes the next change harder. Strategic programming treats every code change as an opportunity to improve the system's design, not just ship a feature.

## How to Apply

- When implementing a feature, spend a small amount of extra time (10–20%) finding a clean design rather than the fastest path.
- If the cleanest implementation requires refactoring existing code, do the refactoring — don't layer new code on top of a bad structure.
- Don't introduce technical debt intentionally. "We'll fix it later" almost never happens.
- Every change to the system should leave the design at least as clean as it was before, ideally cleaner.

## Red Flags

- PRs that are described as "quick fix" or "hack" with a TODO to clean up later.
- Duplicated logic introduced to avoid modifying an existing abstraction.
- Pattern of shipping fast and immediately needing follow-up bug fixes.
- Developers afraid to modify existing code because it's fragile.

## Examples

**Bad:** Copy-pasting a function and modifying the copy, because changing the original feels risky.

**Good:** Refactoring the original function to be general-purpose enough to handle both use cases.
