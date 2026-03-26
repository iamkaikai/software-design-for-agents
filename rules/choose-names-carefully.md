---
name: Choose Names Carefully
chapter: 14
tags: [naming, readability]
---

## Principle

Names are a form of abstraction. A good name conveys the essential nature of a thing precisely and concisely. Vague, generic, or misleading names force readers to look at the implementation to understand what something does.

## Why It Matters

Names are read far more often than they are written. A poor name creates a false mental model that leads to bugs. A good name reduces cognitive load by communicating exactly what something is or does.

## How to Apply

- Names should be precise: `getCount` is vague, `getActiveUserCount` is clear.
- Avoid generic names like `data`, `result`, `info`, `manager`, `handler`, `process` unless the scope is very narrow.
- Use consistent naming conventions across the codebase.
- If you can't find a good name, it may be a sign that the thing's purpose isn't well-defined — reconsider the design.
- Name length should be proportional to scope: short names for loop variables, descriptive names for module-level functions.

## Red Flags

- Variables named `tmp`, `data`, `result`, `val` with wide scope.
- Functions named `processData()` or `handleRequest()` that give no hint of what processing or handling means.
- Names that are misleading — e.g., a function called `getUser()` that also modifies state.
- Inconsistent naming: `fetchUser` in one place, `loadUser` in another, for the same operation.

## Examples

**Bad:** `def process(d)` — says nothing about what it processes or what `d` is.

**Good:** `def calculateMonthlyRevenue(transactions)` — the name tells you both the input and the output.
