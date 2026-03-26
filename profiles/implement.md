# Profile: Implementation

Use these rules when writing new modules, features, or systems.

Read the trade-off sections, not just the rule titles. If a rule would hide an important distinction or force a surprising semantic choice, stop and clarify the contract before implementation.

## Primary Rules

Apply these rules during most implementation work:

1. **[Working Code Isn't Enough](../rules/tactical-vs-strategic.md)** — Invest in design, not just behavior.
2. **[Deep Modules](../rules/deep-modules.md)** — Prefer small interfaces over small implementations.
3. **[Information Hiding](../rules/information-hiding.md)** — Decide what knowledge each module should own.
4. **[General-Purpose Modules](../rules/general-purpose-modules.md)** — Solve the broader problem, not only today's caller.
5. **[Pull Complexity Downward](../rules/pull-complexity-downward.md)** — Move repeated caller burden inward when semantics remain honest.
6. **[Better Together Or Better Apart](../rules/better-together-or-better-apart.md)** — Choose decomposition based on overall complexity, not size alone.
7. **[Design It Twice](../rules/design-it-twice.md)** — Compare alternatives before fixing the interface.
8. **[Write Comments First](../rules/write-comments-first.md)** — Use early comments to test whether the abstraction is clear.
9. **[Decide What Matters](../rules/decide-what-matters.md)** — Center the design on the distinctions that actually matter.

## Secondary Rules

Apply when relevant:

10. **[Define Errors Out of Existence](../rules/define-errors-out-of-existence.md)** — Simplify branch-heavy error handling only when the new semantics stay clear.
11. **[Why Write Comments](../rules/why-write-comments.md)** — Document what code cannot express by itself.
12. **[Choose Names Carefully](../rules/choose-names-carefully.md)** — Name the important distinctions directly.
13. **[Different Layer, Different Abstraction](../rules/different-layer-different-abstraction.md)** — Do not add layers that merely relay the same idea.
14. **[Designing for Performance](../rules/designing-for-performance.md)** — Keep performance decisions measured and proportional.

## Implementation Checklist

Before considering the code done, ask:

- [ ] What complexity did this design remove?
- [ ] What complexity did it move into semantics, defaults, implementation, or operations?
- [ ] Which distinctions must stay visible to callers?
- [ ] Did I compare at least one materially different alternative where the boundary mattered?
- [ ] Is the interface simpler than the implementation behind it?
- [ ] If the trade-off is still ambiguous, did I clarify the contract instead of guessing?
