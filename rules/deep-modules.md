---
name: Deep Modules
chapter: 4
tags: [interfaces, abstraction, modules]
---

## Principle

Prefer modules whose interface is small relative to the functionality and complexity they hide.

## Why It Matters

Interfaces are paid for by every caller. A deep module concentrates complexity behind a boundary so the rest of the system can ignore most of it.

## What It Simplifies

- It reduces the amount of API surface that callers must learn.
- It replaces multi-step usage protocols with a smaller number of meaningful operations.
- It keeps implementation detail local instead of making every caller participate.

## Trade-offs and Boundaries

- Deep does not mean large in every direction. A big interface with many unrelated features is not deep; it is sprawling.
- A deep abstraction still requires callers to understand its contract, invariants, and failure modes.
- Sometimes the cheapest honest interface is narrow because the underlying behavior truly differs across use cases.
- Ask for clarification when a module boundary is being defined around team ownership or file layout rather than around a coherent abstraction.

## When Context Changes the Answer

- Internal helper layers can be smaller and narrower if they support one higher-level abstraction cleanly.
- Public or shared modules benefit most from depth because interface clutter is multiplied across many callers.

## Red Flags

- A caller must make several ordered calls to complete one logical task.
- Wrapper modules mostly pass through calls with renamed methods.
- The interface exposes many toggles that mirror implementation choices.
- You can only understand the top-level module by reading several lower-level helpers in detail.

## Examples

**Helpful:** A storage client that exposes `put`, `get`, and `delete` while hiding retries, pooling, and encoding.

**Backfires:** A "deep" service object that hides too much important behavior and forces callers to guess at lifecycle, latency, or consistency semantics.
