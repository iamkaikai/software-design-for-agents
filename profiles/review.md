# Profile: Code Review

Use these rules when reviewing code changes.

Review for trade-offs, not just local correctness. The main question is whether the change makes the system easier or harder to reason about over time.

## Primary Rules

Apply these rules to most reviews:

1. **[Complexity Is Incremental](../rules/complexity-is-incremental.md)** — Small complexity increases still count.
2. **[Deep Modules](../rules/deep-modules.md)** — Check whether new interfaces buy enough leverage.
3. **[Information Hiding](../rules/information-hiding.md)** — Look for leaked knowledge and overexposed representation.
4. **[Better Together Or Better Apart](../rules/better-together-or-better-apart.md)** — Challenge needless splitting and needless joining.
5. **[Code Should Be Obvious](../rules/code-should-be-obvious.md)** — The intended mental model should be easy to form.
6. **[Choose Names Carefully](../rules/choose-names-carefully.md)** — Names should encode the important distinctions.
7. **[Consistency](../rules/consistency.md)** — Similar ideas should behave in similar ways.
8. **[Decide What Matters](../rules/decide-what-matters.md)** — The change should emphasize the right distinctions, not the incidental ones.

## Secondary Rules

Apply when relevant:

9. **[Define Errors Out of Existence](../rules/define-errors-out-of-existence.md)** — Check whether simplification preserved the distinctions that matter.
10. **[Why Write Comments](../rules/why-write-comments.md)** — Ask whether missing documentation is forcing readers into code archaeology.
11. **[Comments Should Describe Things Not Obvious from Code](../rules/comments-describe-non-obvious.md)** — Comments should add design knowledge, not echo the code.
12. **[Software Trends vs Good Design](../rules/software-trends.md)** — Patterns should earn their keep.
13. **[Designing for Performance](../rules/designing-for-performance.md)** — Complexity added for performance should be measured and justified.

## Review Checklist

When reviewing, ask:

- [ ] Does this change reduce or increase overall system complexity?
- [ ] What new knowledge must readers or callers now carry?
- [ ] Did the change hide something that should remain visible?
- [ ] Are new boundaries deeper, clearer, and more honest than the old ones?
- [ ] Are comments, names, and APIs aligned on the same semantics?
- [ ] If the semantics are ambiguous, did the author clarify them or silently pick one?
