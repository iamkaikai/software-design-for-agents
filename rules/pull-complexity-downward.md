---
name: Pull Complexity Downward
chapter: 8
tags: [complexity, interfaces, modules]
---

## Principle

When a choice must be made between a simpler implementation and a simpler interface, usually prefer the simpler interface and carry the complexity inside the module.

## Why It Matters

Implementation complexity is paid once. Interface complexity is paid by every caller, reviewer, and future maintainer. Pulling complexity downward can reduce total system cost even when the module itself gets harder to implement.

## What It Simplifies

- It removes repeated boilerplate from call sites.
- It replaces distributed edge-case handling with one internal implementation.
- It often lowers the cognitive load of common usage.

## Trade-offs and Boundaries

- Complexity should move downward only when the module can still expose honest, predictable semantics.
- Pulling too much inward can hide important distinctions, operational costs, or rare-but-critical choices that callers actually need to control.
- The complexity does not disappear; it moves into defaults, policies, and internal branching that must still be designed well.
- Ask for clarification when the proposed simplification removes a caller choice that may matter for correctness, visibility, or performance.

## When Context Changes the Answer

- Good defaults are valuable when most callers want the same thing.
- Explicit options are better when usage varies materially and hidden policy would surprise callers.

## Red Flags

- Every caller passes the same options or performs the same validation first.
- Callers repeatedly wrap the same module with helper functions just to make common usage tolerable.
- A "simple" API hides costly or irreversible behavior that callers discover too late.
- Rare use cases are handled by undocumented conventions rather than visible extension points.

## Examples

**Helpful:** `connect(host)` uses safe defaults while an advanced path exists for unusual needs.

**Backfires:** Automatically retrying non-idempotent operations without giving callers control or visibility.
