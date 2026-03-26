---
name: Mistaking the Org Chart for the Architecture
chapter: external
tags: [architecture, teams, ownership]
---

## Principle

Team structure strongly shapes technical boundaries, but neither one should blindly dictate the other.

## Common Mistake

Designing boundaries only around the current org chart, or ignoring coordination cost entirely and pretending architecture is purely technical.

## Why It Is Tempting

- Team lines are visible and already come with ownership labels.
- It feels efficient to align technical structure to existing management structure.
- On the other side, architects often want to ignore organizational constraints and design a "pure" structure.

## What Goes Wrong

- Boundaries become optimized for reporting lines instead of for coherent change.
- Or the architecture demands cross-team coordination for every routine change because no one priced communication cost into the design.
- Incidents, roadmap changes, and migrations become ownership fights instead of technical work.

## Better Decision Pattern

- Treat communication paths, approval flow, and ownership as architectural forces.
- Ask which code, data, and workflows tend to change together and who can realistically own them end to end.
- Align architecture and team boundaries where that reduces coordination, and deliberately reshape one or the other where they are misaligned.

## Trade-offs and Boundaries

- Mirroring the org chart blindly can fossilize temporary or dysfunctional structures.
- Ignoring team realities can produce elegant diagrams that no team can actually maintain.
- The right move is often a negotiation between domain cohesion and coordination cost, not obedience to either one alone.

## Boundary Questions

- Does this boundary create split ownership for one workflow?
- Will routine changes require two or more teams to move together without a strong reason?
- Does this module exist mainly because a team exists, not because the domain boundary is real?

## Red Flags

- Incident response starts with "who owns this?" instead of "what failed?"
- Teams access each other's internals because the official boundary is impractical.
- A single customer-facing capability is fragmented across many teams with no clear contract between them.

## Examples

**Failure pattern:** Creating separate services because separate teams already exist, even though the workflow and data model are still one tightly coupled unit.

**Counterexample:** Deliberately shaping team ownership around a stable product boundary so the people who build it can also operate and evolve it.
