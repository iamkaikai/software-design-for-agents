---
name: General-Purpose Modules
chapter: 6
tags: [interfaces, abstraction, modules]
---

## Principle

Design modules around the broader class of problem they solve, not only the first caller that happens to need them.

## Why It Matters

Interfaces that mirror a single use case tend to accrete special-case methods and arguments as more callers arrive. A somewhat general-purpose interface is often both simpler and more resilient.

## What It Simplifies

- It reduces future interface churn caused by today's overly specific choices.
- It replaces many caller-specific entry points with a smaller set of more composable operations.
- It often improves information hiding because the module is no longer shaped around one caller's workflow.

## Trade-offs and Boundaries

- "Somewhat general-purpose" does not mean guessing at every future need. Speculative abstraction creates its own complexity.
- A general interface still has to be easy for today's caller to use; generic ceremony is not a win.
- The complexity often moves from specialized convenience methods into more explicit caller composition.
- Clarify the trade-off when pressure to make an API "general" is really pressure to anticipate unknown future requirements without evidence.

## When Context Changes the Answer

- Shared infrastructure should bias toward generality more than one-off application glue.
- Specialized operations may still belong outside the general module, layered on top of it where the specialization actually matters.

## Red Flags

- Method names encode UI gestures, workflows, or one caller's exact intent.
- Each new use case requires a new method in the same shared module.
- Option objects mirror one specific endpoint or screen.
- A supposedly reusable module is only understandable in terms of one caller.

## Examples

**Helpful:** Exposing `insert(range, text)` instead of `backspaceAtCursor`.

**Backfires:** Introducing a generic plugin system when two straightforward operations would have kept the interface clearer.
