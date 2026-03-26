---
name: Information Hiding and Leakage
chapter: 5
tags: [abstraction, modules, encapsulation]
---

## Principle

Each module should own specific design knowledge and keep that knowledge from spreading unnecessarily.

## Why It Matters

When the same knowledge appears in multiple places, the system becomes harder to change because one design decision now has many dependents. Information hiding is one of the main ways to contain change amplification.

## What It Simplifies

- It reduces the number of places that must change when an internal decision changes.
- It lets callers operate on a simpler view of the module rather than its representation.
- It replaces distributed knowledge with a single point of truth.

## Trade-offs and Boundaries

- Hiding is only good when the hidden information is not needed by callers to act correctly.
- This rule shifts understanding from representation details to module contracts; callers still need the parts of the truth that affect semantics, performance, or safety.
- Over-hiding can make important distinctions invisible and create surprising behavior.
- Clarify the trade-off when a proposed abstraction hides data, modes, or operational differences that callers may need in order to make correct decisions.

## When Context Changes the Answer

- Internal data structures usually should be hidden.
- User-visible guarantees, tuning knobs that materially affect behavior, and distinctions needed for correctness usually should remain visible.

## Red Flags

- Two modules both know the same file format, protocol rule, or validation logic.
- An API returns raw internal maps, records, or state objects that callers must interpret.
- A change to representation requires changes in distant callers.
- Module boundaries follow execution order instead of ownership of knowledge.

## Examples

**Helpful:** One parser owns wire-format details and returns a domain object.

**Backfires:** A transport layer hides delivery guarantees that application code must actually reason about.
