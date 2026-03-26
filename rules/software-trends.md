---
name: Software Trends vs Good Design
chapter: 19
tags: [design, mindset]
---

## Principle

Software trends (design patterns, agile, TDD, OOP, etc.) are tools, not religions. Evaluate each trend based on whether it reduces complexity in your specific situation. Don't apply a pattern just because it's popular — apply it when it genuinely simplifies the system.

## Why It Matters

Cargo-culting trends leads to over-engineered code. Design patterns used where they aren't needed add complexity instead of reducing it. The goal is always the same: reduce the complexity of the system. Trends are only valuable when they serve that goal.

## How to Apply

- Ask "Does this pattern/practice reduce complexity here?" before applying it.
- Don't create abstractions just because a pattern suggests you should — only abstract when it simplifies.
- Test-driven development is useful, but don't let it drive you toward shallow modules or bad interfaces.
- Object-oriented design is a tool, not a goal. Not everything needs to be a class.
- Getters and setters that expose internal state aren't encapsulation — they're ceremony.

## Red Flags

- An `AbstractSingletonProxyFactoryBean` pattern used where a simple function would do.
- Test-driven design that produces many tiny, shallow classes.
- Getter/setter pairs for every field with no real encapsulation.
- Using design patterns as a checklist rather than in response to a real design problem.

## Examples

**Bad:** Creating a `UserFactory`, `UserBuilder`, `UserValidator`, `UserMapper`, and `UserDTO` when a single `User` class with a constructor would suffice.

**Good:** Using the factory pattern only when object creation is genuinely complex and varies at runtime.
