# Software Design for Agents

Software design principles from [*A Philosophy of Software Design*](https://web.stanford.edu/~ouster/cgi-bin/book.php) by John Ousterhout, structured for AI coding agents to follow.

Works with **any AI coding agent** — Claude, OpenAI Codex, Gemini, Cursor, Aider, and more.

## Why

AI coding agents write code fast but don't inherently follow good design principles. This repo gives them a set of rules to follow, so the code they produce is well-designed — not just functional.

## Quick Start

### Option A: New project (use as boilerplate)

```bash
# Clone into your new project
git clone https://github.com/YOUR_USERNAME/software-design-for-agents.git my-project
cd my-project

# Copy the right example file to your project root
cp examples/CLAUDE.md ./CLAUDE.md    # For Claude Code
cp examples/AGENTS.md ./AGENTS.md    # For OpenAI Codex / cross-platform
cp examples/GEMINI.md ./GEMINI.md    # For Gemini CLI

# Remove the scaffolding you don't need
rm -rf examples/ profiles/ rules/ CLAUDE.md
# (keep only the agent file you copied to the root)
```

### Option B: Add to an existing project

```bash
# From your existing project directory
curl -O https://raw.githubusercontent.com/YOUR_USERNAME/software-design-for-agents/main/examples/AGENTS.md
# Or CLAUDE.md / GEMINI.md depending on your agent
```

Or just copy the contents of the file you need from the `examples/` directory.

### Option C: Use the full rule set (advanced)

If you want the detailed rules and profiles available to your agent (not just the summary), copy the full `rules/` and `profiles/` directories into your project:

```bash
cp -r rules/ /path/to/your-project/rules/
cp -r profiles/ /path/to/your-project/profiles/
```

Then reference them from your agent's config file. For example, in a `CLAUDE.md`:

```markdown
Follow the software design rules in the `rules/` directory.
Before writing code, read `profiles/implement.md`.
Before reviewing code, read `profiles/review.md`.
```

## What's Inside

```
rules/              # One file per design principle (16 rules)
  _index.md         # Master list with summaries and tags
  deep-modules.md
  information-hiding.md
  ...

profiles/           # Task-specific rule sets
  review.md         # Rules to apply when reviewing code
  implement.md      # Rules to apply when writing new code
  refactor.md       # Rules to apply when refactoring
  debug.md          # Rules to apply when debugging

examples/           # Drop-in files for each agent platform
  AGENTS.md         # OpenAI Codex / cross-platform standard
  CLAUDE.md         # Anthropic Claude Code
  GEMINI.md         # Google Gemini CLI
```

## Platform Guide

| Platform | File to use | Where to put it |
|----------|------------|-----------------|
| **Claude Code** | `examples/CLAUDE.md` | Project root as `CLAUDE.md` |
| **OpenAI Codex** | `examples/AGENTS.md` | Project root as `AGENTS.md` |
| **Gemini CLI** | `examples/GEMINI.md` | Project root as `GEMINI.md` |
| **Cursor** | `examples/AGENTS.md` | Project root as `AGENTS.md` (Cursor reads this) |
| **Aider** | `examples/AGENTS.md` | Project root as `AGENTS.md` |
| **Other agents** | `examples/AGENTS.md` | `AGENTS.md` is the emerging cross-platform standard |

All three example files contain **identical content** — the only difference is the filename. Use whichever your agent expects, or use multiple if you work with several agents.

## The 16 Rules (Summary)

1. **Complexity Is Incremental** — Fight every small increase in complexity.
2. **Working Code Isn't Enough** — Be strategic, not tactical. Invest in design.
3. **Deep Modules** — Simple interfaces, rich implementations.
4. **Information Hiding** — Encapsulate knowledge behind module boundaries.
5. **General-Purpose Modules** — Design for the general problem, not today's caller.
6. **Different Layer, Different Abstraction** — No pass-through methods.
7. **Pull Complexity Downward** — Handle it inside the module, not at the call site.
8. **Define Errors Out of Existence** — Design away error conditions.
9. **Design It Twice** — Compare alternatives before committing.
10. **Comments Describe the Non-Obvious** — Explain why, not what.
11. **Choose Names Carefully** — Precise names reduce cognitive load.
12. **Write Comments First** — Use comments as a design tool.
13. **Modifying Existing Code** — Leave the design cleaner than you found it.
14. **Consistency** — Same patterns everywhere. No competing conventions.
15. **Code Should Be Obvious** — If it needs study, rewrite it.
16. **Software Trends vs Good Design** — Patterns are tools, not goals.

## Contributing

To add or modify rules:

1. Each rule lives in its own file in `rules/` with YAML frontmatter (`name`, `chapter`, `tags`).
2. Update `rules/_index.md` when adding/removing rules.
3. Update relevant profiles in `profiles/` to reference new rules.
4. Update **all three** example files in `examples/` — they must stay in sync.

## License

MIT
