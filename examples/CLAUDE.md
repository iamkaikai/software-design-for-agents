# Software Design Rules

You must follow the software design principles below when writing, reviewing, refactoring, or debugging code in this project. These rules are derived from *A Philosophy of Software Design* by John Ousterhout.

## Core Principles

### 1. Complexity Is Incremental
Complexity accumulates in small increments. Treat every addition of a special case, parameter, or conditional as a significant cost. Resist "just this once" thinking.

### 2. Working Code Isn't Enough
Be a strategic programmer, not a tactical one. Invest 10–20% extra time in clean design rather than taking the fastest path. Every change should leave the design at least as clean as before.

### 3. Deep Modules
Design modules with simple interfaces and rich implementations. A good module hides significant complexity. Avoid shallow modules where the interface is as complex as the implementation.

### 4. Information Hiding
Each module should encapsulate design decisions and hide them behind a simple interface. If two modules both depend on the same knowledge (file format, protocol, algorithm), one of them should own it entirely.

### 5. General-Purpose Modules
Design interfaces for the general class of problem, not just today's specific use case. A general-purpose interface is simpler and more resilient to change.

### 6. Different Layer, Different Abstraction
Each layer should provide a different abstraction from the layers above and below. If adjacent layers have similar interfaces, the decomposition is wrong. Eliminate pass-through methods.

### 7. Pull Complexity Downward
When choosing between pushing complexity to the caller or handling it internally, handle it internally. Provide sensible defaults. A module is implemented once but called many times.

### 8. Define Errors Out of Existence
Design APIs so errors can't happen. Make operations idempotent. Clip out-of-range values instead of throwing. Reserve exceptions for truly exceptional conditions.

### 9. Design It Twice
Consider at least two designs before committing. Compare them on simplicity, flexibility, and information hiding. The first idea is rarely the best.

### 10. Comments Describe the Non-Obvious
Write comments that explain *why*, not *what*. Document non-obvious side effects, constraints, and assumptions. Never restate the code in English.

### 11. Choose Names Carefully
Names are abstraction. Be precise: `getActiveUserCount` not `getCount`. Avoid generic names (`data`, `result`, `manager`) for anything with wide scope. Inconsistent naming causes bugs.

### 12. Write Comments First
Write interface comments before implementation. If you can't describe what a function does in one or two sentences, the design needs work.

### 13. Modifying Existing Code
When modifying code, make the change fit the existing design cleanly. If it doesn't fit, improve the design as part of the change. Leave code cleaner than you found it.

### 14. Consistency
Follow existing patterns and conventions. Use the same name for the same concept everywhere. If a convention is wrong, change it everywhere — don't create a competing convention.

### 15. Code Should Be Obvious
A reader should understand code quickly without much thought. Avoid clever tricks, unusual features, and subtle side effects. If code needs a comment to be understood, consider rewriting it.

### 16. Software Trends vs Good Design
Design patterns, agile, TDD, and OOP are tools, not goals. Apply them only when they reduce complexity. Don't create abstractions just because a pattern suggests you should.

## How to Apply

- **Writing new code:** Focus on rules 2, 3, 4, 5, 7, 9, 12.
- **Reviewing code:** Focus on rules 1, 3, 4, 6, 11, 14, 15.
- **Refactoring:** Focus on rules 1, 3, 4, 6, 13, 14.
- **Debugging:** Focus on rules 8, 13, 14, 15.

## Red Flags (Stop and Reconsider)

- Shallow modules: interface as complex as implementation.
- Pass-through methods that just delegate with no logic.
- Information leakage: same knowledge in multiple modules.
- Vague names: `data`, `result`, `manager`, `handler`, `process`.
- Comments that restate the code.
- Special-case logic proliferating across the codebase.
- Error handling that is more complex than the normal path.
- Patterns applied without a clear reason.
