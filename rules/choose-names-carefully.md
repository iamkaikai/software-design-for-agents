---
name: Choose Names Carefully
chapter: 14
tags: [naming, readability]
---

## Principle

Names are part of the design. They should communicate the most important distinctions a reader needs in order to reason correctly about the code.

## Why It Matters

Readers build mental models through names before they inspect implementations. A vague or misleading name creates false understanding, which is often worse than no understanding.

## What It Simplifies

- It reduces the need to inspect implementation to learn purpose.
- It makes interfaces more obvious and lowers cognitive load in reviews.
- It shifts understanding from code archaeology to direct recognition.

## Trade-offs and Boundaries

- Precision matters more than brevity, but names should still fit their scope and frequency of use.
- Long names do not automatically help if they mix multiple concepts or encode too much incidental detail.
- Naming cannot rescue a confused abstraction; sometimes the hard part is not the word choice but the design boundary itself.
- Ask for clarification when two plausible names imply different semantics, lifecycles, or ownership models and the underlying concept is not yet settled.

## When Context Changes the Answer

- Local short names are fine when the scope is tiny and the role is obvious.
- Module, API, and domain names need much stronger precision because they shape many readers' mental models.

## Red Flags

- Generic names like `data`, `manager`, `helper`, or `process` in wide scope.
- The same concept has different names in different modules.
- A name implies retrieval but the function mutates state.
- Developers repeatedly ask "what does this actually mean here?"

## Examples

**Helpful:** `activeSubscriptionCount` instead of `count`.

**Backfires:** `customerWithValidatedBillingAddressEligibleForRenewal` when the code still has no clear abstraction for that state.
