# Profile: Planning

Use these rules when designing systems, choosing boundaries, or deciding on an approach before writing code.

Planning is where design leverage is highest and change is cheapest. The goal is to compare alternatives, surface trade-offs, and fix the important contracts before implementation locks them in.

## Primary Rules

Apply these rules during most planning work:

1. **[Design It Twice](../rules/design-it-twice.md)** — Compare at least two plausible approaches before committing. The first idea is shaped by habit; the second reveals trade-offs.
2. **[Deep Modules](../rules/deep-modules.md)** — Evaluate whether proposed boundaries buy enough leverage. A boundary that exposes as much as it hides is not worth the cost.
3. **[Information Hiding](../rules/information-hiding.md)** — Decide what knowledge each module should own before building it. Ownership assigned after implementation is rarely clean.
4. **[General-Purpose Modules](../rules/general-purpose-modules.md)** — Design for the broader problem class, not only the first caller. The second caller reveals whether the abstraction was right.
5. **[Different Layer, Different Abstraction](../rules/different-layer-different-abstraction.md)** — Each layer should change the abstraction, not relay it. Plan layers that earn their existence.
6. **[Define Errors Out of Existence](../rules/define-errors-out-of-existence.md)** — Design away error branches before they become API surface. Once error paths are in the interface, they are hard to remove.
7. **[Decide What Matters](../rules/decide-what-matters.md)** — Center the design on the distinctions that actually matter. Everything else should be hidden or defaulted.

## Secondary Rules

Apply when relevant:

8. **[Working Code Isn't Enough](../rules/tactical-vs-strategic.md)** — Favor strategic design over fast local fixes when the code will matter again.
9. **[Pull Complexity Downward](../rules/pull-complexity-downward.md)** — Plan for caller simplicity when the module can absorb the burden honestly.
10. **[Better Together Or Better Apart](../rules/better-together-or-better-apart.md)** — Choose decomposition based on overall complexity, not size alone.
11. **[Complexity Is Incremental](../rules/complexity-is-incremental.md)** — Track the complexity budget. Each "small" addition compounds.
12. **[Write Comments First](../rules/write-comments-first.md)** — Sketch interface comments to test whether the abstraction is clear before building it.
13. **[Designing for Performance](../rules/designing-for-performance.md)** — Choose naturally efficient structures now rather than optimizing later.

## Supplemental Architecture Rules

When planning touches service boundaries, deployment topology, or cross-team concerns:

- **[Distribution Has a Premium](../rules/distribution-has-a-premium.md)** — Don't split into services for "clean separation." Only distribute when scaling, isolation, or tech divergence demands it.
- **[Architecture Must Match Team Boundaries](../rules/architecture-must-match-team-boundaries.md)** — Align boundaries with team ownership. Misaligned boundaries create coordination overhead that erodes the design.
- **[Make Quality Trade-offs Explicit](../rules/make-quality-trade-offs-explicit.md)** — Name the quality attributes you are trading (performance vs modularity vs operability). "Better architecture" is not a shared priority until the trade-off is stated.
- **[Record Architectural Decisions](../rules/record-architectural-decisions.md)** — Document the context, alternatives, and trade-offs behind consequential decisions. Future teams will otherwise re-debate from scratch.
- **[Own Data Boundaries](../rules/own-data-boundaries.md)** — Shared databases and backdoor data access are architectural coupling. Give each boundary an explicit data contract.
- **[Operability Is Part of Architecture](../rules/operability-is-part-of-architecture.md)** — Observability, safe rollouts, and failure diagnosis are requirements, not polish. Design signals and migration paths alongside boundaries.

## Planning Checklist

Before committing to a design, ask:

- [ ] Did I compare at least two materially different alternatives?
- [ ] What complexity does this design remove, and where does it move the rest?
- [ ] Are the proposed interfaces deeper than the implementations behind them?
- [ ] Which distinctions must stay visible to callers, and which are hidden?
- [ ] What knowledge must each module own, and is that ownership clean?
- [ ] Are error semantics designed into the interface, or bolted on?
- [ ] If priorities conflict (simplicity vs performance vs extensibility), did I state the chosen priority?
- [ ] If a boundary crosses teams or services, is the cost of distribution justified?
- [ ] Is the decision recorded with enough context to survive team turnover?
- [ ] If an ambiguity would materially change the design, did I clarify it before proceeding?
