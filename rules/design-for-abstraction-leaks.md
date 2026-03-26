---
name: Mistaking Abstraction for Removal of Reality
chapter: external
tags: [architecture, abstractions, reality]
---

## Principle

Abstractions can hide many details, but they do not erase the underlying realities of latency, failure, consistency, memory, or concurrency.

## Common Mistake

Acting as if a clean abstraction means the underlying phenomenon no longer matters to callers.

## Why It Is Tempting

- Clean abstractions feel safer and easier to reason about.
- Teams want interfaces that are simple and general.
- It is easy to slide from "we hid this well" into "this no longer matters."

## What Goes Wrong

- Callers make incorrect assumptions about timing, retries, consistency, or failure visibility.
- Production incidents reveal realities that the interface encouraged people to ignore.
- The abstraction looks elegant but only because it omitted decisions that users still needed to make.

## Better Decision Pattern

- Hide everything you can without lying about what still matters.
- Decide explicitly which realities must stay visible for correct use.
- Prefer abstractions that make leaks survivable over abstractions that pretend leaks are impossible.

## Trade-offs and Boundaries

- Exposing too many low-level details overwhelms callers and defeats the abstraction.
- Hiding too much makes the interface dishonest.
- The right boundary is not "show everything" or "hide everything," but "show what correct use still depends on."

## Boundary Questions

- Does this boundary hide latency, consistency, retries, caching, or failure behavior that callers may still need?
- Does the interface look simple only because important operational distinctions disappeared from view?
- Can the team explain which underlying realities still matter after the abstraction is applied?

## Red Flags

- Callers learn important behavior only through incidents.
- Retries, timeouts, or consistency semantics are implicit rather than visible.
- Teams talk as if network or storage behavior vanished because it sits behind a client library.

## Examples

**Failure pattern:** A storage client hides consistency mode so completely that callers assume reads are immediately up to date when they are not.

**Counterexample:** A client library that hides transport details but still makes retry and consistency semantics explicit.
