# Profile: Debugging

Use these rules when diagnosing and fixing bugs.

## Primary Rules

Apply these rules when debugging:

1. **[Code Should Be Obvious](../rules/code-should-be-obvious.md)** — Bugs often live in non-obvious code. If the code is hard to follow, that's likely where the bug is.
2. **[Information Hiding](../rules/information-hiding.md)** — Bugs caused by leaked information (one module depending on another's internals) are common. Check module boundaries.
3. **[Consistency](../rules/consistency.md)** — Inconsistencies in how similar operations are handled are a frequent source of bugs. If two paths should behave the same but are implemented differently, check both.
4. **[Modifying Existing Code](../rules/modifying-existing-code.md)** — When fixing the bug, don't just patch it. Make sure the fix fits the design cleanly.
5. **[Complexity Is Incremental](../rules/complexity-is-incremental.md)** — The bug may stem from complexity that accumulated over time. Consider whether the fix should also simplify the surrounding code.

## Secondary Rules

Apply when relevant:

6. **[Define Errors Out of Existence](../rules/define-errors-out-of-existence.md)** — If the bug is in error handling, consider whether the error condition can be designed away entirely.
7. **[Choose Names Carefully](../rules/choose-names-carefully.md)** — Misleading names cause bugs. If a variable or function name is misleading, fix it as part of the bug fix.
8. **[Different Layer, Different Abstraction](../rules/different-layer-different-abstraction.md)** — Bugs at layer boundaries often result from abstraction leaks between layers.

## Debugging Checklist

When fixing a bug:

- [ ] Is the root cause in non-obvious or overly complex code?
- [ ] Does the fix address the root cause, not just the symptom?
- [ ] Does the fix fit cleanly into the existing design?
- [ ] Could the error condition be defined out of existence?
- [ ] Are there similar patterns elsewhere that have the same bug?
- [ ] Does the fix leave the code simpler and more obvious than before?
