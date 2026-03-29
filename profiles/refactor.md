# Profile: Refactoring

Use these rules when restructuring existing code.

Refactoring should reduce the system's ongoing knowledge burden, not just rearrange files or objects.

## Primary Rules

Apply these rules during most refactors:

1. **[Complexity Is Incremental](../rules/complexity-is-incremental.md)** — Remove accumulated burden, not only obvious breakage. The goal is net complexity reduction.
2. **[Deep Modules](../rules/deep-modules.md)** — Merge shallow surfaces into deeper abstractions where that lowers interface cost. Two shallow modules replaced by one deep module is a win.
3. **[Better Together Or Better Apart](../rules/better-together-or-better-apart.md)** — Revisit whether code is separated or joined in the right places. Split-then-glue patterns often signal a wrong boundary.
4. **[Information Hiding](../rules/information-hiding.md)** — Consolidate leaked knowledge into clearer ownership. If three callers all know the same implementation detail, that detail belongs inside the module.
5. **[Different Layer, Different Abstraction](../rules/different-layer-different-abstraction.md)** — Eliminate pass-through structure. If a layer only renames or relays, it earns nothing.
6. **[Modifying Existing Code](../rules/modifying-existing-code.md)** — Leave the design cleaner than it was. Make the new behavior fit the design, or improve the design until it does.
7. **[Consistency](../rules/consistency.md)** — Converge on patterns that lower reader effort. Inconsistency across similar code paths is a form of complexity.
8. **[Decide What Matters](../rules/decide-what-matters.md)** — Move the design toward the distinctions that actually deserve the structure. Remove structure around distinctions that no longer matter.

## Secondary Rules

Apply when relevant:

9. **[General-Purpose Modules](../rules/general-purpose-modules.md)** — Pull special-purpose logic upward where a shared mechanism should stay clean.
10. **[Pull Complexity Downward](../rules/pull-complexity-downward.md)** — Collapse repeated caller-side work into stable modules. If every caller does the same dance, the module should absorb it.
11. **[Code Should Be Obvious](../rules/code-should-be-obvious.md)** — Simplify the reader's path through the code. Refactoring that makes code harder to follow is not a win.
12. **[Choose Names Carefully](../rules/choose-names-carefully.md)** — Rename when the old name no longer reflects the module's actual responsibility.
13. **[Define Errors Out of Existence](../rules/define-errors-out-of-existence.md)** — Simplify error paths that guard against conditions the redesign makes impossible.
14. **[Designing for Performance](../rules/designing-for-performance.md)** — Preserve or improve critical-path efficiency without cargo-cult optimization. Measure before and after.

## Supplemental Architecture Rules

When refactoring touches boundaries, data ownership, or cross-module contracts:

- **[Expect Implicit Interfaces](../rules/expect-implicit-interfaces.md)** — Before changing behavior, identify undocumented contracts that consumers depend on. Breaking implicit interfaces causes silent failures.
- **[Own Data Boundaries](../rules/own-data-boundaries.md)** — Consolidate shared data access behind explicit contracts. Refactoring is the right time to fix backdoor coupling.
- **[Record Architectural Decisions](../rules/record-architectural-decisions.md)** — Document the motivation behind structural changes. Future teams need to know why the boundary moved, not just that it moved.
- **[Architecture Must Match Team Boundaries](../rules/architecture-must-match-team-boundaries.md)** — Align refactored boundaries with team ownership. A clean boundary that nobody owns will decay.

## Refactoring Checklist

After refactoring, verify:

- [ ] Is the system simpler in the way future readers and modifiers will feel?
- [ ] Did the refactor remove interfaces, branches, or duplicated knowledge rather than only relocate them?
- [ ] Are special-purpose and general-purpose concerns separated more cleanly?
- [ ] Did any important distinction get hidden by the cleanup?
- [ ] Are implicit contracts (ordering, timing, side effects) preserved or explicitly migrated?
- [ ] If data access patterns changed, are boundaries explicit rather than backdoor?
- [ ] If performance mattered, was it preserved intentionally rather than by accident?
- [ ] Is the motivation for the structural change documented?
- [ ] Where the right boundary was unclear, did I clarify it instead of guessing?
