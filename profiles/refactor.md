# Profile: Refactoring

Use these rules when refactoring or restructuring existing code.

## Primary Rules

Apply these rules during every refactoring:

1. **[Complexity Is Incremental](../rules/complexity-is-incremental.md)** — The goal of refactoring is to reduce accumulated complexity. Measure success by whether the system is simpler after.
2. **[Deep Modules](../rules/deep-modules.md)** — Merge shallow modules into deeper ones. Split modules that do too many unrelated things.
3. **[Information Hiding](../rules/information-hiding.md)** — Fix information leakage by consolidating leaked knowledge into a single module.
4. **[Different Layer, Different Abstraction](../rules/different-layer-different-abstraction.md)** — Eliminate pass-through methods and redundant layers.
5. **[Consistency](../rules/consistency.md)** — Use refactoring as an opportunity to converge on consistent patterns.
6. **[Modifying Existing Code](../rules/modifying-existing-code.md)** — Every change should leave the design cleaner, not just different.

## Secondary Rules

Apply when relevant:

7. **[General-Purpose Modules](../rules/general-purpose-modules.md)** — Replace use-case-specific interfaces with general-purpose ones.
8. **[Pull Complexity Downward](../rules/pull-complexity-downward.md)** — Move repeated caller-side logic into the module being called.
9. **[Code Should Be Obvious](../rules/code-should-be-obvious.md)** — Rewrite non-obvious code to be clear.

## Refactoring Checklist

After refactoring, verify:

- [ ] Is the system simpler (fewer concepts, cleaner interfaces) than before?
- [ ] Have shallow modules been merged into deeper ones?
- [ ] Is leaked information now properly encapsulated?
- [ ] Have pass-through layers been eliminated?
- [ ] Do remaining patterns and conventions remain consistent?
- [ ] Does the refactored code still fit cleanly into the surrounding design?
