# Profile: Debugging

Use these rules when diagnosing and fixing bugs.

The best fix usually clarifies a broken contract, hidden distinction, or accumulated complexity instead of only patching the visible symptom.

## Primary Rules

Apply these rules when debugging:

1. **[Code Should Be Obvious](../rules/code-should-be-obvious.md)** — Bugs cluster where behavior is hard to predict.
2. **[Information Hiding](../rules/information-hiding.md)** — Check whether leaked knowledge or hidden assumptions caused the failure.
3. **[Consistency](../rules/consistency.md)** — Divergent handling of similar cases often reveals the bug.
4. **[Modifying Existing Code](../rules/modifying-existing-code.md)** — Fix the design fit, not only the symptom.
5. **[Complexity Is Incremental](../rules/complexity-is-incremental.md)** — Look for the small decisions that accumulated into the failure.
6. **[Decide What Matters](../rules/decide-what-matters.md)** — Identify which distinction was ignored, hidden, or treated as unimportant.

## Secondary Rules

Apply when relevant:

7. **[Define Errors Out of Existence](../rules/define-errors-out-of-existence.md)** — Remove unnecessary error branches only when the remaining semantics stay honest.
8. **[Choose Names Carefully](../rules/choose-names-carefully.md)** — Misleading names often point directly at wrong assumptions.
9. **[Different Layer, Different Abstraction](../rules/different-layer-different-abstraction.md)** — Bugs often leak across confused boundaries.
10. **[Designing for Performance](../rules/designing-for-performance.md)** — Performance fixes can create or reveal correctness bugs when trade-offs were implicit.

## Debugging Checklist

When fixing a bug, ask:

- [ ] What misunderstanding allowed this bug to happen?
- [ ] Was an important distinction hidden, collapsed, or named poorly?
- [ ] Does the fix reduce the root complexity instead of only adding another branch?
- [ ] If I simplify the error path, do I still preserve the distinctions that matter?
- [ ] Are there parallel paths elsewhere that carry the same wrong assumption?
- [ ] If the correct contract is still unclear, did I stop and clarify it before changing semantics?
