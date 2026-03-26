---
name: General-Purpose Modules
chapter: 6
tags: [interfaces, abstraction, modules]
---

## Principle

Modules should be designed with a somewhat general-purpose interface, even if they are currently only used in one place. The interface should reflect the general nature of the problem, not the specific context of today's usage.

## Why It Matters

A general-purpose interface is simpler because it omits the details of any particular use case. It's also more reusable and more resilient to change — new features can often be implemented without modifying the module.

## How to Apply

- Design the interface to solve the general class of problem, not just today's specific scenario.
- Ask: "What is the simplest interface that covers my current needs?" — not "What does my current caller need?"
- It's fine if the implementation is general-purpose but you only use a subset of it now.
- Avoid adding use-case-specific parameters or methods to a general-purpose module.
- Don't over-generalize — the interface should be driven by real, foreseeable needs, not speculative ones.

## Red Flags

- A text editing module with methods like `backspaceAndCapitalize()` that combine multiple unrelated operations for a specific UI need.
- Functions that accept configuration objects mirroring one caller's exact context.
- Frequent modifications to a "shared" module every time a new use case appears.

## Examples

**Bad:** A text editor class with `deleteTextBeforeCursorAndUpdateUI()` — it bakes a specific UI behavior into the core module.

**Good:** A text editor class with `delete(start, end)` — the UI layer computes the range and calls the general method.
