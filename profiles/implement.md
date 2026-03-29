# Profile: Implementation

Use these rules when writing new modules, features, or systems.

Read the trade-off sections, not just the rule titles. If a rule would hide an important distinction or force a surprising semantic choice, stop and clarify the contract before implementation.

## Primary Rules

Apply these rules during most implementation work:

1. **[Working Code Isn't Enough](../rules/tactical-vs-strategic.md)** — Invest in design, not just behavior. Tactical shortcuts compound into strategic debt.
2. **[Deep Modules](../rules/deep-modules.md)** — Prefer small interfaces over small implementations. A module that hides substantial complexity behind a simple contract earns its existence.
3. **[Information Hiding](../rules/information-hiding.md)** — Decide what knowledge each module should own. If a caller must know how the module works to use it correctly, the abstraction has leaked.
4. **[General-Purpose Modules](../rules/general-purpose-modules.md)** — Solve the broader problem, not only today's caller. The interface should not embed the first use case's workflow.
5. **[Pull Complexity Downward](../rules/pull-complexity-downward.md)** — Move repeated caller burden inward when semantics remain honest. Callers should not all solve the same problem.
6. **[Better Together Or Better Apart](../rules/better-together-or-better-apart.md)** — Choose decomposition based on overall complexity, not size alone. Three similar lines are better than a premature abstraction.
7. **[Design It Twice](../rules/design-it-twice.md)** — Compare alternatives before fixing the interface. The first idea is shaped by the current call site.
8. **[Write Comments First](../rules/write-comments-first.md)** — Use early comments to test whether the abstraction is clear. If the comment is hard to write, the interface needs work.
9. **[Decide What Matters](../rules/decide-what-matters.md)** — Center the design on the distinctions that actually matter. Everything else should be hidden or defaulted.

## Secondary Rules

Apply when relevant:

10. **[Define Errors Out of Existence](../rules/define-errors-out-of-existence.md)** — Simplify branch-heavy error handling only when the new semantics stay clear. Prefer structural prevention over semantic redefinition over guard clauses.
11. **[Why Write Comments](../rules/why-write-comments.md)** — Document what code cannot express by itself: rationale, invariants, surprising consequences.
12. **[Choose Names Carefully](../rules/choose-names-carefully.md)** — Name the important distinctions directly. A misleading name is worse than a long name.
13. **[Different Layer, Different Abstraction](../rules/different-layer-different-abstraction.md)** — Do not add layers that merely relay the same idea. Each layer must transform the abstraction.
14. **[Code Should Be Obvious](../rules/code-should-be-obvious.md)** — Arrange code so a reasonable reader can form the right mental model quickly.
15. **[Consistency](../rules/consistency.md)** — Follow existing patterns so readers carry knowledge from one part of the system to another.
16. **[Complexity Is Incremental](../rules/complexity-is-incremental.md)** — Each "small" addition has a real cost. Track the running total.
17. **[Designing for Performance](../rules/designing-for-performance.md)** — Keep performance decisions measured and proportional. Complexity for performance without measurement is cargo cult.

## Supplemental Architecture Rules

When implementation touches service boundaries or cross-module contracts:

- **[Expect Implicit Interfaces](../rules/expect-implicit-interfaces.md)** — Consumers depend on actual observable behavior, not just the written contract. Undocumented ordering, timing, and defaults are hidden dependencies you must respect.
- **[Design for Abstraction Leaks](../rules/design-for-abstraction-leaks.md)** — Abstractions hide details but cannot erase reality (latency, failure, consistency). Design interfaces that acknowledge and make survivable the leaks that still matter.
- **[Make Quality Trade-offs Explicit](../rules/make-quality-trade-offs-explicit.md)** — Name the quality attributes you are trading. If you chose speed over safety, say so.
- **[Operability Is Part of Architecture](../rules/operability-is-part-of-architecture.md)** — Build observability signals, health checks, and safe rollout paths during implementation, not after.

## Implementation Checklist

Before considering the code done, ask:

- [ ] What complexity did this design remove?
- [ ] What complexity did it move into semantics, defaults, implementation, or operations?
- [ ] Which distinctions must stay visible to callers?
- [ ] Did I compare at least one materially different alternative where the boundary mattered?
- [ ] Is the interface simpler than the implementation behind it?
- [ ] Are names, comments, and APIs aligned on the same semantics?
- [ ] Does the code follow existing patterns, or does it diverge for a good reason?
- [ ] Are error paths designed into the interface or bolted on as afterthoughts?
- [ ] If the code crosses a service or module boundary, does it respect implicit contracts?
- [ ] If the trade-off is still ambiguous, did I clarify the contract instead of guessing?
