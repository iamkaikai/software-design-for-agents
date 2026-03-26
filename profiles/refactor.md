# Profile: Refactoring

Use these rules when restructuring existing code.

Refactoring should reduce the system's ongoing knowledge burden, not just rearrange files or objects.

## Primary Rules

Apply these rules during most refactors:

1. **[Complexity Is Incremental](../rules/complexity-is-incremental.md)** — Remove accumulated burden, not only obvious breakage.
2. **[Deep Modules](../rules/deep-modules.md)** — Merge shallow surfaces into deeper abstractions where that lowers interface cost.
3. **[Better Together Or Better Apart](../rules/better-together-or-better-apart.md)** — Revisit whether code is separated or joined in the right places.
4. **[Information Hiding](../rules/information-hiding.md)** — Consolidate leaked knowledge into clearer ownership.
5. **[Different Layer, Different Abstraction](../rules/different-layer-different-abstraction.md)** — Eliminate pass-through structure.
6. **[Modifying Existing Code](../rules/modifying-existing-code.md)** — Leave the design cleaner than it was.
7. **[Consistency](../rules/consistency.md)** — Converge on patterns that lower reader effort.
8. **[Decide What Matters](../rules/decide-what-matters.md)** — Move the design toward the distinctions that actually deserve the structure.

## Secondary Rules

Apply when relevant:

9. **[General-Purpose Modules](../rules/general-purpose-modules.md)** — Pull special-purpose logic upward where a shared mechanism should stay clean.
10. **[Pull Complexity Downward](../rules/pull-complexity-downward.md)** — Collapse repeated caller-side work into stable modules.
11. **[Code Should Be Obvious](../rules/code-should-be-obvious.md)** — Simplify the reader's path through the code.
12. **[Designing for Performance](../rules/designing-for-performance.md)** — Preserve or improve critical-path efficiency without cargo-cult optimization.

## Refactoring Checklist

After refactoring, verify:

- [ ] Is the system simpler in the way future readers and modifiers will feel?
- [ ] Did the refactor remove interfaces, branches, or duplicated knowledge rather than only relocate them?
- [ ] Are special-purpose and general-purpose concerns separated more cleanly?
- [ ] Did any important distinction get hidden by the cleanup?
- [ ] If performance mattered, was it preserved intentionally rather than by accident?
- [ ] Where the right boundary was unclear, did I clarify it instead of guessing?
