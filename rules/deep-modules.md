---
name: Deep Modules
chapter: 4
tags: [interfaces, abstraction, modules]
---

## Principle

The best modules are deep: they provide powerful functionality behind a simple interface. A deep module hides significant complexity from the rest of the system. The opposite — a shallow module — has a complex interface relative to the small amount of functionality it provides.

## Why It Matters

Every interface represents complexity that the rest of the system must manage. Deep modules minimize this cost by offering a high ratio of functionality to interface complexity. Shallow modules spread complexity across the system because callers must understand more to use them.

## How to Apply

- Design interfaces that are much simpler than the implementation behind them.
- A module with a simple interface but hundreds of lines of implementation is a good sign — it's hiding complexity.
- Avoid creating classes or functions that are little more than pass-throughs.
- If a module's interface is almost as complex as its implementation, consider merging it with an adjacent module or rethinking the decomposition.

## Red Flags

- Classes with many methods that each do very little.
- Interfaces where the caller must make multiple calls in a specific sequence to accomplish one logical operation.
- Functions where the argument list is as complex as the function body.
- Wrapper classes that add little value beyond delegation.

## Examples

**Bad:** A `FileReader` class where the caller must call `open()`, `setEncoding()`, `setBufferSize()`, `readHeader()`, then `readBody()` in order.

**Good:** A `FileReader` class where the caller calls `read(path)` and the class handles encoding detection, buffering, and parsing internally.
