---
name: Code Should Be Obvious
chapter: 18
tags: [readability, complexity]
---

## Principle

Code should be arranged so a reasonable reader can form the right mental model quickly and with little guesswork.

## Why It Matters

Non-obvious code consumes time on every read and increases the chance that future modifications are made under false assumptions. Obviousness is a direct defense against obscurity.

## What It Simplifies

- It reduces the amount of hidden context a reader must gather before acting.
- It replaces cleverness with clearer structure, naming, and control flow.
- It makes reviews, debugging, and maintenance faster because the first interpretation is more often correct.

## Trade-offs and Boundaries

- Obvious to one expert is not always obvious to the next maintainer. The test is the reader's experience, not the author's confidence.
- Some domains are inherently subtle; the goal is to make the subtlety legible, not to pretend it does not exist.
- Simplifying for readability may require more lines, more intermediate names, or a slightly less "elegant" implementation.
- Ask for clarification when code remains hard to follow because the underlying contract, event ordering, or lifecycle model is still ambiguous.

## When Context Changes the Answer

- Performance-critical or low-level code may legitimately use denser techniques, but then naming, structure, and comments have to compensate.
- Convention-heavy environments can rely more on established patterns because readers already carry that knowledge.

## Red Flags

- Readers must inspect several helper functions just to understand a simple path.
- The code relies on surprising side effects, hidden ordering, or subtle language features.
- Generic containers or vague variable names obscure meaning.
- Review comments repeatedly ask "what does this actually do?"

## Examples

**Helpful:** Splitting a complex condition into well-named intermediate booleans.

**Backfires:** Flattening nuanced domain logic so aggressively that the code becomes superficially simple but semantically misleading.
