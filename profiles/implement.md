# Profile: Implementation

Use these rules when writing new code — new features, modules, or systems.

## Primary Rules

Apply these rules during every implementation:

1. **[Tactical vs Strategic](../rules/tactical-vs-strategic.md)** — Invest in good design. Don't just make it work — make it clean.
2. **[Deep Modules](../rules/deep-modules.md)** — Design modules with simple interfaces and rich implementations.
3. **[Information Hiding](../rules/information-hiding.md)** — Each module should encapsulate and hide its design decisions.
4. **[General-Purpose Modules](../rules/general-purpose-modules.md)** — Design interfaces for the general problem, not just today's caller.
5. **[Pull Complexity Downward](../rules/pull-complexity-downward.md)** — Handle complexity inside the module, not at the call site.
6. **[Design It Twice](../rules/design-it-twice.md)** — Consider at least two designs before committing to one.
7. **[Write Comments First](../rules/write-comments-first.md)** — Write interface comments before implementation to clarify your thinking.

## Secondary Rules

Apply when relevant:

8. **[Define Errors Out of Existence](../rules/define-errors-out-of-existence.md)** — Design APIs so errors can't happen in the first place.
9. **[Choose Names Carefully](../rules/choose-names-carefully.md)** — Invest time in precise, consistent names.
10. **[Different Layer, Different Abstraction](../rules/different-layer-different-abstraction.md)** — Each layer should transform the abstraction, not just pass it through.

## Implementation Checklist

Before considering a piece of code done, ask:

- [ ] Is the interface much simpler than the implementation?
- [ ] Is knowledge hidden — would a change to internals require changing callers?
- [ ] Did I consider an alternative design?
- [ ] Are comments written for the interface explaining the abstraction?
- [ ] Does the module pull complexity inward rather than pushing it to callers?
- [ ] Are names precise enough that the code reads without needing comments?
