# Profile: Code Review

Use these rules when reviewing code changes (PRs, diffs, code review).

## Primary Rules

Apply these rules to every review:

1. **[Complexity Is Incremental](../rules/complexity-is-incremental.md)** — Is this change adding unnecessary complexity? Even small increments matter.
2. **[Deep Modules](../rules/deep-modules.md)** — Are new modules/classes deep (simple interface, rich implementation) or shallow?
3. **[Information Hiding](../rules/information-hiding.md)** — Does the change leak implementation details across boundaries?
4. **[Different Layer, Different Abstraction](../rules/different-layer-different-abstraction.md)** — Are there new pass-through methods or redundant layers?
5. **[Code Should Be Obvious](../rules/code-should-be-obvious.md)** — Can you understand the change without extensive study?
6. **[Choose Names Carefully](../rules/choose-names-carefully.md)** — Are new names precise and consistent with the codebase?
7. **[Consistency](../rules/consistency.md)** — Does the change follow existing patterns and conventions?

## Secondary Rules

Apply when relevant to the change:

8. **[Define Errors Out of Existence](../rules/define-errors-out-of-existence.md)** — Does new error handling add unnecessary complexity?
9. **[Comments Should Describe Things Not Obvious from Code](../rules/comments-describe-non-obvious.md)** — Are comments adding value, or just restating code?
10. **[Software Trends vs Good Design](../rules/software-trends.md)** — Is a pattern being applied because it helps, or just because it's trendy?

## Review Checklist

When reviewing, ask:

- [ ] Does this change increase or decrease overall system complexity?
- [ ] Are new interfaces simpler than their implementations?
- [ ] Is knowledge properly encapsulated, or does it leak across modules?
- [ ] Could a new team member understand this code without help?
- [ ] Do names accurately communicate purpose?
- [ ] Does the change follow existing codebase conventions?
