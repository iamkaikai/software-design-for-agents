# Software Design for Agents — Repo Guidelines

This repo contains software design rules from *A Philosophy of Software Design*, structured for AI coding agents.

## Structure

- `rules/` — One file per design principle. Each has frontmatter (name, chapter, tags) and sections (Principle, Why It Matters, How to Apply, Red Flags, Examples).
- `profiles/` — Task-specific rule sets (plan, implement, review, refactor, debug). Each profile references rules in priority order.

## Conventions

- Rule files use YAML frontmatter with `name`, `chapter`, and `tags` fields.
- Profile files reference rules using relative links to the rules directory.
- Keep `rules/_index.md` in sync when adding/removing/renaming rules.
