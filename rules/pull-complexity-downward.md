---
name: Pull Complexity Downward
chapter: 8
tags: [complexity, interfaces, modules]
---

## Principle

It is more important for a module to have a simple interface than a simple implementation. When there's a choice between pushing complexity to the caller or handling it internally, handle it internally. Pull complexity downward into the implementation.

## Why It Matters

A module is used in many places but implemented once. Complexity in the implementation is paid once; complexity in the interface is paid by every caller. Simpler interfaces reduce the overall system complexity even if the module itself becomes harder to implement.

## How to Apply

- If you can handle a concern (defaults, error recovery, configuration) inside the module, don't force the caller to handle it.
- Provide sensible defaults instead of requiring configuration.
- Handle edge cases and errors internally where possible, rather than surfacing them to callers.
- Ask: "Would a caller ever want to do this differently?" If not, just do it inside the module.

## Red Flags

- Callers that must always pass the same boilerplate configuration.
- Every caller wrapping a function call with the same error-handling logic.
- "Convenience wrapper" functions that exist because the real interface is too hard to use directly.
- APIs that require multiple steps for the common case.

## Examples

**Bad:** A `connect(host, port, timeout, retries, backoffStrategy, tlsConfig)` function where every caller passes nearly identical arguments.

**Good:** A `connect(host)` function that uses sensible defaults and a separate `connectWithOptions(host, options)` for the rare caller that needs customization.
