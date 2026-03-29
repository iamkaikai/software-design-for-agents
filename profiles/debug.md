# Profile: Debugging

Use these rules when diagnosing and fixing bugs.

The best fix usually clarifies a broken contract, hidden distinction, or accumulated complexity instead of only patching the visible symptom.

## Primary Rules

Apply these rules when debugging:

1. **[Code Should Be Obvious](../rules/code-should-be-obvious.md)** — Bugs cluster where behavior is hard to predict. If the code is hard to follow, the bug is likely in the gap between what the code appears to do and what it actually does.
2. **[Information Hiding](../rules/information-hiding.md)** — Check whether leaked knowledge or hidden assumptions caused the failure. When a caller depends on implementation details it should not know, breakage is inevitable.
3. **[Consistency](../rules/consistency.md)** — Divergent handling of similar cases often reveals the bug. When two paths should behave the same but don't, the inconsistency is the root cause.
4. **[Modifying Existing Code](../rules/modifying-existing-code.md)** — Fix the design fit, not only the symptom. A patch that leaves the broken contract in place will break again.
5. **[Complexity Is Incremental](../rules/complexity-is-incremental.md)** — Look for the small decisions that accumulated into the failure. The bug is often not one mistake but ten "harmless" ones.
6. **[Decide What Matters](../rules/decide-what-matters.md)** — Identify which distinction was ignored, hidden, or treated as unimportant. The missing distinction is often the root cause.

## Secondary Rules

Apply when relevant:

7. **[Define Errors Out of Existence](../rules/define-errors-out-of-existence.md)** — Remove unnecessary error branches only when the remaining semantics stay honest. A "simplified" error path that swallows a real invariant creates the next bug.
8. **[Choose Names Carefully](../rules/choose-names-carefully.md)** — Misleading names often point directly at wrong assumptions. If the name says one thing and the code does another, start there.
9. **[Different Layer, Different Abstraction](../rules/different-layer-different-abstraction.md)** — Bugs often leak across confused boundaries. When layers don't change the abstraction, errors propagate undetected.
10. **[Better Together Or Better Apart](../rules/better-together-or-better-apart.md)** — Check whether the bug lives in a seam between modules that should have been joined, or in a monolith that should have been split.
11. **[Deep Modules](../rules/deep-modules.md)** — A shallow module that leaks its internals is a likely source of caller-side bugs. The fix may be to deepen the module, not patch the caller.
12. **[Designing for Performance](../rules/designing-for-performance.md)** — Performance fixes can create or reveal correctness bugs when trade-offs were implicit. Check whether an optimization assumed invariants that don't hold.

## Supplemental Architecture Rules

When debugging crosses service boundaries or involves distributed behavior:

- **[Expect Implicit Interfaces](../rules/expect-implicit-interfaces.md)** — Undocumented behavioral contracts (ordering, timing, defaults, side effects) are the most common source of cross-boundary bugs. The written contract passed; the implicit one broke.
- **[Design for Abstraction Leaks](../rules/design-for-abstraction-leaks.md)** — The abstraction promised to hide a detail, but the detail leaked through (latency spike, partial failure, eventual consistency). The fix is to acknowledge the leak, not to add another layer of hiding.
- **[Operability Is Part of Architecture](../rules/operability-is-part-of-architecture.md)** — If you cannot observe the failure, you cannot diagnose it. Check whether missing signals, health checks, or rollout safeguards made the bug harder to find or reproduce.

## Debugging Checklist

When fixing a bug, ask:

- [ ] What misunderstanding allowed this bug to happen?
- [ ] Was an important distinction hidden, collapsed, or named poorly?
- [ ] Does the fix reduce the root complexity instead of only adding another branch?
- [ ] If I simplify the error path, do I still preserve the distinctions that matter?
- [ ] Are there parallel paths elsewhere that carry the same wrong assumption?
- [ ] Did the bug cross a module or service boundary? If so, was an implicit contract broken?
- [ ] Did an abstraction leak a detail it claimed to hide?
- [ ] Can the system observe this class of failure, or did I find it by accident?
- [ ] If the correct contract is still unclear, did I stop and clarify it before changing semantics?
