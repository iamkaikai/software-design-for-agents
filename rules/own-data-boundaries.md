---
name: Mistaking Shared Data for Harmless Convenience
chapter: external
tags: [architecture, data, boundaries]
---

## Principle

Shared schemas, shared tables, and backdoor reads are not neutral conveniences. They are architectural coupling.

## Common Mistake

Using shared data access as the easy path while still claiming the surrounding systems are meaningfully separate.

## Why It Is Tempting

- Shared storage avoids duplication and makes queries easy.
- Cross-system joins feel simpler than publishing contracts or building synchronization paths.
- Teams can move quickly at first because they are borrowing each other's data model instead of negotiating interfaces.

## What Goes Wrong

- Changes to one schema ripple across many services or subsystems.
- Ownership becomes ambiguous because several teams rely on the same internal representation.
- The system looks decoupled in deployment diagrams while remaining tightly coupled in the data layer.

## Better Decision Pattern

- Treat shared data access as a coupling decision, not just a storage implementation detail.
- Ask whether the shared schema reflects one coherent boundary or a shortcut around missing contracts.
- Prefer explicit data contracts when the systems are supposed to evolve independently.

## Trade-offs and Boundaries

- Separate data ownership introduces duplication, synchronization, and eventual consistency costs.
- In a cohesive monolith or tightly coupled subsystem, one shared database can still be the honest design.
- The mistake is not duplication or sharing by itself; the mistake is pretending a shared data model has no boundary consequence.

## Ask for Clarification When

- A service wants autonomy but still needs direct reads from another service's tables.
- Schema changes now require routine cross-team coordination.
- The justification for shared storage is "it was easier than designing the interface."

## Red Flags

- Several teams treat one schema as theirs.
- Services are independently deployed but not independently evolvable.
- Data access bypasses public contracts during deadlines and never gets repaired.

## Examples

**Failure pattern:** Two services share the same tables so they can move faster, then neither can change its model without coordinating every release.

**Counterexample:** A monolith with one shared database and one coherent ownership model, where pretending there are independent services would only add ceremony.
