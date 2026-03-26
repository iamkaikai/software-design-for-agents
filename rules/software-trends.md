---
name: Software Trends vs Good Design
chapter: 19
tags: [design, mindset]
---

## Principle

Treat trends, paradigms, and patterns as tools to evaluate, not doctrines to obey.

## Why It Matters

Popular practices often solve real problems, but applying them mechanically can increase complexity instead of reducing it. Good design still depends on whether the technique fits the specific problem.

## What It Simplifies

- It prevents cargo-cult abstractions and process rituals from becoming design substitutes.
- It redirects attention from ideology to actual complexity costs and benefits.
- It encourages reuse of useful patterns without surrendering judgment to them.

## Trade-offs and Boundaries

- Dismissing trends reflexively is just as shallow as worshipping them. Many patterns exist because they genuinely help.
- The burden moves to evaluation: you must understand what problem the trend solves and whether that problem exists here.
- Familiar frameworks can reduce local decision cost, but only if they do not force irrelevant ceremony onto the design.
- Ask for clarification when a proposed pattern, architecture, or process is being chosen for legitimacy or familiarity rather than for a stated reduction in complexity.

## When Context Changes the Answer

- Strong ecosystem conventions can be worth following when they lower onboarding cost and fit the problem well.
- Custom solutions are preferable when the trend forces awkward abstractions, unnecessary layers, or misleading terminology.

## Red Flags

- Patterns are introduced before the underlying problem is named.
- TDD, OOP, DI, or factories are defended as defaults rather than as responses to a concrete need.
- Getters, setters, or wrappers multiply without adding meaningful behavior.
- A trend makes interfaces or workflows more ceremonial than the domain requires.

## Examples

**Helpful:** Using a factory where object creation truly varies at runtime and callers benefit from a stable creation contract.

**Backfires:** Adding multiple pattern-named layers to a simple workflow because "that is how modern apps are structured."
