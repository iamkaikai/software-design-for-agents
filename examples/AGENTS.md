# Software Design Rules

Use these rules as design heuristics, not one-size-fits-all commandments.

## Context First

- There is no single correct design rule for every situation.
- Every design decision has consequences. It moves complexity into interfaces, implementation, semantics, operations, or future change.
- The goal is not to eliminate understanding. The goal is to replace more dangerous, scattered, and branch-heavy understanding with simpler, more local, and more predictable understanding.
- If a rule would hide an important distinction or force a surprising contract, stop and clarify before locking it in.

Chapter 1 of *A Philosophy of Software Design* is represented here as framing for the whole project rather than as a standalone rule file.

## Core Principles

### 1. Complexity Is Incremental
Treat each small increase in complexity as a real cost, because systems usually become hard in tiny steps.

### 2. Working Code Isn't Enough
Favor strategic design over fast local fixes when the code will matter again.

### 3. Deep Modules
Prefer modules with small interfaces relative to the complexity they hide.

### 4. Information Hiding
Let modules own design knowledge so that one decision does not leak across the system.

### 5. General-Purpose Modules
Design for the broader problem class, not only the first caller's workflow.

### 6. Different Layer, Different Abstraction
Each layer should change the abstraction, not merely relay the same idea.

### 7. Pull Complexity Downward
Carry repeatable complexity inside the module when the resulting semantics stay honest.

### 8. Better Together Or Better Apart
Split or join code based on overall complexity, not on blanket rules about size.

### 9. Define Errors Out of Existence
Make errors structurally impossible (types, constraints, schemas) or redefine operations so common errors become normal semantics. Prefer structural prevention over semantic redefinition over procedural guard clauses.

### 10. Design It Twice
Compare alternatives before fixing an interface or decomposition.

### 11. Why Write Comments
Comments matter because code cannot express all the design knowledge future readers need.

### 12. Comments Describe the Non-Obvious
Use comments for rationale, assumptions, invariants, and surprising consequences, not for narrating the obvious.

### 13. Choose Names Carefully
Names should communicate the distinctions readers must get right.

### 14. Write Comments First
Early interface comments are a design tool for testing whether the abstraction is clear.

### 15. Modifying Existing Code
When changing code, make the new behavior fit the design cleanly or improve the design until it does.

### 16. Consistency
Reuse patterns and names so readers can carry knowledge from one part of the system to another.

### 17. Code Should Be Obvious
Arrange code so a reasonable reader can understand it quickly and form the right mental model.

### 18. Software Trends vs Good Design
Patterns and paradigms are tools to evaluate, not defaults to obey.

### 19. Designing for Performance
Keep designs naturally efficient when possible, and use measurement to justify complexity when not.

### 20. Decide What Matters
Center the design on the distinctions, guarantees, and constraints that matter most.

## How to Apply

- Writing new code: focus first on rules 2, 3, 4, 5, 7, 8, 10, 14, 20.
- Reviewing code: focus first on rules 1, 3, 4, 8, 13, 16, 17, 20.
- Refactoring: focus first on rules 1, 3, 4, 6, 8, 15, 16, 20.
- Debugging: focus first on rules 1, 4, 9, 15, 16, 17, 20.

## Supplemental Architecture Rules

For service boundaries, deployment topology, distributed data, compatibility, and operational design, also read the supplemental architecture mistake patterns in `rules/`:

- `Mistaking Distribution for Clean Separation`
- `Mistaking the Org Chart for the Architecture`
- `Mistaking "Better Architecture" for a Shared Priority`
- `Letting Architectural Context Evaporate`
- `Mistaking the Written Contract for the Real Interface`
- `Mistaking Abstraction for Removal of Reality`
- `Mistaking Shared Data for Harmless Convenience`
- `Treating Operability as Cleanup Work`

## How To Use The Rules

- Read the trade-off sections, not just the headings.
- Ask what complexity the rule removes, what complexity it moves elsewhere, and what understanding still remains necessary.
- If an unresolved ambiguity would materially change the design or semantics, clarify it before implementing the choice.
- Prefer clear contracts over hidden cleverness.

## Red Flags

- Shallow modules whose interfaces are almost as complicated as their implementations.
- New flags, modes, or branches added to stable APIs without a clear abstraction shift.
- Important distinctions hidden behind "simple" interfaces.
- Pass-through layers that only rename or relay calls.
- Comments that restate the code while leaving the real rationale undocumented.
- Naming that hides ownership, semantics, or lifecycle.
- Performance complexity added without measurement.
