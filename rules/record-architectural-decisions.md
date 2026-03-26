---
name: Letting Architectural Context Evaporate
chapter: external
tags: [architecture, documentation, decisions]
---

## Principle

Consequential architectural decisions should leave behind enough context that future engineers can understand why they were made and when they should be revisited.

## Common Mistake

Keeping major design context in people's heads, chat history, or meeting memory.

## Why It Is Tempting

- Writing down context feels slower than making the decision.
- Teams assume the current participants will remember the rationale.
- Architecture work often happens in discussion, while documentation is deferred until later and then never written.

## What Goes Wrong

- Teams cargo-cult old decisions long after the original assumptions have changed.
- The same design debate repeats every few months because no one can find the last decision.
- Future engineers preserve constraints they do not understand or remove constraints they should have respected.

## Better Decision Pattern

- Record consequential decisions briefly: context, alternatives, trade-offs, and expected consequences.
- Prefer short working notes over heavyweight templates.
- Revisit records when assumptions change instead of treating them as permanent truth.

## Trade-offs and Boundaries

- Not every local design choice deserves an architecture record.
- Over-documenting trivial decisions creates noise and teaches teams to ignore the records.
- The value is not in formality; it is in preserving the reasoning behind decisions that shape the system.

## Boundary Questions

- Can anyone state why this option beat the alternatives for a decision that affects boundaries, deployments, data ownership, or compatibility?
- Is a long-lived constraint being preserved on authority rather than on visible reasoning?
- Is the team saying "we decided this before" without being able to recover the assumptions?

## Red Flags

- Architecture is explained as folklore.
- Teams keep re-litigating the same structural questions.
- Old diagrams show the result but not the rationale.
- A once-reasonable boundary survives after its original pressure disappeared.

## Examples

**Failure pattern:** Preserving a service split for years because "there was a reason," even though no one can explain the trade-off anymore.

**Counterexample:** Keeping a lightweight ADR for a data boundary decision so later engineers can revisit it when traffic, team structure, and compliance needs change.
