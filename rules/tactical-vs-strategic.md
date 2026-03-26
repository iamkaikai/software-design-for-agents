---
name: Working Code Isn't Enough (Tactical vs Strategic)
chapter: 3
tags: [mindset, complexity, design]
---

## Principle

Do not optimize only for getting today's code to work. Invest enough in structure that tomorrow's changes are cheaper and safer.

## Why It Matters

Tactical coding ships local behavior quickly but often leaves behind fragile seams, duplicated logic, and awkward interfaces. Strategic design spends more thought up front so the system does not degrade with each change.

## What It Simplifies

- It reduces repeated rework caused by shortcuts that have to be revisited later.
- It shifts effort from patching around yesterday's decisions to designing cleaner abstractions today.
- It turns implementation into cumulative improvement instead of cumulative damage.

## Trade-offs and Boundaries

- Strategic work is not a license for overdesign. You are buying future simplicity, not architecture theater.
- You still need to ship. The question is how much design work is justified by the likely lifetime and reuse of the code.
- The cost moves from immediate typing speed to deliberate design time; that trade is only good when it lowers future change cost.
- Ask for clarification when a request pressures you toward a shortcut that changes long-lived interfaces, duplicates logic, or entrenches a known bad abstraction.

## When Context Changes the Answer

- Short-lived experiments, throwaway migrations, and isolated prototypes justify less design investment than shared infrastructure.
- Mature code paths with frequent changes justify more strategic work than rarely touched leaf code.

## Red Flags

- "Quick fix" becomes a recurring label for permanent code.
- Follow-up bugs appear because the first patch forced the change into the wrong place.
- Developers avoid touching a module because earlier shortcuts made it brittle.
- Similar logic is copied to avoid refactoring an existing abstraction.

## Examples

**Helpful:** Refactoring a shared parsing module before adding a new format instead of adding one more special branch.

**Backfires:** Building an elaborate extension framework for a path that may never be reused.
