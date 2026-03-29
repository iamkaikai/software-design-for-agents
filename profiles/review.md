# Profile: Code Review

Use these rules when reviewing code changes.

Review for trade-offs, not just local correctness. The main question is whether the change makes the system easier or harder to reason about over time.

## Primary Rules

Apply these rules to most reviews:

1. **[Complexity Is Incremental](../rules/complexity-is-incremental.md)** — Small complexity increases still count. Each "minor" addition compounds into the system's long-term burden.
2. **[Deep Modules](../rules/deep-modules.md)** — Check whether new interfaces buy enough leverage. A new boundary that exposes as much as it hides is not earning its cost.
3. **[Information Hiding](../rules/information-hiding.md)** — Look for leaked knowledge and overexposed representation. If callers must understand the implementation to use the interface, the abstraction is broken.
4. **[Better Together Or Better Apart](../rules/better-together-or-better-apart.md)** — Challenge needless splitting and needless joining. Decomposition should reduce total complexity, not just file size.
5. **[Code Should Be Obvious](../rules/code-should-be-obvious.md)** — The intended mental model should be easy to form. If a reviewer struggles to understand the flow, future maintainers will too.
6. **[Choose Names Carefully](../rules/choose-names-carefully.md)** — Names should encode the important distinctions. A misleading name is a latent bug.
7. **[Consistency](../rules/consistency.md)** — Similar ideas should behave in similar ways. Divergence from existing patterns needs justification.
8. **[Decide What Matters](../rules/decide-what-matters.md)** — The change should emphasize the right distinctions, not the incidental ones.

## Secondary Rules

Apply when relevant:

9. **[Define Errors Out of Existence](../rules/define-errors-out-of-existence.md)** — Check whether simplification preserved the distinctions that matter. Removing an error path that hid a real invariant creates a silent bug.
10. **[Why Write Comments](../rules/why-write-comments.md)** — Ask whether missing documentation is forcing readers into code archaeology.
11. **[Comments Should Describe Things Not Obvious from Code](../rules/comments-describe-non-obvious.md)** — Comments should add design knowledge, not echo the code.
12. **[Different Layer, Different Abstraction](../rules/different-layer-different-abstraction.md)** — Flag pass-through layers that relay without transforming.
13. **[Modifying Existing Code](../rules/modifying-existing-code.md)** — Did the change leave the design cleaner, or did it add a tactical patch that makes the next change harder?
14. **[Software Trends vs Good Design](../rules/software-trends.md)** — Patterns should earn their keep. A design pattern applied without justification adds complexity.
15. **[Designing for Performance](../rules/designing-for-performance.md)** — Complexity added for performance should be measured and justified, not assumed.

## Supplemental Architecture Rules

When reviewing changes that touch boundaries, data contracts, or cross-service interactions:

- **[Expect Implicit Interfaces](../rules/expect-implicit-interfaces.md)** — Check whether the change breaks undocumented behavioral contracts that consumers depend on (ordering, timing, defaults, side effects).
- **[Design for Abstraction Leaks](../rules/design-for-abstraction-leaks.md)** — Does the abstraction acknowledge the realities it cannot hide (latency, failure modes, consistency)?
- **[Make Quality Trade-offs Explicit](../rules/make-quality-trade-offs-explicit.md)** — Is the trade-off stated? "Better" is not a quality attribute. Ask what was traded for what.
- **[Record Architectural Decisions](../rules/record-architectural-decisions.md)** — If this change reflects a consequential decision, is the context preserved for future teams?
- **[Distribution Has a Premium](../rules/distribution-has-a-premium.md)** — If a new boundary or service split is introduced, is the cost of distribution justified by a concrete need?
- **[Own Data Boundaries](../rules/own-data-boundaries.md)** — Does the change introduce shared data access or backdoor coupling between modules?

## Review Checklist

When reviewing, ask:

- [ ] Does this change reduce or increase overall system complexity?
- [ ] What new knowledge must readers or callers now carry?
- [ ] Did the change hide something that should remain visible?
- [ ] Are new boundaries deeper, clearer, and more honest than the old ones?
- [ ] Are comments, names, and APIs aligned on the same semantics?
- [ ] Does the change follow existing patterns, or diverge without explanation?
- [ ] Are error paths cleaner, or were real invariants silently removed?
- [ ] If implicit contracts exist (ordering, timing, side effects), are they preserved?
- [ ] If the change touches a service boundary, is the distribution cost justified?
- [ ] If the semantics are ambiguous, did the author clarify them or silently pick one?
