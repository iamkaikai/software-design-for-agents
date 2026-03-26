---
name: Modifying Existing Code
chapter: 16
tags: [maintenance, complexity, design]
---

## Principle

When modifying existing code, don't just make the change work — make sure the change fits cleanly into the existing design. If the system's design doesn't accommodate the change well, improve the design as part of the change.

## Why It Matters

Most development time is spent modifying existing code, not writing new code. Each modification is an opportunity to improve the design or to degrade it. If developers only focus on making changes work without considering design, the system degrades steadily.

## How to Apply

- After making a change, step back and ask: "Does this change fit naturally into the existing design, or did I force it in?"
- If a change requires touching many modules, consider whether a refactoring would localize the change.
- Maintain the design invariants of the code you're modifying — don't break abstractions for convenience.
- If you're adding a feature that doesn't fit the current structure, refactor the structure to accommodate it cleanly.
- Leave the code cleaner than you found it.

## Red Flags

- Modifications that scatter related changes across many unrelated files.
- Special-case logic added to a general-purpose module for one specific caller.
- Changes that violate the naming conventions or structural patterns of the surrounding code.
- A change that works but makes the next change harder.

## Examples

**Bad:** Adding an `if (isSpecialCase)` branch in five different functions to support a new feature.

**Good:** Refactoring to introduce a strategy pattern or a new abstraction that handles the new feature alongside existing features in a uniform way.
