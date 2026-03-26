# Rules Index

These rules are context-sensitive design heuristics, not absolute commandments.

Chapter 1 is represented as project framing in the repository docs and synced example files. The public rule set starts at Chapter 2 and now includes explicit coverage for Chapters 9, 12, 20, and 21.

## Core Book-Derived Rules

| #   | Rule                                                  | File                                                                                 | Chapter | Tags                                   |
| --- | ----------------------------------------------------- | ------------------------------------------------------------------------------------ | ------- | -------------------------------------- |
| 1   | Complexity Is Incremental                             | [complexity-is-incremental.md](complexity-is-incremental.md)                         | 2       | complexity, fundamentals               |
| 2   | Working Code Isn't Enough (Tactical vs Strategic)     | [tactical-vs-strategic.md](tactical-vs-strategic.md)                                 | 3       | mindset, complexity, design            |
| 3   | Deep Modules                                          | [deep-modules.md](deep-modules.md)                                                   | 4       | interfaces, abstraction, modules       |
| 4   | Information Hiding and Leakage                        | [information-hiding.md](information-hiding.md)                                       | 5       | abstraction, modules, encapsulation    |
| 5   | General-Purpose Modules                               | [general-purpose-modules.md](general-purpose-modules.md)                             | 6       | interfaces, abstraction, modules       |
| 6   | Different Layer, Different Abstraction                | [different-layer-different-abstraction.md](different-layer-different-abstraction.md) | 7       | abstraction, modules, layers           |
| 7   | Pull Complexity Downward                              | [pull-complexity-downward.md](pull-complexity-downward.md)                           | 8       | complexity, interfaces, modules        |
| 8   | Better Together Or Better Apart                       | [better-together-or-better-apart.md](better-together-or-better-apart.md)             | 9       | modules, methods, decomposition        |
| 9   | Define Errors Out of Existence                        | [define-errors-out-of-existence.md](define-errors-out-of-existence.md)               | 10      | complexity, error-handling, interfaces |
| 10  | Design It Twice                                       | [design-it-twice.md](design-it-twice.md)                                             | 11      | design, process                        |
| 11  | Why Write Comments                                    | [why-write-comments.md](why-write-comments.md)                                       | 12      | comments, documentation, abstractions  |
| 12  | Comments Should Describe Things Not Obvious from Code | [comments-describe-non-obvious.md](comments-describe-non-obvious.md)                 | 13      | comments, documentation, readability   |
| 13  | Choose Names Carefully                                | [choose-names-carefully.md](choose-names-carefully.md)                               | 14      | naming, readability                    |
| 14  | Write Comments First                                  | [write-comments-first.md](write-comments-first.md)                                   | 15      | comments, documentation, process       |
| 15  | Modifying Existing Code                               | [modifying-existing-code.md](modifying-existing-code.md)                             | 16      | maintenance, complexity, design        |
| 16  | Consistency                                           | [consistency.md](consistency.md)                                                     | 17      | readability, conventions, maintenance  |
| 17  | Code Should Be Obvious                                | [code-should-be-obvious.md](code-should-be-obvious.md)                               | 18      | readability, complexity                |
| 18  | Software Trends vs Good Design                        | [software-trends.md](software-trends.md)                                             | 19      | design, mindset                        |
| 19  | Designing for Performance                             | [designing-for-performance.md](designing-for-performance.md)                         | 20      | performance, complexity, measurement   |
| 20  | Decide What Matters                                   | [decide-what-matters.md](decide-what-matters.md)                                     | 21      | prioritization, abstraction, design    |

## Supplemental Architecture Heuristics

These rules are intentionally separate from the 20 book-derived rules. They are written as mistake patterns: tempting instincts, the failure modes they create, and better decision habits to use instead. Most use `Boundary Questions` rather than hard stop-signs so agents do not learn to pause reflexively on every rule.

| Rule | File | Origin | Tags |
| --- | --- | --- | --- |
| Mistaking Distribution for Clean Separation | [distribution-has-a-premium.md](distribution-has-a-premium.md) | External | architecture, distributed-systems, tradeoffs |
| Mistaking the Org Chart for the Architecture | [architecture-must-match-team-boundaries.md](architecture-must-match-team-boundaries.md) | External | architecture, teams, ownership |
| Mistaking "Better Architecture" for a Shared Priority | [make-quality-trade-offs-explicit.md](make-quality-trade-offs-explicit.md) | External | architecture, quality-attributes, tradeoffs |
| Letting Architectural Context Evaporate | [record-architectural-decisions.md](record-architectural-decisions.md) | External | architecture, documentation, decisions |
| Mistaking the Written Contract for the Real Interface | [expect-implicit-interfaces.md](expect-implicit-interfaces.md) | External | architecture, APIs, compatibility |
| Mistaking Abstraction for Removal of Reality | [design-for-abstraction-leaks.md](design-for-abstraction-leaks.md) | External | architecture, abstractions, reality |
| Mistaking Shared Data for Harmless Convenience | [own-data-boundaries.md](own-data-boundaries.md) | External | architecture, data, boundaries |
| Treating Operability as Cleanup Work | [operability-is-part-of-architecture.md](operability-is-part-of-architecture.md) | External | architecture, operability, observability |
