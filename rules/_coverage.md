# Chapter Coverage

This file maps Chapters 1-21 of *A Philosophy of Software Design* to the rule set in this repo.

Chapter 1 is intentionally represented as project framing in [README.md](../README.md) and the synced files in `examples/`, not as a numbered rule file.


| Chapter | Theme                                                | Representation in This Repo                                                          | Coverage Type |
| ------- | ---------------------------------------------------- | ------------------------------------------------------------------------------------ | ------------- |
| 1       | How to use the book / design framing                 | [README.md](../README.md), `examples/*.md`                                           | Framing       |
| 2       | Complexity and its symptoms                          | [complexity-is-incremental.md](complexity-is-incremental.md)                         | Explicit      |
| 3       | Tactical vs strategic programming                    | [tactical-vs-strategic.md](tactical-vs-strategic.md)                                 | Explicit      |
| 4       | Deep modules                                         | [deep-modules.md](deep-modules.md)                                                   | Explicit      |
| 5       | Information hiding and leakage                       | [information-hiding.md](information-hiding.md)                                       | Explicit      |
| 6       | General-purpose interfaces                           | [general-purpose-modules.md](general-purpose-modules.md)                             | Explicit      |
| 7       | Different layer, different abstraction               | [different-layer-different-abstraction.md](different-layer-different-abstraction.md) | Explicit      |
| 8       | Pull complexity downward                             | [pull-complexity-downward.md](pull-complexity-downward.md)                           | Explicit      |
| 9       | Split vs join, general vs special, conjoined methods | [better-together-or-better-apart.md](better-together-or-better-apart.md)             | Explicit      |
| 10      | Define errors out of existence                       | [define-errors-out-of-existence.md](define-errors-out-of-existence.md)               | Explicit      |
| 11      | Design it twice                                      | [design-it-twice.md](design-it-twice.md)                                             | Explicit      |
| 12      | Why comments matter                                  | [why-write-comments.md](why-write-comments.md)                                       | Explicit      |
| 13      | Comments that describe the non-obvious               | [comments-describe-non-obvious.md](comments-describe-non-obvious.md)                 | Explicit      |
| 14      | Naming                                               | [choose-names-carefully.md](choose-names-carefully.md)                               | Explicit      |
| 15      | Write comments first                                 | [write-comments-first.md](write-comments-first.md)                                   | Explicit      |
| 16      | Modifying existing code                              | [modifying-existing-code.md](modifying-existing-code.md)                             | Explicit      |
| 17      | Consistency                                          | [consistency.md](consistency.md)                                                     | Explicit      |
| 18      | Obvious code                                         | [code-should-be-obvious.md](code-should-be-obvious.md)                               | Explicit      |
| 19      | Evaluating trends and patterns                       | [software-trends.md](software-trends.md)                                             | Explicit      |
| 20      | Designing for performance                            | [designing-for-performance.md](designing-for-performance.md)                         | Explicit      |
| 21      | Decide what matters                                  | [decide-what-matters.md](decide-what-matters.md)                                     | Explicit      |


## Notes

- Chapter 21 is the meta-principle for the whole corpus. It explains when to emphasize or hide distinctions and why the other rules are heuristics rather than fixed truths.
- Chapter 10's rewritten treatment of errors is the clearest example of the repo's new stance: simplify the knowledge burden, but keep important distinctions visible.
- Chapter 9 is used to counter shallow "small pieces everywhere" thinking by centering split-vs-join decisions on information hiding and overall complexity.
- Chapter 12 is kept separate from Chapter 13 so the repo now covers both why comments matter and how to write useful ones.

