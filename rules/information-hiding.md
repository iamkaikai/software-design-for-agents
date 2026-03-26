---
name: Information Hiding and Leakage
chapter: 5
tags: [abstraction, modules, encapsulation]
---

## Principle

Each module should encapsulate knowledge — design decisions, data formats, internal mechanisms — and hide it behind a simple interface. Information leakage occurs when the same knowledge is used in multiple modules, creating tight coupling.

## Why It Matters

When implementation details leak across module boundaries, changes to those details require modifying multiple modules simultaneously. This makes the system fragile and harder to evolve. Information hiding is the most important technique for achieving deep modules.

## How to Apply

- When designing a module, ask: "What knowledge does this module hide from the rest of the system?"
- If two modules both depend on the same piece of knowledge (file format, protocol, algorithm), one of them should own it entirely.
- Avoid exposing internal data structures through your interface.
- Private methods and fields are a tool for information hiding — use them.
- If changing one module always requires changing another, they likely share leaked information.

## Red Flags

- Two classes that both know the details of a file format.
- An interface that exposes internal data structures (returning raw internal maps, lists, etc.).
- Changing a data format requires edits in multiple unrelated files.
- Back-door dependencies via global variables or shared mutable state.
- Classes whose interfaces mirror their implementation closely.

## Examples

**Bad:** Both the `HTTPParser` and the `RequestHandler` know the exact byte layout of the HTTP header format.

**Good:** `HTTPParser` fully owns HTTP format knowledge and exposes a structured `Request` object. `RequestHandler` never sees raw bytes.
