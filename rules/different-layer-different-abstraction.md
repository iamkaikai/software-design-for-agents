---
name: Different Layer, Different Abstraction
chapter: 7
tags: [abstraction, modules, layers]
---

## Principle

Each layer of a system should provide a different abstraction from the layers above and below it. If adjacent layers have similar abstractions, the decomposition is likely wrong — classes may be too shallow or responsibilities may be poorly divided.

## Why It Matters

When adjacent layers operate at the same level of abstraction, they create pass-through methods and shallow modules. This adds complexity without adding value. Good layering means each level transforms or simplifies what the level below provides.

## How to Apply

- When writing a method that mostly just calls another method with the same signature, ask whether the layers are properly separated.
- Each layer should add meaningful transformation, aggregation, or simplification.
- If a decorator or wrapper just delegates without changing the abstraction, consider eliminating it.
- Think of layers as a progression from low-level (close to the machine/storage) to high-level (close to the user/business logic).

## Red Flags

- Pass-through methods that add no logic, just forward calls.
- A class whose methods have the same signatures as the methods of the class it wraps.
- Multiple layers of classes with nearly identical interfaces.
- Dispatcher or router classes that just map calls to another class with the same API.

## Examples

**Bad:** A `UserService` that has a `getUser(id)` method which simply calls `UserRepository.getUser(id)` with no additional logic.

**Good:** A `UserService` that provides `getUserProfile(id)` — combining data from `UserRepository`, `PreferencesRepository`, and an avatar service into a unified view.
