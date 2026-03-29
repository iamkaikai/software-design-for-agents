# Software Design for Agents

Software design heuristics for AI coding agents, derived from *A Philosophy of Software Design* by John Ousterhout and extended with supplemental architecture rules for broader system design trade-offs.

Works with Claude, OpenAI Codex, Gemini, Cursor, Aider, and other coding agents.

## Context First

This project does **not** treat design rules as one-size-fits-all commandments.

- These rules are decision aids, not slogans to apply mechanically.
- Good design always moves complexity somewhere: into interfaces, semantics, implementation, operations, or future change.
- The goal is not to eliminate understanding. The goal is to replace more dangerous, scattered, and branch-heavy understanding with simpler, more local, and more predictable understanding.
- When a rule would hide an important distinction or make semantics surprising, context wins over the slogan.

Chapter 1 of the book is represented here as project framing rather than as a standalone rule file.

## Why

AI coding agents can produce working code quickly, but working code is not enough. This repo gives agents a shared design vocabulary so they optimize for lower complexity, clearer abstractions, and more honest trade-offs.

## Quick Start

Copy the `rules/` and `profiles/` directories into your project, then reference them from your agent config:

```bash
cp -r rules/ /path/to/your-project/rules/
cp -r profiles/ /path/to/your-project/profiles/
```

```markdown
Follow the software design rules in `rules/`.
Before planning, read `profiles/plan.md`.
Before writing code, read `profiles/implement.md`.
Before reviewing code, read `profiles/review.md`.
```

## What's Inside

```text
rules/              # 20 book-derived rules + 8 supplemental architecture rules
  _index.md         # Master list of rules
  _coverage.md      # Chapter 1-21 coverage map
  ...

profiles/           # Task-specific rule subsets (plan, implement, review, refactor, debug)
source/             # Book source text used for coverage and refinement
```

## The 20 Rules

1. Complexity Is Incremental
2. Working Code Isn't Enough (Tactical vs Strategic)
3. Deep Modules
4. Information Hiding and Leakage
5. General-Purpose Modules
6. Different Layer, Different Abstraction
7. Pull Complexity Downward
8. Better Together Or Better Apart
9. Define Errors Out of Existence
10. Design It Twice
11. Why Write Comments
12. Comments Should Describe Things Not Obvious from Code
13. Choose Names Carefully
14. Write Comments First
15. Modifying Existing Code
16. Consistency
17. Code Should Be Obvious
18. Software Trends vs Good Design
19. Designing for Performance
20. Decide What Matters

## Supplemental Architecture Heuristics

These are not additional book chapters. They are complementary architecture mistake patterns. Each one is written to reduce overfitting:

- the tempting instinct
- why it looks reasonable
- what goes wrong
- the better decision pattern

Current supplemental mistake patterns:

1. Mistaking Distribution for Clean Separation
2. Mistaking the Org Chart for the Architecture
3. Mistaking "Better Architecture" for a Shared Priority
4. Letting Architectural Context Evaporate
5. Mistaking the Written Contract for the Real Interface
6. Mistaking Abstraction for Removal of Reality
7. Mistaking Shared Data for Harmless Convenience
8. Treating Operability as Cleanup Work

## How To Read The Rules

Each rule file is intentionally structured around trade-offs:

- `Principle`: the core idea
- `Why It Matters`: why the idea reduces complexity
- `What It Simplifies`: what kind of understanding or burden it reduces
- `Trade-offs and Boundaries`: what it costs, moves, or can hide
- `When Context Changes the Answer`: when the principle should be applied differently
- `Red Flags`: signs of misuse or design trouble
- `Examples`: a helpful use and a backfire case

If a rule and the context disagree, the agent should reason from the trade-offs, not blindly follow the rule heading.

Not every ambiguity should trigger a pause. Use the rules to surface boundary conditions and ask questions only when the unresolved ambiguity would materially change the design, semantics, or architectural trade-off.

For architecture-level work across services, deployment boundaries, data ownership, or operational design, also consult the supplemental architecture mistake patterns listed in [rules/_index.md](/Users/kyle/Desktop/software-design-for-agents/rules/_index.md).

## Contributing

When adding or revising rules:

1. Keep Chapter 1 framing in repo-level docs, not as a standalone rule file.
2. Each rule file should preserve the shared section structure.
3. Update `rules/_index.md` and `rules/_coverage.md`.
4. Update relevant `profiles/`.

## License

MIT
